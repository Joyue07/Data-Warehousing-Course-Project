# Lab 2: ETL Pipeline Development with SSIS

## 🎯 Objective
The goal of this lab is to design and implement an end-to-end **ETL (Extract, Transform, Load)** pipeline using **SQL Server Integration Services (SSIS)**. The pipeline extracts inventory data from flat files (Excel), cleanses and transforms it in a staging area, and loads it into the dimensional data warehouse (`LabDW`).

## 🛠️ Tools & Technologies
* **ETL Platform:** SQL Server Integration Services (SSIS) / Visual Studio
* **Database:** MS SQL Server (Staging & Data Warehouse)
* **Data Sources:** Microsoft Excel flat files

## 🚀 Implementation Steps

### 1. Data Staging & Extraction
* Created a temporary staging database (`Labstaging`) in SQL Server.
* Utilized the **SQL Server Import and Export Wizard** to extract raw inventory data (`Inventory_Beginning`, `Inventory_UnitsIn`, `Inventory_UnitsOut`) from Excel files into staging tables.

### 2. Data Transformation & Cleansing
* **Handling NULLs:** Applied the **Derived Column** component to replace NULL values with standard placeholders (e.g., "NotAvailable").
* **Type Casting:** Utilized the **Data Conversion** component to resolve data type mismatches between the source flat files and the target data warehouse schema.

### 3. Dimension Loading & SCD Processing
* **DimDate:** Loaded temporal data directly into the Date Dimension.
* **DimProduct (SCD):** Engineered a data flow task to load the Product Dimension while implementing **Slowly Changing Dimension (SCD)** logic. Configured both **SCD Type 1** (overwrite) and **SCD Type 2** (historical tracking) to manage product attribute changes over time.

### 4. Fact Table Loading
* **Calculations & Snapshots:** Extracted start and end dates using **Set Parameters** to generate daily product snapshots.
* **Data Merging:** Used the **Merge Join** component to integrate product and date dimension data.
* **Surrogate Key Retrieval:** Implemented the **Lookup** component to retrieve valid surrogate keys from `DimProduct`.
* **Filtering:** Applied the **Conditional Split** component to route and filter out unnecessary data before finalizing the load into `FactProductInventory` via the **OLE DB Destination**.

### 5. Testing & Debugging
* Inserted **Row Sampling** components and enabled **Data Viewers** between critical data flow paths to validate data transformations and ensure pipeline accuracy before full execution.
