# Data Warehousing Project — University Case
 
Dimensional modeling project for a fictitious higher-education case, built as part of the IS5 Data Warehousing course. The goal was to design a data warehouse that supports decision-making around academic programs, courses, and student registrations, following Kimball's dimensional modeling methodology.
 
## 🎯 Project Overview
 
Acting as a BI Developer team, we designed a dimensional model iteratively across several milestones — starting from a Bus Matrix and Prioritization Grid, then drafting and refining star schemas for each business process as the design matured.
 
The warehouse supports four business processes:
 
- **Program Enrollment** 
- **Program Application** 
- **Course Registration** 
- **Program Course Management** 
## 🏗️ Methodology
 
Design followed the standard four-step Kimball process for each business process:
 
1. **Select the business process**
2. **Declare the grain**
3. **Identify the dimensions**
4. **Identify the facts**
A **Prioritization Grid** (feasibility vs. business impact) and a **Bus Matrix** (processes × shared dimensions) were used to plan which processes to model first and to spot conformed dimensions across processes.
 
## 🧩 Fact Tables

* **Core Metrics:** Capture quantitative data for Program Applications, Enrollments, Course Registrations, and Program Management.
* **Fact Types:** Utilize Transaction, Periodic Snapshot, and Accumulating Snapshot models to track both point-in-time events and multi-stage pipelines.
* **Integration:** Connect seamlessly with relevant dimensions (Student, Program, Course, Date) to enable multidimensional analysis.
 
## 🧱 Dimension Tables

* **DimStudent / DimStaff** — Manage personal profiles and historical changes.
* **DimProgram / DimCourse** — Store academic attributes and coordinator history.
* **DimOrganization** — Model university hierarchy and leadership.
* **DimDate** — Custom calendar for academic terms.
* **Role-playing & Bridge Tables** — Handle complex many-to-many relationships and multiple staff roles.

 
## 🛠️ Tools & Technologies
* **draw.io** — Bus Matrix, Prioritization Grid, and dimensional model diagrams.
* **Microsoft SSAS & Visual Studio** — Building OLAP cubes, dimensions, and partitions.
* **MDX** — Querying multidimensional data.
* **Power BI & Excel** — Data visualization and OLAP reporting.
  
## 🤝 Project Collaboration
 
This project was completed as a group assignment for the IS5 Data Warehousing course at Stockholm University. Team member names are omitted here for privacy.
 
## ⚖️ Academic Integrity Notice
 
This repository shares our own dimensional modeling work. The original case description, milestone instructions, and grading materials are the property of the course instructor and are not reproduced here.
