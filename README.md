# 🚗⚡ Global Electric Vehicle (EV) Data Analysis — Power BI Dashboard  
A complete end-to-end Power BI project analyzing global electric vehicle adoption, sales, charging infrastructure, energy demand, and market trends using IEA Global EV Data 2024.

---

## 📌 Project Overview  
This project analyzes global EV (Electric Vehicle) growth trends using the **IEA Global EV Data 2024** dataset.  
The dashboard provides clear insights into:

- EV Sales (Battery Electric Vehicles & Plug-in Hybrid Vehicles)  
- EV Stock Growth  
- Charging Infrastructure (Public & Private points)  
- Electricity Demand from EVs  
- EV Market Share by Country  
- Country-wise & Year-wise EV performance  
- Worldwide shift from fuel vehicles to electric mobility

This project demonstrates strong skills in **Power Query, Data Modeling, DAX, Business Intelligence, and Dashboard Design**.

---

## 🛠 Files Included  
| File | Description |
|------|-------------|
| **EV_DATA_ANALYSIS1.pbix** | Main Power BI report |
| **IEA Global EV Data 2024.csv** | Source dataset |
| **README.md** | Project documentation |

---

## 🎯 Objectives of the Project  
- Analyze worldwide electric vehicle adoption using real-world data  
- Compare EV performance across countries and years  
- Study BEV vs PHEV sales and stock trends  
- Examine charging infrastructure growth  
- Understand electricity demand created by EVs  
- Provide actionable insights using an interactive Power BI dashboard  

---

## 📂 Dataset Description (IEA Global EV Data 2024)

### Key Columns Used:
- Country  
- Year  
- EV Stock (Total EVs in use)  
- EV Sales (Annual EV purchases)  
- BEV Sales (Battery Electric Vehicles)  
- PHEV Sales  
- Public Charging Points  
- Private Charging Points  
- Electricity Demand (GWh)  
- Market Share (%)  

This dataset enables **trend analysis**, **global comparison**, and **EV sector intelligence**.

---

# 🛠 Step-by-Step Project Workflow (End-to-End)

## 1️⃣ Data Import  
- Open Power BI Desktop  
- Go to **Get Data → Text/CSV**  
- Load `IEA Global EV Data 2024.csv`  
- Click **Transform Data** to enter Power Query  

---

## 2️⃣ Power Query — Data Cleaning  
Performed the following transformations:

- Renamed columns for readability  
- Removed unnecessary rows & null fields  
- Standardized data types (Year → Whole Number, numeric fields → Decimal)  
- Cleaned country names  
- Ensured EV stock, sales, and charging columns are numeric  
- Prepared a clean dataset for modeling  

---

## 3️⃣ Data Modeling  
Since the dataset is structured, a simple model was used:

### Tables:
- **EV_Data** (fact table with all EV metrics)  
- **DimDate** (calendar table for time intelligence)

### Relationship:
- `EV_Data[Year]` → `DimDate[Year]`

This enables accurate **YoY**, **MoM**, and **time-based** calculations.

---

## 4️⃣ DAX Measures Created  

```DAX
Total EV Sales = SUM(EV_Data[EV_Sales])

Total EV Stock = SUM(EV_Data[EV_Stock])

Total Public Chargers = SUM(EV_Data[Public_Charging_Points])

Total Private Chargers = SUM(EV_Data[Private_Charging_Points])

EV Electricity Demand = SUM(EV_Data[Electricity_Demand])

EV Sales YoY (%) =
VAR Prev = CALCULATE([Total EV Sales], SAMEPERIODLASTYEAR(DimDate[Date]))
RETURN DIVIDE([Total EV Sales] - Prev, Prev)

Market Share (%) = AVERAGE(EV_Data[Market_Share])
