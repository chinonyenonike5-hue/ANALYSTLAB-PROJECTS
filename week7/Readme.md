# HealthConnect Clinic - Data Analytics

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
│   ├── HealthConnect_Week6_Advanced_Analytics_Report.docx
│   ├── HealthConnect_Week6_Project_Summary.docx
│   ├── HealthConnect_Week6_CrossTrack_Integration.docx
│   ├── HealthConnect_Week7_Testing_Refinement_Report.docx
│   ├── HealthConnect_Week7_Project_Summary.docx
│   └── HealthConnect_DAX_Measures.md
└── dashboard/
    ├── HealthConnect_Dashboard.pbix
    └── HealthConnect_Dashboard_Week7_Evidence.pdf
```

Note: the original dataset in `data/` is never modified. Any cleaned or transformed data used for analysis is generated within Power BI (Power Query) and documented separately rather than overwriting the source file.

## Key findings

- Overall no-show rate is 51.2% of completed appointments (Attended + No-Show), excluding cancellations.
- Distance to the clinic is the strongest predictor found: no-show rate rises from 48.7% for patients within 5km to 70.0% for patients living more than 30km away, and this holds independently of age group and appointment type (validated in Week 6).
- Patients with a prior no-show are considerably more likely to miss their next appointment (57.8% vs 46.3% for patients with no prior no-show history).
- Distance and prior no-show history compound: patients with both risk factors show a 77.4% no-show rate (n=31), the highest of any segment identified.
- Sending a reminder is associated with a 4.8 percentage-point average reduction in no-shows, but this varies sharply by appointment type: Diagnostic Test appointments show an 11.8-point reminder effect versus 3.6 points for General Consultation (validated in Week 6).
- Follow-up appointments have the highest no-show rate by appointment type (54.2%), notably higher than General Consultations (49.1%).
- Waiting time shows no meaningful relationship to no-show behavior.
- Cancellations account for only 5.3% of all appointments, confirming no-shows (not cancellations) are the primary issue to address.

Full definitions, calculations, and validation are documented in `reports/HealthConnect_Week6_Advanced_Analytics_Report.docx` (Week 5 baseline in `HealthConnect_Week5_Analytics_Report.docx`). All figures above were independently re-derived and confirmed accurate in Week 7 (`reports/HealthConnect_Week7_Testing_Refinement_Report.docx`, Part 3) - 11 tests, zero discrepancies found.

## Dashboard

An interactive Power BI dashboard was built and updated across Week 5 and Week 6, covering:

- Headline KPI cards: total appointments, no-show rate, average waiting time, reminder impact, cancellation rate, and compounded risk rate.
- A monthly no-show rate trend line (Jan 2025 - Jun 2026).
- No-show rate by distance and prior no-show history, shown as a matrix to reveal the compounding effect between the two.
- No-show rate by appointment type and reminder status, showing that reminder effectiveness varies by appointment type.
- Breakdown charts by appointment type, distance to clinic, and patient age group.
- Slicers for age group, appointment type, date, distance band, prior no-show status, and reminder status.

The two strongest risk factors (distance to clinic and prior no-show history) are visually highlighted throughout the dashboard using a consistent accent color, so the most actionable findings are visible at a glance.

The dashboard carried forward unchanged into Week 7: no rebuild was needed, since Week 7 testing confirmed every displayed value was already accurate. A dated evidence export (`dashboard/HealthConnect_Dashboard_Week7_Evidence.pdf`) documents this validated state.

## Testing and validation (Week 7)

Every KPI card and chart value was independently re-derived from the raw dataset using a separate calculation method from the original DAX measures, to confirm no drift had occurred since Week 6. All 11 tests passed with exact matches, including two previously-corrected Week 6 issues (the Compounded Risk Rate measure and the reminder-by-appointment-type chart) that were specifically retested to confirm their fixes held. Dashboard filters (single and compound) were also tested and confirmed to narrow the data correctly. Full test records are in `reports/HealthConnect_Week7_Testing_Refinement_Report.docx`, Part 3.

## Cross-track collaboration

In Week 5, a dependency with the Data Science track was identified. In Week 6, this was acted on directly: a ranked feature handoff document was prepared identifying distance to clinic, prior no-show history, and reminder status (interacted with appointment type) as validated candidate features for a no-show prediction model, along with a compounded-risk engineered feature. In Week 7, that handoff was independently retested rather than simply assumed correct - every effect size cited in it was checked against the Week 7 recalculation and confirmed unchanged. This placement is being completed solo, so both the Week 6 handoff and the Week 7 retest are documented as prepared/self-verified analytical outputs rather than a two-way exchange, in the interest of accurately representing actual progress. Full detail is in `reports/HealthConnect_Week6_CrossTrack_Integration.docx` and `reports/HealthConnect_Week7_Testing_Refinement_Report.docx`, Part 9.

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
| Week 6 | Validation of key findings, interaction effects, cross-track integration, dashboard update | Complete |
| Week 7 | Testing, refinement, end-to-end validation, cross-track retest | Complete |
| Week 8 | Planned: final integration, presentation | Upcoming |

## Limitations

- Dataset is fictional and anonymized; findings would need validation against real clinic data before operational use.
- Missing values in `distance_to_clinic_km` and `waiting_time_minutes` were left blank rather than imputed at this stage.
- Analysis is descriptive and correlational, not causal - the reminder effect and distance relationship are associations, not proven causal effects; Week 7 testing confirmed the calculations are correct but could not and did not establish causation.
- The compounded-risk finding (distance 30km+ combined with prior no-show) rests on a small sample (n=31) and should be treated as directionally indicative rather than precise; this was confirmed unchanged by Week 7 testing, which could not and did not expand the sample.

Full assumptions, limitations, risks, and dependencies are documented in `reports/HealthConnect_Week7_Testing_Refinement_Report.docx`, Part 10 (reviewed across Weeks 4-6).

## Author

Nonike Emmanuella - Data Analytics Track
#AnalystLabAfrica
