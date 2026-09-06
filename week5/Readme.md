 HealthConnect Clinic - Data Analytics

AnalystLab Africa Experience Lab Internship Programme
Data Analytics Track

## Project overview

HealthConnect Clinic is a fictional healthcare provider facing a high rate of missed patient appointments. This project analyzes appointment-level data to understand attendance patterns, quantify the scale of the no-show problem, and identify which factors are most strongly associated with patients missing their appointments.

Central project question: How can HealthConnect Clinic use data and AI to reduce missed appointments and improve the patient support experience?

## Repository structure

```
.
├── README.md
├── data/
│   └── HealthConnect_Appointment_Data.csv        (original dataset, unmodified)
├── docs/
│   ├── HealthConnect_Data_Dictionary.xlsx
│   └── HealthConnect_Clinic_Knowledge_Base.docx
├── reports/
│   ├── HealthConnect_Week5_Analytics_Report.docx
│   ├── HealthConnect_Week5_Project_Summary.docx
│   └── HealthConnect_DAX_Measures.md
└── dashboard/
    └── HealthConnect_Dashboard.pbix
```

Note: the original dataset in `data/` is never modified. Any cleaned or transformed data used for analysis is generated within Power BI (Power Query) and documented separately rather than overwriting the source file.

## Key findings

- Overall no-show rate is 51.2% of completed appointments (Attended + No-Show), excluding cancellations.
- Distance to the clinic is the strongest predictor found: no-show rate rises from 48.7% for patients within 5km to 70.0% for patients living more than 30km away.
- Patients with a prior no-show are considerably more likely to miss their next appointment (57.8% vs 46.3% for patients with no prior no-show history).
- Sending a reminder is associated with a 4.8 percentage-point reduction in no-shows (54.6% without a reminder vs 49.9% with one).
- Follow-up appointments have the highest no-show rate by appointment type (54.2%), notably higher than General Consultations (49.1%).
- Waiting time shows no meaningful relationship to no-show behavior.
- Cancellations account for only 5.3% of all appointments, confirming no-shows (not cancellations) are the primary issue to address.

Full definitions, calculations, and interpretation for each KPI are documented in `reports/HealthConnect_Week5_Analytics_Report.docx`.

## Dashboard

An interactive Power BI dashboard was built covering:

- Headline KPI cards: total appointments, no-show rate, average waiting time, reminder impact, and cancellation rate.
- A monthly no-show rate trend line (Jan 2025 - Jun 2026).
- Breakdown charts by appointment type, patient age group, distance to clinic, reminder channel, prior no-show history, and gender.
- Slicers for age group, appointment type, date, gender, and reminder status.

The two strongest risk factors (distance to clinic and prior no-show history) are visually highlighted on the dashboard to draw attention to the most actionable findings.

## Tools used

- Power BI (data modeling, DAX measures, dashboard)
- Power Query (data cleaning and transformation)
- Python / pandas (data quality validation and cross-checking calculations)

## Data quality summary

The dataset (5,000 appointment records) was checked for missing values, duplicates, and internal consistency before analysis:

- No duplicate appointment IDs or duplicate rows.
- Missing values found only in `reminder_channel` (expected, tied to `reminder_sent = No`), `distance_to_clinic_km`, and `waiting_time_minutes` - all explainable and not treated as errors.
- `booking_lead_days`, `appointment_day`, and `age_group` were all cross-checked against their source fields and matched in 100% of rows.

Full detail is in `reports/HealthConnect_Week5_Analytics_Report.docx`, Part 2.

## Project progress

| Week | Focus | Status |
|------|-------|--------|
| Week 4 | Problem understanding, resource review, initial approach | Complete |
| Week 5 | Data preparation, EDA, KPI development, dashboard, business insights | Complete |
| Week 6 | Planned: refine dashboard design, deepen interaction-effect analysis, formalize operational recommendations | Upcoming |

## Limitations

- Dataset is fictional and anonymized; findings would need validation against real clinic data before operational use.
- Missing values in `distance_to_clinic_km` and `waiting_time_minutes` were left blank rather than imputed at this stage.
- Analysis is descriptive and correlational, not causal - the reminder effect and distance relationship are associations, not proven causal effects.

Full assumptions, limitations, risks, and dependencies are documented in `reports/HealthConnect_Week5_Analytics_Report.docx`, Part 7.

## Cross-track collaboration

Findings on distance to clinic and prior no-show history were shared with the Data Science track as candidate predictive features for a future no-show prediction model.

## Author

Nonike Emmanuella - Data Analytics Track
#AnalystLabAfrica
