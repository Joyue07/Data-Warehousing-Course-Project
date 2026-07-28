# Data Warehousing Project — University Case
 
Dimensional modeling project for a fictitious higher-education case, built as part of the IS5 Data Warehousing course. The goal was to design a data warehouse that supports decision-making around academic programs, courses, and student registrations, following Kimball's dimensional modeling methodology.
 
## 🎯 Project Overview
 
Acting as a BI Developer team, we designed a dimensional model iteratively across several milestones — starting from a Bus Matrix and Prioritization Grid, then drafting and refining star schemas for each business process as the design matured.
 
The warehouse supports four business processes:
 
- **Program Enrollment** — tracking students enrolling into programs
- **Program Application** — tracking applicants from submission through selection, ranking, and invitation
- **Course Registration** — tracking students registering for courses
- **Program Course Management** — tracking which courses belong to which programs over time
## 🏗️ Methodology
 
Design followed the standard four-step Kimball process for each business process:
 
1. **Select the business process**
2. **Declare the grain**
3. **Identify the dimensions**
4. **Identify the facts**
A **Prioritization Grid** (feasibility vs. business impact) and a **Bus Matrix** (processes × shared dimensions) were used to plan which processes to model first and to spot conformed dimensions across processes.
 
## 🧩 Fact Tables
 
| Process | Grain | Fact Type | Key Measures |
|---|---|---|---|
| Program Enrollment | One row per student, per program, per date | Transaction | Enrollment Count |
| Program Application | One row per applicant, per program, per application date | Accumulating Snapshot | Selection/Ranking/Invitation Counts, Ranking Score, stage-to-stage date lags |
| Course Registration | One row per student, per course, per date | Transaction | Registration Count |
| Program Course Management | One row per course, per program, per date | Periodic Snapshot | Course Count |
 
The Program Application fact is an accumulating snapshot because a single application progresses through several milestone dates (application → selection → ranking → invitation), and we wanted one row that updates as it moves through the pipeline.
 
## 🧱 Dimension Tables
 
- **DimStudent / DimApplicant / DimStaff** — person dimensions. Identity number and name changes are tracked with **SCD Type 2**; contact details (phone, email, address) are overwritten with **SCD Type 1** since history isn't needed for those; biographical attributes like gender and birth date are **SCD Type 0** (fixed).
- **DimProgram** — mostly static attributes (code, name, language, level, credits, delivery mode) as **SCD 0**; the linked program coordinator is **SCD 2** since coordinators change over time.
- **DimCourse** — static descriptive attributes (**SCD 0**), linked to the offering organization.
- **DimOrganization** — models the University → Faculty → Department → Unit hierarchy; each level has a "Head" staff role tracked as **SCD 2**.
- **DimDate** — standard calendar attributes plus academic-year/semester fields (HT/VT terms), since the academic calendar doesn't align with the Gregorian year.
- **Role-playing dimensions** (e.g. `DimProgramCoordinator`, `DimUniversityHead`, `DimUnitHead`) — views of `DimStaff` reused in different roles across fact tables.
- **BridgeCourseToStaff** — a bridge table handling the many-to-many relationship between courses and coordinating staff, with SCD2-style effective/expiration dating.

 
## 🛠️ Tools
 
- **draw.io** — Bus Matrix, Prioritization Grid, and dimensional model diagrams
## 🤝 Project Collaboration
 
This project was completed as a group assignment for the IS5 Data Warehousing course at Stockholm University. Team member names are omitted here for privacy.
 
## ⚖️ Academic Integrity Notice
 
This repository shares our own dimensional modeling work. The original case description, milestone instructions, and grading materials are the property of the course instructor and are not reproduced here.
