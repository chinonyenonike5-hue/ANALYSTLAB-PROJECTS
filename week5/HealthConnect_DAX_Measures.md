# HealthConnect Dashboard - Date Table & DAX Measures

## 1. Date Table

Create a new table (Modeling > New Table) rather than a calculated column, so it's a standalone table you can relate to `appointment_date`.

```DAX
DateTable =
ADDCOLUMNS (
    CALENDAR ( DATE ( 2025, 1, 1 ), DATE ( 2026, 12, 31 ) ),
    "Year", YEAR ( [Date] ),
    "Month Number", MONTH ( [Date] ),
    "Month Name", FORMAT ( [Date], "MMMM" ),
    "Month Short", FORMAT ( [Date], "MMM" ),
    "Year-Month", FORMAT ( [Date], "MMM YYYY" ),
    "Quarter", "Q" & FORMAT ( [Date], "Q" ),
    "Weekday Name", FORMAT ( [Date], "dddd" ),
    "Weekday Number", WEEKDAY ( [Date], 2 ),
    "Is Weekend", IF ( WEEKDAY ( [Date], 2 ) > 5, TRUE, FALSE )
)
```

Notes:
- Adjust the `CALENDAR()` start/end dates to match your actual min/max `appointment_date` (check first - your `booking_date` range may start earlier than `appointment_date`).
- In **Model view**: mark this table as a Date table (right-click > Mark as date table, using the `Date` column), then relate `DateTable[Date]` → `HealthConnect_Appointment_Data[appointment_date]` (one-to-many, single direction).
- Sort `Month Name` and `Weekday Name` by their respective Number columns (Column tool > Sort by Column) so they display in calendar order, not alphabetically.

---

## 2. Core Measures

```DAX
Total Appointments = COUNTROWS ( HealthConnect_Appointment_Data )

Total No-Shows =
CALCULATE ( [Total Appointments], HealthConnect_Appointment_Data[appointment_outcome] = "No-Show" )

Total Attended =
CALCULATE ( [Total Appointments], HealthConnect_Appointment_Data[appointment_outcome] = "Attended" )

Total Cancelled =
CALCULATE ( [Total Appointments], HealthConnect_Appointment_Data[appointment_outcome] = "Cancelled" )
```

## 3. No-Show Rate (excluding cancellations from the denominator)

Since `appointment_outcome` has three categories, decide how `Cancelled` factors in. The standard approach - and the one I'd recommend - is to exclude cancellations, since a cancelled slot was never a "show/no-show" outcome:

```DAX
Completed Appointments = [Total Attended] + [Total No-Shows]

No-Show Rate =
DIVIDE ( [Total No-Shows], [Completed Appointments] )

Cancellation Rate =
DIVIDE ( [Total Cancelled], [Total Appointments] )
```

If you'd rather report a no-show rate against *all* booked appointments (including cancellations in the base), swap the denominator:

```DAX
No-Show Rate (All Bookings) =
DIVIDE ( [Total No-Shows], [Total Appointments] )
```

Keep both if you want to show them side by side - just label clearly which base each uses.

## 4. Operational Measures

```DAX
Avg Waiting Time (min) =
AVERAGE ( HealthConnect_Appointment_Data[waiting_time_minutes] )

Avg Booking Lead Days =
AVERAGE ( HealthConnect_Appointment_Data[booking_lead_days] )

Avg Distance to Clinic (km) =
AVERAGE ( HealthConnect_Appointment_Data[distance_to_clinic_km] )

Avg Previous No-Shows =
AVERAGE ( HealthConnect_Appointment_Data[previous_no_shows] )
```

## 5. Reminder Effectiveness

```DAX
No-Shows (Reminder Sent) =
CALCULATE ( [Total No-Shows], HealthConnect_Appointment_Data[reminder_sent] = "Yes" )

Completed (Reminder Sent) =
CALCULATE ( [Completed Appointments], HealthConnect_Appointment_Data[reminder_sent] = "Yes" )

No-Show Rate (Reminder Sent) =
DIVIDE ( [No-Shows (Reminder Sent)], [Completed (Reminder Sent)] )

No-Shows (No Reminder) =
CALCULATE ( [Total No-Shows], HealthConnect_Appointment_Data[reminder_sent] = "No" )

Completed (No Reminder) =
CALCULATE ( [Completed Appointments], HealthConnect_Appointment_Data[reminder_sent] = "No" )

No-Show Rate (No Reminder) =
DIVIDE ( [No-Shows (No Reminder)], [Completed (No Reminder)] )

Reminder Impact (pp) =
[No-Show Rate (No Reminder)] - [No-Show Rate (Reminder Sent)]
```

`Reminder Impact (pp)` gives you the percentage-point drop in no-show rate attributable to sending a reminder - a good headline stat.

## 6. Repeat No-Show Risk

```DAX
Has Prior No-Show =
CALCULATE (
    [Total Appointments],
    HealthConnect_Appointment_Data[previous_no_shows] > 0
)

No-Show Rate (Repeat Offenders) =
CALCULATE ( [No-Show Rate], HealthConnect_Appointment_Data[previous_no_shows] > 0 )

No-Show Rate (First-Timers) =
CALCULATE ( [No-Show Rate], HealthConnect_Appointment_Data[previous_no_shows] = 0 )
```

## 7. Distance Buckets (for a binned chart)

Add this as a **calculated column** on the `HealthConnect_Appointment_Data` table (not a measure, since it needs to sit on each row for slicing/axis use):

```DAX
Distance Band =
SWITCH (
    TRUE (),
    HealthConnect_Appointment_Data[distance_to_clinic_km] <= 5, "0-5 km",
    HealthConnect_Appointment_Data[distance_to_clinic_km] <= 10, "5-10 km",
    HealthConnect_Appointment_Data[distance_to_clinic_km] <= 20, "10-20 km",
    HealthConnect_Appointment_Data[distance_to_clinic_km] <= 30, "20-30 km",
    ISBLANK ( HealthConnect_Appointment_Data[distance_to_clinic_km] ), "Unknown",
    "30+ km"
)
```

## 8. Formatting reminders

- Format `No-Show Rate` and other rate measures as Percentage, 1 decimal place, in the measure's Formatting pane.
- `Total Appointments`, `Total No-Shows` etc. as Whole Number.
- `Avg Waiting Time (min)` and `Avg Distance` as 1 decimal place.
