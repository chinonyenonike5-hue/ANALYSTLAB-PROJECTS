# HealthConnect Clinic – Week 8 Final Project

## Overview
This repository contains the final deliverables for the **HealthConnect Clinic Data Analytics Track** (AnalystLab Africa Experience Lab, Week 8).  
The project investigates **missed appointments (no-shows)** at HealthConnect Clinic and develops **data-driven insights** to reduce them.  

Across 5,000 anonymized appointment records (Jan 2025 – Jun 2026), the analysis identifies the strongest predictors of no-shows, validates findings through independent testing, and prepares actionable recommendations for clinic operations and cross-track integration with Data Science.

---

## Contents
- **HealthConnect_Week8_Final_Presentation.pptx**  
  Final presentation slides summarizing the problem, data, key findings, dashboard visuals, and recommendations.

- **HealthConnect_Week8_HCPOD_Final_Integration.docx**  
  Evidence of final integration with the Data Science track. Documents the validated feature handoff (distance, prior no-show history, reminder status by appointment type, compounded-risk feature).

- **HealthConnect_Week8_Final_Analytics_Package.docx**  
  Comprehensive analytics package including KPIs, validated findings, Power BI dashboard description, business insights, recommendations, and limitations.

  - **HealthConnect_video_presentation.mp4**
 
 - **Healthconnect_dashboard_final**  

---

## Key Findings
- **No-Show Rate:** 51.2% of completed appointments end in a no-show (vs. 5.3% cancelled in advance).  
- **Distance Effect:** Patients living 30km+ away no-show at **70.0%**, compared to **48.7%** within 5km.  
- **Prior History Effect:** Patients with a prior no-show miss again at **57.8%**, vs. **46.3%** for first-time patients.  
- **Compounded Risk:** Patients 30km+ away *and* with prior no-shows have the highest risk (**77.4%**, n=31).  
- **Reminder Effect:** Reminders reduce no-shows by **4.8pp on average**, but effectiveness varies:
  - Diagnostic Test: **11.8pp reduction**
  - General Consultation: **3.6pp reduction**

---

## KPIs
1. **Overall No-Show Rate:** 51.2%  
2. **Cancellation Rate:** 5.3%  
3. **Reminder Impact:** 4.8pp average reduction  
4. **Distance-Based No-Show Rates:** 48.7% → 70.0% across bands  
5. **Compounded Risk Segment:** 77.4% (30km+ & prior no-show, n=31)

---

## Recommendations
1. Prioritize reminders for Diagnostic Test appointments (largest effect size).  
2. Introduce distance-based interventions (telehealth or transport support) for patients ≥20km away.  
3. Flag compounded-risk patients (30km+ & prior no-show) for manual confirmation calls.  
4. Continue reminders for patients with prior no-shows (effect is slightly stronger for this group).

---

## Limitations
- Dataset is fictional and anonymized – findings require validation against real clinic data.  
- Relationships are **correlational, not causal**.  
- Small sample size for compounded-risk segment (n=31).  
- Missing values (distance, waiting time) were left blank, not imputed.

---

## Cross-Track Contribution
- Prepared and validated a **ranked feature handoff** for Data Science:
  - Distance to clinic  
  - Prior no-show history  
  - Reminder status × appointment type  
  - Compounded-risk engineered feature  
- Independently re-verified all figures in Week 7 testing.  
- Provides a reliable foundation for a **no-show prediction model**.

---

## Presentation Materials
- **Power BI Dashboard**: Patient Attendance & Risk Insights (validated in Week 7).  
- **Final Presentation Video**: Walkthrough of findings, insights, and recommendations.  
- **Supporting Reports**: Week 5–7 analytics and testing documents.

---

## Acknowledgment
This project was completed **solo** within the Data Analytics track.  
Outputs are self-prepared and independently verified, with clear documentation of integration points for Data Science.

---



## Author

Nonike Emmanuella - Data Analytics Track
#AnalystLabAfrica
