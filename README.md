# 🎵 Project_DWBI – Chinook Music Sales Data Warehouse & BI Solution

A full-stack **Data Warehousing and Business Intelligence (DWBI)** solution developed using the **Chinook** dataset. This project demonstrates data integration, dimensional modeling, ETL processing with SSIS, OLAP cube creation with SSAS, and Power BI reporting.

---

## 📁 Dataset

**Chinook Database**  
A sample digital music store database containing:
- Customers, Invoices, Employees
- Tracks, Albums, Artists, Genres, Media Types

🔗 [Original Chinook Dataset](https://www.kaggle.com/datasets/anurag629/chinook-csv-dataset)

---

## 🧱 Project Architecture

![Screenshot 2025-04-17 223845](https://github.com/user-attachments/assets/69297ecd-c950-479a-acd2-7e6f8263a0ab)

1. **Source Systems**
   - Chinook OLTP SQL Database
   - Additional source: `TrackPlayCounts.txt`

2. **Staging Area**
   - Data loaded into staging tables (e.g., `StgCustomer`, `StgInvoice`, etc.)

3. **ETL Process**
   - Built using **SQL Server Integration Services (SSIS)**
   - Packages: `Load_Staging.dtsx`, `Load_DW.dtsx`, `Data_Profiling.dtsx`, `Accumulating_Fact.dtsx`

4. **Data Warehouse**
   - Modeled using a **Snowflake Schema**
   - Fact Table: `FactSales`
   - Dimension Tables: `DimCustomer`, `DimTrack`, `DimDate`, `DimEmployee`, `DimArtist`, `DimAlbum`, `DimGenre`, `DimMediaType`

5. **OLAP Cube**
   - Created with **SQL Server Analysis Services (SSAS)**
   - Cube Name: `ChinookDW_SSAS`
   - Measures: `Total Sales`, `Average Order Value`, `Order Count`
   - Hierarchies: Time, Music, and Geographic

6. **Reporting**
   - Excel OLAP Operations: Slice, Dice, Drill-Down, Roll-Up, Pivot
   - Power BI Dashboards & Reports

---

## 📊 Data Warehouse Design

### ➤ Fact Table: `FactSales`
- `SalesSK`, `CustomerSK`, `TrackSK`, `EmployeeSK`, `DateKey`
- Measures: `UnitPrice`, `Quantity`, `ExtendedPrice`
- Accumulating Fields: `txn_create_time`, `txn_complete_time`, `process_time_hours`

### ➤ Dimension Tables
| Table         | SCD Type | Key Attributes                                      |
|---------------|----------|-----------------------------------------------------|
| DimCustomer   | Type-2   | FirstName, LastName, Email, City, Country, etc.    |
| DimEmployee   | Type-2   | Title, BirthDate, HireDate, Country, etc.          |
| DimTrack      | Type-1   | Name, Album, Genre, UnitPrice, etc.                |
| DimDate       | -        | FullDate, Year, Quarter, Month, Day, etc.          |
| DimAlbum      | Type-1   | Title, Artist                                       |
| DimArtist     | Type-1   | Name                                                |
| DimGenre      | Type-1   | Name                                                |
| DimMediaType  | Type-1   | Name                                                |

---

## 🔄 ETL Development (SSIS Packages)

- `Chinook_Load_Stagging.dtsx`: Load source data into staging
- `Chinook_Load_DW.dtsx`: Transform and load data into DW
- `Data_Profiling.dtsx`: Check nulls, duplicates, and data types
- `Accumulating_Fact.dtsx`: Update transaction completion & calculate processing time

---

## 🧮 OLAP Cube (SSAS)

- Cube Name: `ChinookDW_SSAS`
- Measures: Total Sales, Order Count, Average Order Value
- Hierarchies:
  - **Time**: Year → Quarter → Month → Day
  - **Music**: Artist → Album → Track
  - **Geographic**: Country → State → City

---

## 📈 Power BI Reporting

### ✅ Report Highlights
1. **Matrix Report** – Conditional formatting & stepped layout
2. **Interactive Dashboard** – Cascading filters, slicers, KPIs
3. **Drill-Down Analysis** – Multi-level country & time drill-downs
4. **Drill-Through Report** – Genre & artist-level exploration with breadcrumbs

---

## 💻 Technologies Used

- SQL Server
- SQL Server Integration Services (SSIS)
- SQL Server Analysis Services (SSAS)
- Microsoft Excel (OLAP)
- Power BI
- Chinook Database

---

## 📚 Learning Outcomes

- Implemented a full end-to-end BI pipeline
- Applied dimensional modeling principles
- Developed Type-1 and Type-2 slowly changing dimensions (SCD)
- Built analytical dashboards using OLAP and Power BI

---

## 📌 Author

**Ishara Madusanka**  

