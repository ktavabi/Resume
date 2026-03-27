# BIOS Team — Comprehensive Product Owner Overview

**Purpose:** Professional CV content and targeted employment history for **Data Scientist** or **AI/Data Engineer** roles.  
**Source:** Azure DevOps work item data (`ado-tree-work.csv`) — work item type, title, value area, creation/close dates, descriptions.

---

## Product Ownership Scope

As product owner you hold 5 active Epics spanning **Jan 2023 – Dec 2028**, all under the BIOS (Business & Operations Surveillance) program of the Washington DOC Research & Data Analytics unit. Each epic has its own strategic purpose and feature portfolio. A cross-functional team of analysts (Connor Saxe, Matthew Landon, Amy Lodge, Porranee Thanapakpawin, Zaira Lujan) executes under your ownership.

---

## Epic 1 — Business & Operations Surveillance Reports

**ID 14 | Area: Business Operations | Created: Jan 2023 | Status: Active**

> Parent for all BIOS operational reporting activities, including recurring reports and BI dashboards aligned with agency mission and correctional surveillance.

### Features

| ID | Title | Value Area | Status | Created | Closed |
|----|-------|-----------|--------|---------|--------|
| 58 | Reception Center Processing Dashboard | Correctional Operations | Closed | Oct 2023 | Jun 2025 |
| 79 | Employment Security Division (ESD) Quarterly Report | Correctional Operations | Closed | Dec 2023 | Jan 2026 |
| 122 | WAONE Risk Level Classification Dashboard | Correctional Operations | Closed | Jan 2024 | Sep 2025 |
| 178 | Monthly Recurring Reports (container) | Business Operations | Closed | Mar 2024 | Jan 2026 |
| 179 | Quarterly Recurring Reports (container) | Enterprise Results | Closed | Mar 2024 | Aug 2025 |
| 260 | Annual Recurring Reports (container) | Enterprise Results | Active | Apr 2024 | — |
| 332 | Drug and Alcohol Testing (DAT) Dashboard | Correctional Operations | Active | Apr 2024 | — |
| 494 | Corrections Staffing Reporting | Business Operations | Active | May 2024 | — |
| 740 | Restrictive Housing & Mental Health Outcomes | Research | Closed | Jun 2024 | Dec 2024 |
| 1112 | High-Frequency Recurring Reports (container) | Enterprise Results | Closed | Aug 2024 | Jul 2025 |
| 1113 | Agency Performance Evaluation Dashboard | Enterprise Results | Active | Aug 2024 | — |
| 1719 | Agency Recidivism Rates Dashboard | Enterprise Results | Closed | Feb 2025 | Nov 2025 |
| 1823 | CeConnect Dashboard | Enterprise Results | Active | Mar 2025 | — |
| 1971 | CeConnect Dashboard — Phase 2 UI Enhancements | Business Operations | Active | May 2025 | — |
| 2288 | Scorecard Completion Metrics Dashboard | Enterprise Results | Closed | Jul 2025 | Aug 2025 |
| 2395 | Executive Summary — Elderly Prison Population (55–64, 65+) | Research | Closed | Aug 2025 | Jan 2026 |
| 2427 | Security Threat Group (STG) Dashboard | Correctional Operations | Active | Aug 2025 | — |
| 2475 | Strength in Families Eligibility Dashboard | Correctional Operations | Closed | Sep 2025 | Mar 2026 |
| 2547 | Administrative Segregation & Maximum Custody Dashboard | Correctional Operations | Pending | Sep 2025 | — |
| 2698 | Fentanyl Task Force Dashboard | Correctional Operations | Closed | Oct 2025 | Nov 2025 |
| 2741 | Reception Center Counts Dashboard | Business Operations | Closed | Oct 2025 | Feb 2026 |
| 2773 | PEAR Behavior Observation Dashboard | Correctional Operations | Closed | Nov 2025 | Dec 2025 |
| 2806 | PEAR Misconduct Infraction Risk Dashboard | Enterprise Results | Closed | Nov 2025 | Dec 2025 |
| 2807 | PEAR Misconduct Sanction Risk Dashboard | Enterprise Results | Closed | Nov 2025 | Dec 2025 |
| 2824 | DAT Dashboard — CCD Testing Rates Page | Community Interactions | Closed | Nov 2025 | Mar 2026 |
| 2932 | ATLAS Custody Staffing Dashboard | Correctional Operations | Active | Jan 2026 | — |
| 2933 | Recommission ATLAS Custody Staffing Dashboard | Business Operations | Closed | Jan 2026 | Jan 2026 |
| 2995 | Initial Build — Security Threat Group Dashboard | Correctional Operations | Active | Jan 2026 | — |

**Portfolio highlights:**
- 28 features across correctional operations, enterprise performance, research, and community interactions.
- Products span automated Power BI dashboards, recurring reports (daily/weekly/monthly/quarterly/annual), and research analytics.
- Stakeholders include Prisons, Mission Housing, Health Services, Reentry, HR, Security Management, PEAR Misconduct workgroup, Fentanyl Task Force.

---

## Epic 2 — Data Analysis & Research

**ID 24 | Area: Correctional Operations | Created: Feb 2023 | Status: Active**

> Parent container for BIOS work involving data models, EDA/profiling, or inferential and causal analytics.

### Features

| ID | Title | Value Area | Status | Created | Closed |
|----|-------|-----------|--------|---------|--------|
| 59 | Risk Assessment Scale for Prison (RASP) — Regression Model | Correctional Operations | Removed | Oct 2023 | — |
| 68 | Washington All Payers Claims (WAPC) — Phase 1 | Community Interactions | Closed | Nov 2023 | Aug 2025 |
| 120 | WADOC Release Cohort Database Integration | Community Interactions | Closed | Jan 2024 | Oct 2024 |
| 555 | IMRS Machine Learning Model (NLP/classification POC) | Correctional Operations | Closed | May 2024 | Oct 2024 |
| 1749 | Washington All Payers Claims (WAPC) Analysis — Phase 2 | Research | Active | Feb 2025 | — |
| 2495 | Data Covariance — DAT Features vs. Contraband & Violence | Research | Active | Sep 2025 | — |
| 2588 | TMVSA Recidivism A/B Testing | Enterprise Results | Closed | Sep 2025 | Oct 2025 |
| 2800 | WAPC Analysis — Opioid Prescriptions (Query 12) | Research | Active | Nov 2025 | — |
| 2840 | WADOC Recidivism Measure White Paper | Enterprise Results | Closed | Nov 2025 | Mar 2026 |
| 2869 | Women's Mental Health Research Paper | Research | Closed | Dec 2025 | Jan 2026 |
| 2878 | Assist on ISRB Recidivism Study | Research | Removed | Dec 2025 | — |
| 2986 | APCD Query 1 — Healthcare Coverage RMD Notebook | Research | Active | Jan 2026 | — |

**Portfolio highlights:**
- Machine learning proof-of-concept (NLP classification of free-text incident reports with Recidiviz/CSG grant).
- Predictive and causal modeling: regression (RASP), A/B testing (TMVSA recidivism), covariance analysis.
- Healthcare data linkage: WAPC/APCD claims data for a DOC release cohort (2016–2022), opioid prescriptions, women's PTSD/opioid intervention study.
- Release cohort database design and integration (SQL, demographics, risk factors, outcomes).
- Public-facing white paper on recidivism methodology and reproducible RMD notebooks.

---

## Epic 3 — Agency Initiatives

**ID 1365 | Area: Enterprise Results | Created: Oct 2024 | Status: Active**

> General-purpose container for features conceived from agency-level directives and executive initiatives.

### Features

| ID | Title | Value Area | Status | Created | Closed |
|----|-------|-----------|--------|---------|--------|
| 76 | Reentry Dashboard | Correctional Operations | Closed | Dec 2023 | Mar 2026 |
| 512 | OCM Standalone Dashboard | Enterprise Results | Closed | May 2024 | Oct 2024 |
| 1300 | Scorecard Dashboard | Correctional Operations | Closed | Sep 2024 | Jan 2026 |
| 1366 | Pro-Equity Anti-Racism (PEAR) Initiative Reporting | Enterprise Results | Closed | Oct 2024 | Aug 2025 |
| 2088 | Reimagine Visitation Study | Enterprise Results | Pending | May 2025 | — |

**Portfolio highlights:**
- Delivered BI tools for high-visibility executive and legislative initiatives: Reentry Scorecard, OCM presentations, PEAR anti-racism reporting.
- Supported PEAR (Governor's Executive Order 22-04) with equity dashboards covering racial/ethnic disparities in behavior observations, infractions, and sanctions.
- Visitation study scoped by direction from Office of the Secretary.

---

## Epic 4 — Cross-Unit Collaboration

**ID 31 | Area: Business Operations | Created: Feb 2023 | Status: Active**

> Parent container for BIOS work items involving cross-unit collaboration between BIOS and other RDA sections (Data Analytics, Health Services Infrastructure, Research).

### Features

| ID | Title | Value Area | Status | Created | Closed |
|----|-------|-----------|--------|---------|--------|
| 515 | RDA Ad-Hoc Stories (peer review & data requests) | Business Operations | Closed | May 2024 | Aug 2025 |
| 1127 | Prisons Aging Population Data Model | Correctional Operations | Closed | Aug 2024 | Nov 2025 |
| 1284 | RDA Health Services Data Requests | Business Operations | Closed | Sep 2024 | Jul 2025 |
| 1327 | Women's Pathways Studies (Research collab) | Research | Closed | Sep 2024 | Jan 2025 |
| 1818 | Data Analytics Stand-ups | Process Improvement | Active | Mar 2025 | — |
| 2005 | Design of RDA Recognition Program | Process Improvement | Closed | May 2025 | Jul 2025 |
| 3005 | Production Audit — FldPop Table | Process Improvement | Active | Jan 2026 | — |
| 3045 | Production File Review & Audit Process Improvement | Process Improvement | Active | Feb 2026 | — |

**Portfolio highlights:**
- Predictive analytics: aging prison population data model (CDO-directed), R-based forecasting.
- Cross-unit peer review and code review pipeline (RDA data analytics, health services, research).
- Structured collaboration (stand-ups, ad-hoc requests) bridging BIOS, Infrastructure, and Health Services.
- Led RDA recognition program design.

---

## Epic 5 — Process Improvements

**ID 198 | Area: Business Operations | Created: Mar 2024 | Status: Active**

> Repository dedicated to enhancing and standardizing Agile DevOps processes for the BIOS team and RDA unit.

### Features

| ID | Title | Value Area | Status | Created | Closed |
|----|-------|-----------|--------|---------|--------|
| 314 | Report Automation | Process Improvement | Closed | Apr 2024 | Jan 2026 |
| 370 | User Guide for BIOS Agile Process | Business Operations | Closed | Apr 2024 | Feb 2025 |
| 866 | Documentation Updates (repos, README, changelogs) | Process Improvement | Closed | Jul 2024 | Dec 2024 |
| 1161 | RDA Strategic Planning Alignment | Process Improvement | Closed | Aug 2024 | Aug 2025 |
| 1250 | BIOS Process Improvement (Agile, repo management) | Process Improvement | Active | Sep 2024 | — |
| 1251 | BIOS Performance Development Planning | Process Improvement | Closed | Sep 2024 | Aug 2025 |
| 2324 | RDA PBI Landing Page | Process Improvement | Active | Jul 2025 | — |
| 2325 | RDA PBI Process Improvement | Process Improvement | Active | Jul 2025 | — |
| 2326 | RDA Production Tables — Quality Assurance | Process Improvement | Closed | Jul 2025 | Jan 2026 |
| 2706 | Positron Development Environment (VS Code/R/SQL) | Process Improvement | Closed | Oct 2025 | Jan 2026 |

**Portfolio highlights:**
- Formalized BIOS Agile process: ADO user guides, sprint ceremonies, backlog management.
- Report automation (Power Automate, scheduled SQL, gateway refresh).
- Standardized Git repos: skeleton files, README, CHANGELOG, `.gitignore`, peer review.
- Positron/VS Code IDE configurations (JSON settings, extensions) for R, SQL, Markdown.
- RDA-wide Power BI governance: landing page, production table QA, PBI template alignment.
- Strategic planning participation at the RDA unit level.

---

## Aggregate Portfolio Summary

| Epic | Features | Value Areas | Period |
|------|----------|-------------|--------|
| Business & Ops Surveillance Reports | 28 | Correctional Ops, Enterprise Results, Business Ops, Research, Community Interactions | Jan 2023 – present |
| Data Analysis & Research | 12 | Research, Correctional Ops, Enterprise Results, Community Interactions | Feb 2023 – present |
| Agency Initiatives | 5 | Enterprise Results, Correctional Operations | Oct 2024 – present |
| Cross-Unit Collaboration | 8 | Business Ops, Correctional Ops, Research, Process Improvement | Feb 2023 – present |
| Process Improvements | 10 | Process Improvement, Business Ops | Mar 2024 – present |
| **Total** | **63 features** | 7 value areas | **Jan 2023 – Dec 2028** |

---

## Technical Stack

| Category | Technologies |
|----------|-------------|
| BI & Visualization | Power BI (semantic models, DAX, templates, governance) |
| Data & ETL | SQL (T-SQL, complex queries, scheduling), SAS (legacy → SQL migration) |
| Statistical Analysis | R (ggplot2, reshape2, ANOVA, regression, correlation, effect sizes) |
| ML / AI | NLP text classification (IMRS POC), A/B testing, predictive modeling |
| Notebooks | R Markdown (RMD), reproducible analytical notebooks |
| DevOps | Azure DevOps (work items, boards, repos), Git, pull requests, code review |
| Automation | Power Automate, gateway-based refresh, scheduled SQL jobs |
| IDE / Environment | Positron / VS Code, JSON settings, extensions for R/SQL/Markdown |
| Data Governance | PBI landing page, production table QA, RDA template, SharePoint lists |

---

## CV-Ready Bullets — Data Scientist

- **Product-owned 5 Agile epics** (63+ features) for the Washington DOC Business Intelligence & Operations Surveillance (BIOS) program, directing a cross-functional team of data analysts and engineers on dashboards, research studies, and automation pipelines.
- Led **applied research and statistical analysis**: regression modeling, ANOVA, Spearman/Kendall correlation, t-tests, effect sizes (Cohen's d), and EDA in R for studies on aging populations, restrictive housing, and mental health outcomes.
- Delivered **NLP machine learning proof-of-concept** (IMRS incident report classification) in partnership with Recidiviz and the Council of State Governments, demonstrating AI application in corrections data.
- Directed **healthcare data integration and analysis** across Washington All Payers Claims (APCD) data for DOC release cohorts (2016–2022): opioid prescriptions, women's PTSD/opioid intervention, healthcare coverage outcomes.
- Supervised **30+ Power BI dashboards and recurring reports** across correctional operations, reentry, equity (PEAR), and staffing; defined metrics, counting rules, and stakeholder requirements with Health Services, Prisons, and Reentry.
- Built and maintained **reproducible analytics pipelines**: R Markdown notebooks, SQL ETL, and version-controlled Git repos with peer review, documentation, and Agile work item tracking.

---

## CV-Ready Bullets — AI / Data Engineer

- **Product-owned 5 Agile epics** managing the end-to-end delivery of BI products: SQL ETL design, Power BI semantic models, automated pipelines, and governance for a large corrections agency.
- Designed and oversaw **SQL ETL pipelines** for 30+ operational dashboards; led SAS-to-SQL migration for Reception Center processing to enable automated scheduling and eliminate manual intervention.
- Implemented **ML proof-of-concept for free-text classification** (IMRS incident reports) using NLP, coordinating technical delivery with external foundation partners (Recidiviz, CSG).
- Drove **pipeline automation**: Power Automate flows, gateway-based Power BI refresh, and scheduled SQL jobs for daily/weekly/monthly/quarterly/annual recurring reports.
- Established **BI DevOps standards** for RDA: Azure DevOps work items, Git repositories, PR peer review, skeleton files, production table QA, and Positron/VS Code IDE configurations for R/SQL.
- Led **Power BI governance**: RDA dashboard landing page, RDA template alignment, permissions, production QA, and Power BI governance committee preparation.

---

## Employment History Snippet — Data Scientist

**Product Owner, Business Intelligence & Operations Surveillance (BIOS)**  
Washington State Department of Corrections — Research & Data Analytics Division  
*[Start date] – Present*

Manage a cross-functional team of analysts delivering BI products and applied research across a large corrections agency. Own 5 Agile epics (63+ features) spanning operational dashboards, statistical research, ML prototypes, and process improvement. Deliver Power BI dashboards and recurring reports to facility leadership and executive stakeholders. Lead statistical research on incarcerated populations (aging trends, restrictive housing, mental health outcomes), applying regression, ANOVA, and correlation analyses in R. Supervised an NLP/ML proof-of-concept for free-text classification of incident reports, in partnership with Recidiviz and the Council of State Governments. Direct healthcare data analysis using Washington APCD claims data and design reproducible R Markdown notebooks and SQL ETL pipelines maintained in Azure DevOps and Git.

---

## Employment History Snippet — AI / Data Engineer

**Product Owner, Business Intelligence & Operations Surveillance (BIOS)**  
Washington State Department of Corrections — Research & Data Analytics Division  
*[Start date] – Present*

Own technical delivery of 5 Agile epics (63+ features) covering BI infrastructure, ML prototyping, and automation for a large public-sector corrections agency. Design SQL ETL pipelines for 30+ Power BI dashboards; led SAS-to-SQL migration enabling automated gateway refresh. Oversaw NLP/ML proof-of-concept (incident report classification) with external grant partners. Implement automated reporting pipelines (Power Automate, scheduled SQL, gateway refresh) for daily through annual cadences. Establish engineering standards across Azure DevOps work items, Git repos, PR review, production table QA, and Positron/VS Code IDE configurations for R/SQL/Markdown workflows.

---

*Source: `ado-tree-work.csv` — 5 Epic work items, 63 Features, work item types include Epic, Feature, User Story, Task.*
