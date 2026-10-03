# Data Warehousing Course Project — University Case & Labs

This repository contains work completed for the IS5 Data Warehousing course at Stockholm University, including a group data warehouse design project and three hands-on labs covering **dimensional modeling, ETL, and OLAP analysis**.

## University Case — Project Overview
The goal of the project was to design a data warehouse to support decision-making around academic programs, courses, and student registrations, following **Kimball's dimensional modeling methodology**.

As part of a BI development team, we iteratively designed the dimensional model across several milestones, starting with a Prioritization Grid and Bus Matrix, then developing and refining star schemas for each business process. 

The warehouse supports four business processes:
* Program Enrollment
* Program Application
* Course Registration
* Program Course Management

### Methodology
The dimensional models were designed following the four-step Kimball process:
1. Select the business process
2. Declare the grain
3. Identify the dimensions
4. Identify the facts

A **Prioritization Grid** was used to evaluate business impact and feasibility, while a **Bus Matrix** was used to identify shared and conformed dimensions across business processes.

### Fact Tables
* **Core Metrics:** Capture quantitative measures for program applications, enrollments, course registrations, and program management.
* **Fact Types:** Apply Transaction, Periodic Snapshot, and Accumulating Snapshot models to represent different business processes and event patterns.
* **Integration:** Connect fact tables with shared dimensions such as Student, Program, Course, and Date to support multidimensional analysis.

### Dimension Tables
* **DimStudent / DimStaff** — Manage student and staff attributes, including historical changes.
* **DimProgram / DimCourse** — Store academic attributes and coordinator-related information.
* **DimOrganization** — Represent university organizational structure and leadership.
* **DimDate** — Provide a custom academic calendar for time-based analysis.
* **Role-playing & Bridge Tables** — Support multiple staff roles and complex many-to-many relationships.

---

## Hands-on Labs (End-to-End BI Implementation)
The course also included three independent labs that provided practical experience in implementing and analyzing dimensional data warehouse models.

### Lab 1 — Dimensional Modeling & Star Schema
* Designed and implemented a star schema in **MS SQL Server** using DimProduct, DimDate, and FactProductInventory.
* Created dimension and fact tables using **SQL**, defining primary and foreign key relationships.
* Implemented a composite key for the fact table and validated the schema using SQL Server Database Diagrams.

### Lab 2 — ETL with SSIS
* Built an **ETL workflow** to load inventory data from Excel into a SQL Server data warehouse.
* Imported source data into a staging database using the SQL Server Import and Export Wizard.
* Applied data cleaning and transformation using Derived Column, Data Conversion, Conditional Split, Merge Join, and Lookup components in **SSIS**.
* Implemented **Slowly Changing Dimensions (SCD Type 1 and Type 2)** for the Product dimension.
* Generated daily inventory snapshots and loaded transformed data into the fact table, performing data quality checks using row sampling and data viewers.

### Lab 3 — OLAP & Multidimensional Analysis
* Built and deployed a multidimensional data model using **SQL Server Analysis Services (SSAS)**.
* Designed Date and Product dimensions, hierarchies (e.g., Fiscal Year-Semester-Quarter), and attribute relationships.
* Built an **OLAP cube** with measures including Unit Cost, Units In, Units Out, and Units Balance.
* Created **MDX** calculated members and KPIs, including inventory value and period-over-period growth.
* Connected the OLAP cube to **Excel and Power BI** for multidimensional analysis, visualizing results with interactive charts (e.g., waterfall charts for inventory fluctuations).

---

## Tools & Technologies
* **MS SQL Server** — Database implementation and dimensional model development.
* **SSIS** — ETL workflows, data transformation, cleansing, and SCD Type 1/2.
* **SSAS & Visual Studio** — OLAP cubes, dimensions, hierarchies, and KPI development.
* **MDX** — Multidimensional queries and calculated members.
* **Power BI & Excel** — OLAP analysis, reporting, and data visualization.
* **draw.io** — Bus Matrix, Prioritization Grid, and dimensional model diagrams.

---

## Project Collaboration
The University Case was completed as a group assignment for the IS5 Data Warehousing course at Stockholm University. Team member names are omitted here for privacy.

## Academic Integrity Notice
This repository contains our own dimensional modeling work and implementations developed for the course. The original case description, milestone instructions, and grading materials are the property of the course instructor and are not reproduced here.
