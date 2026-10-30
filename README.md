<!-- Profile README: create a public repo named exactly as your GitHub username and paste this in as README.md -->

# Hi, I'm Ankur 

**Research & Data Analyst at the University of Cambridge** · building data platforms, dashboards and automation that replace manual processes in higher education.

I take messy, multi-source operational data, from legacy spreadsheets to live system feeds, and turn it into reliable, automated reporting. My work spans the Microsoft data stack end to end: Fabric lakehouses and SQL at the back, Power Automate pipelines in the middle, and Power BI at the front, with Python and LLM APIs where they fit.

📍 Cambridge, UK · ✉️ as3827@cam.ac.uk/ ankur11sharma25@gmail.com

---

## 🛠️ Tech stack

![Microsoft Fabric](https://img.shields.io/badge/Microsoft%20Fabric-117865?style=flat)
![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=flat&logo=powerbi&logoColor=black)
![SQL](https://img.shields.io/badge/SQL-4479A1?style=flat&logo=databricks&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![Power Automate](https://img.shields.io/badge/Power%20Automate-0066FF?style=flat&logo=powerautomate&logoColor=white)
![Power Apps](https://img.shields.io/badge/Power%20Apps-742774?style=flat&logo=powerapps&logoColor=white)
![Dataverse](https://img.shields.io/badge/Dataverse-088142?style=flat)
![SharePoint](https://img.shields.io/badge/SharePoint-0078D4?style=flat&logo=microsoftsharepoint&logoColor=white)
![Excel](https://img.shields.io/badge/Excel-217346?style=flat&logo=microsoftexcel&logoColor=white)

**Languages:** DAX · Power Query M · SQL · Python · VBA
**Platforms:** Microsoft Fabric (Lakehouse, SQL database, pipelines) · Power Platform · SharePoint · REST APIs · LLM APIs
**Currently:** deepening SQL and Python · Microsoft PL-300 *(target: Jan 2027)*

---

## 📂 Projects at a glance

| # | Project | Stack | Status |
|---|---------|-------|--------|
| 1 | [Handshake migration: data preservation, Fabric lakehouse and 64-dashboard rebuild](#1-handshake-migration-data-preservation-fabric-lakehouse-and-64-dashboard-rebuild) | SQL, Fabric Lakehouse, pipelines, Power BI, DAX | ✅ Done |
| 2 | [Year-on-year reporting framework](#2-year-on-year-reporting-framework) | Power Query, DAX, research methods | 🟡 In progress |
| 3 | [AI-assisted job posting screening](#3-ai-assisted-job-posting-screening) | Python, REST API, LLM, statistics | ✅ Done |
| 4 | [Data and Digital Services request portal](#4-team-request-portal) | Microsoft Forms, Power Automate, SharePoint, Outlook | ✅ Done |
| 5 | [Operations dashboard for senior executives](#5-operations-dashboard-for-senior-executives) | Power BI, DAX, Power Automate | ✅ Done |
| 6 | [Development of Casework Management System](#6-casework-system-modernisation-access--dataverse) | Dataverse, Power Apps, Access VBA, REST API | 🟡 In progress |
| 7 | [Operational Value Index for UK higher education](#7-operational-value-index-for-uk-higher-education) | Research, risk modelling | 🟡 In progress |

> These are workplace projects. Code and data are internal, so each is shared as a write-up of the problem, approach and outcome, with no confidential data.

---

## 1. Handshake migration: data preservation, Fabric lakehouse and 64-dashboard rebuild

**Problem:** As part of Handshake's global platform migration, the University's historical student data would not carry over to the new platform. Years of records risked being lost, and all **64 Power BI dashboards** the department relies on had to be rebuilt on the new data **within 10 weeks**, with many teams and processes depending on them to keep operations running.

**What I did**
- Preserved the historical Handshake data in a SQL database, rebuilding it as a relational model with the same tables, keys and relationships as the original platform
- Built a Microsoft Fabric Lakehouse that integrates the preserved historical data with the new live Handshake data, and automated the whole pipeline end to end
- Rebuilt all **64 dashboards in 10 weeks** on the integrated data, covering appointments, events, fairs, employers and jobs, labour market information, user feedback, current students and postdoctoral researchers
- Planned the rebuild around dependencies, using a priority-tiered progress register so the dashboards that operations relied on most came first, each tracked through build, review and validation
- Diagnosed and fixed model issues introduced by the new platform, such as inactive relationships and filter directions that left visuals blank
- Resolved identifier mismatches between Handshake's internal IDs and legacy University IDs so demographic and engagement data joined correctly

**Outcome:** Delivered within the 10-week window. The University kept its full history of careers data in one automated platform alongside live data, and department operations continued without a reporting gap, with every dashboard validated against the old version.
<!-- TODO: add data volume (rows / years preserved), refresh schedule, and who uses the dashboards -->

---

## 2. Year-on-year reporting framework

**Problem:** Comparing several years of Careers Service data was unreliable: field formats had drifted between years, some data streams only existed in recent years, and calendar months don't match how a university runs.

**What I did**
- Started with consultation with frontline teams to understand how data was recorded before writing any code (qualitative before quantitative)
- Classified STEM vs non-STEM at school level rather than course level, trading minor precision for a stable, consistent baseline
- Excluded data streams that would distort comparisons, such as categories only tracked in recent years or already reported elsewhere
- Handled schema drift with an upstream append in Power Query, so historical files pass through the same cleaning steps as current ones
- Built an academic-day index (1 October to 30 September) in DAX so each term is compared with the same point in previous years

**Outcome:** Like-for-like year-on-year trends that leadership can trust across terms and years.

---

## 3. AI-assisted job posting screening

**Problem:** The Careers Service team manually reviewed every job posting that the platform's own checks held back, reading each description to spot scams and unsuitable roles.

**What I did**
- Built a Python pipeline that pulls pending postings from the Handshake API
- Sent each posting to an LLM with the service's vetting rules (for example MLM schemes, requests for upfront payments or bank details, vague descriptions), returning a structured JSON decision, confidence score and one-line reason
- Triaged results into approve, flag and reject lists, with staff keeping the final decision
- Evaluated the model statistically: analysed missing-field patterns as a risk signal, and tested accuracy against a baseline with a hypothesis test

**Outcome:** Staff review flagged exceptions instead of reading every posting, with a human approving every action.
<!-- TODO: add measured accuracy, number of postings screened, and review time saved -->

---

## 4. Data and Digital services request portal

**Problem:** Requests to the team arrived by scattered emails, with attachments landing in personal inboxes and OneDrive.

**What I did**
- Built a Microsoft Forms intake with Power Automate flows triggered from the team's shared mailbox
- Created a unique SharePoint folder for every new request automatically
- Moved form attachments from OneDrive into the matching request folder (parsing the form's file JSON) and archived each request email as HTML
- Sent confirmation emails from the shared mailbox, so replies return to the team rather than to individuals
- Matched follow-up emails to their request by tracking ID, using a trigger condition that scales to any number of requests

**Outcome:** Every request gets an ID, a folder and a confirmation, with no manual filing.

---

## 5. Operations dashboard for senior executives

**Problem:** Senior executives had no transparent view of the team's request volumes, status or workload to base decisions on.

**What I did**
- Built a Power BI dashboard on the portal's data: total requests, completed vs in-progress KPIs, status breakdown, monthly trends and workload by team member
- Locked headline KPIs with edit interactions so totals stay consistent while other visuals cross-filter
- Added estimated vs actual time tracking, with variance measures in DAX to support capacity planning

**Outcome:** Senior executives now have live, transparent insight into demand, delivery and capacity, which they use to inform decisions.
<!-- TODO: add requests tracked to date, or an example decision the dashboard informed -->

---

## 6. Development of Case management system (Access → Dataverse)

**Problem:** A university casework team had run case management on the same legacy setup for about 10 years: survey forms, a Microsoft Access database, per-case SharePoint folders and mail-merge letters. Data was duplicated across tools, ten intake forms each had different structures, and the database suffered file-locking with multiple users. Moving to a modern platform meant carrying a decade of case history with it.

**What I did**
- Led a review of the end-to-end process and mapped every data source and hand-off
- Wrote a VBA routine in Access that calls the survey platform's REST API on demand, as a workaround while premium connectors were unavailable
- Identified that student-record data and survey submissions shared no common key, and agreed a single identifier to link them
- Proposed moving to Dataverse; set up a Dev environment and am building a model-driven app with automated survey intake
- Designing a database to hold 10 years of legacy case data in the new structure, so historical cases stay searchable and reportable alongside new ones
- Scoped a phased pilot: internal cases first, external cases once the system is stable

**Outcome:** The head of department approved the move to Dataverse, replacing a system in use for a decade. The prototype, legacy data migration and a testing-and-recommendation paper are in progress.

---

## 7. Operational Value Index for UK higher education

**Idea:** A research paper proposing an Operational Value Index (OVI), a tool to help UK universities understand how to manage risk to their operations over the coming years.

**Status:** Scoping the literature review and refining the concept.

---

##  Next up

- **Public-data SQL project:** a modelled SQL database on HESA open data, with analytical queries, published here with full code
- **Open-source Python pipeline:** API → pandas → SQL → Power BI on public data, so the code behind my workplace projects can be shown in the open

---
## Notes:
There are few other projects which are currently inline and I will update them shortly.
## Get in touch

Open to **BI Developer, Systems and Data Analyst, Analytics Engineer and Data Engineer** roles in the UK. The quickest way to reach me is by texting me on teams as3827@cam.ac.uk.
