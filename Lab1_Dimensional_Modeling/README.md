# Lab 1: Dimensional Modeling & Star Schema Construction

## 🎯 Objective
The goal of this lab is to design and implement a relational data warehouse schema in **MS SQL Server**. This involves creating a dedicated database, writing SQL scripts to generate dimension and fact tables, and establishing primary and foreign key relationships to form a standard Star Schema.

## 🛠️ Tools & Technologies
* **Database Engine:** Microsoft SQL Server
* **Language:** T-SQL
* **Modeling:** SQL Server Database Diagrams

## 🚀 Implementation Steps

### 1. Database Initialization
* Connected to the local SQL Server Database Engine (`localhost`).
* Created a new, empty database named `LabDW` to host the data warehouse architecture.

### 2. Table Creation
* **Dimension Tables:** Executed T-SQL scripts to create `DimProduct` and `DimDate`, defining precise data types to accommodate dimensional attributes.
* **Fact Table:** Created the `FactProductInventory` table, identifying the necessary quantitative measures and foreign key columns required to link with the dimensions.

### 3. Key Constraints & Relationships
* **Composite Primary Key:** Configured a composite primary key for `FactProductInventory` utilizing the combination of `ProductKey` and `DateKey` to ensure unique daily snapshot records.
* **Foreign Keys:** Established 1-to-many relationships between the fact table and the dimension tables, ensuring referential integrity across the data warehouse.

### 4. Schema Validation
* Generated a **Database Diagram** (`ProductInventoryStarSchema`) to visually validate the physical implementation of the Star Schema architecture.
