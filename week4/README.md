# HealthConnect Clinic Experience Lab — Week 4
**AnalystLab Africa Data Analytics Internship**
**Track:** Data Analytics
**Phase:** Problem Understanding

## Project Overview
HealthConnect Clinic is a fictional healthcare provider facing high rates of missed
appointments (no-shows), inefficient use of appointment slots, and repetitive patient
enquiries. This project explores how data and AI can help reduce missed appointments
and improve the patient support experience.

**Central Project Question:** How can HealthConnect Clinic use data and AI to reduce
missed appointments and improve the patient support experience?

From Week 4 onward, this repository tracks the Data Analytics track's contribution to
the shared HealthConnect project, building on the foundation set in Weeks 1–3
(Superstore Sales dataset).

## Week 4 Objective
Establish a clear understanding of the HealthConnect business problem from a Data
Analytics perspective: review the appointment dataset, assess its quality, define
relevant business questions, and identify — without yet calculating — KPIs that will
guide the analysis in later weeks.

## Data Sources
| File | Description |
|---|---|
| `HealthConnect_Appointment_Data.csv` | 5,000 fictional, anonymised appointment records (demographics, booking info, history, reminders, distance, outcome). |
| `HealthConnect_Data_Dictionary.xlsx` | Field definitions and data rules for the appointment dataset. |

> `HealthConnect_Clinic_Knowledge_Base.docx` is part of the shared project resources
> but is scoped to the Generative AI track and was not used in this track's analysis.

## Week 4 Deliverables
- **`HealthConnect_Week4_Initial_Analysis_Document.docx`** — dataset overview, data
  quality assessment, business questions, 5 proposed KPIs (identified and justified,
  not yet calculated per Week 4 scope), initial analysis approach, and assumptions /
  limitations / risks / dependencies.
- **`HealthConnect_Week4_Project_Summary.docx`** — concise summary of the problem,
  resources used, key observations, proposed approach, key considerations, and the
  proposed focus for Week 5.

## Key Findings (Week 4)
- Dataset is clean and internally consistent: no duplicates, and all consistency
  checks (lead-time arithmetic, no-show history rule, reminder/channel dependency,
  weekday and age-group derivation) passed with zero violations.
- Only 3 of 18 fields have missing values, all consistent with the Data Dictionary's
  documented limitations.
- Overall no-show rate in the raw data: **48.5%** (Attended 46.3%, Cancelled 5.3%).
- Five business questions were defined, each mapped to a proposed KPI:
  Overall No-Show Rate, Repeat No-Show Rate, No-Show Rate by Booking Lead Time,
  Reminder Effectiveness Rate, and No-Show Rate by Distance Band.

## Proposed Focus for Week 5
Finalise data-cleaning decisions (missing-value treatment, handling of Cancelled
appointments), calculate the five proposed KPIs, test whether observed segment
differences are meaningful, and begin building the Power BI dashboard.

## Tools Used
Python (pandas) for data exploration and quality checks; Microsoft Word for
documentation. Power BI is planned for Week 5 onward.

## Repository Structure
```
├── HealthConnect_Appointment_Data.csv
├── HealthConnect_Data_Dictionary.xlsx
├── HealthConnect_Week4_Initial_Analysis_Document.docx
├── HealthConnect_Week4_Project_Summary.docx
└── README.md
```

---
*Part of the AnalystLab Africa Experience Lab Internship Programme.*
