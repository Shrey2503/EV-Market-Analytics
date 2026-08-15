# 🚗 Electric Vehicle Market Analytics using Python, SQL and Power BI

An end-to-end **Electric Vehicle Market Analytics** project built using **Python, Pandas, NumPy, SQLite, SQL, Jupyter Notebook, and Power BI**.

The project analyzes electric vehicle registration data from the **Washington State Department of Licensing** to understand EV adoption, manufacturer performance, model popularity, vehicle technology, electric range, geographic distribution, and market concentration.

---

## 🎯 Project Objective 

The objective of this project is to analyze electric vehicle registration activity and identify meaningful patterns related to:

* EV adoption over time
* Manufacturer market leadership
* EV model popularity
* BEV vs PHEV adoption
* Electric vehicle range
* Manufacturer growth
* Market concentration
* New vs used EVs
* County-level EV adoption
* City-level EV activity
* ZIP-code level EV concentration
* Electric utility distribution
* Legislative district activity
* Primary vehicle use

### Analytics Workflow

```text
Official EV Data
       ↓
Python Data Preparation
       ↓
SQLite Database
       ↓
SQL Analysis
       ↓
Power BI
       ↓
Interactive Dashboard
       ↓
EV Market Insights
```

---

## 📊 Dashboard Preview

### Page 1 — Executive Overview

![Executive Overview](./IMAGES/Electric%20Vehicle%20Market%20Analytics%20Dashboard.png)

### Page 2 — Geographic Insights & Regional EV Adoption

![Geographic Insights](./IMAGES/Geographic%20Insights%20%26%20Regional%20EV%20Adoption.png)

### Page 3 — EV Trend & Technology Insights

![EV Trend & Technology Insights](./IMAGES/EV%20Trend%20%26%20Technology%20Insights.png)

---

## 🌐 Data Source

The dataset was obtained from the official **Washington State Open Data** portal.

### Dataset

**Electric Vehicle Title and Registration Activity**

**Publisher:** Washington State Department of Licensing (DOL)

### Official Dataset

[Washington State Electric Vehicle Title and Registration Activity](https://data.wa.gov/Transportation/Electric-Vehicle-Title-and-Registration-Activity/rpr4-cgyd/about_data)

> **Note:** The original dataset is large and is not included directly in this repository. Please download the latest dataset from the official Washington State Open Data portal using the link above.
### Important Fields

* Vehicle Type
* DOL Vehicle ID
* Model Year
* Make
* Model
* Primary Use
* Electric Range
* Odometer Reading
* New or Used Vehicle
* Sale Price
* Sale Date
* Transaction Type
* Transaction Date
* County
* City
* State
* Postal Code
* CAFV Eligibility
* Electric Utility
* Legislative District
* Electrification Fee Information

---

## 📁 Repository Structure

```text
EV-Market-Analytics/
│
├── IMAGES/
│   ├── Electric Vehicle Market Analytics Dashboard.png
│   ├── EV Trend & Technology Insights.png
│   └── Geographic Insights & Regional EV Adoption.png
│
├── POWER BI/
│   └── EV Market Analytics Dashboard.pbix
│
├── QUERIES/
│   └── EV_Analysis.ipynb
│
└── README.md
```

### File Description

| Folder / File               | Purpose                           |
| --------------------------- | --------------------------------- |
| `IMAGES/`                   | Power BI dashboard screenshots    |
| `POWER BI/`                 | Final Power BI dashboard file     |
| `QUERIES/EV_Analysis.ipynb` | Python data preparation and SQL analysis notebook |
| `README.md`                 | Project documentation              |

## 📌 Dataset Overview

The original dataset contained:

```text
Rows    : 1,809,203
Columns : 33
```

After removing exact duplicate records:

```text
Original Records : 1,809,203
Duplicate Rows   : 63
Final Records    : 1,809,140
```

The cleaned dataset was then loaded into SQLite for SQL analysis.

### Main Database Table

```text
registrations
```

---

# 🐍 Python Data Preparation

Python was used to inspect, clean, standardize, validate, and prepare the raw EV registration data before SQL analysis.

The complete workflow is available in:

```text
QUERIES/EV_Analysis.ipynb
```

## Libraries Used

* Python
* Pandas
* NumPy
* SQLite3
* Matplotlib
* Seaborn
* Jupyter Notebook

---

## 1. Data Loading

The official EV dataset was loaded into Pandas and inspected to understand:

* Dataset structure
* Data types
* Missing values
* Unique categories
* Numerical fields
* Categorical fields
* Geographic fields
* Vehicle characteristics

---

## 2. Missing Value Analysis

Missing values were identified across the dataset.

Important fields requiring attention included:

* Electric Range
* County
* State
* Postal Code
* Legislative District
* Sale Date
* Fee-related fields

Missing values were handled according to the analytical purpose of each field rather than applying the same treatment to every column.

---

## 3. Missing Value Handling

Examples of preparation included:

* Filling missing electric-range values using the median
* Handling missing county values
* Handling missing state values
* Handling missing postal-code values

This helped ensure important fields used in aggregation and visualization could be analyzed consistently.

---

## 4. Text Standardization

Text fields were standardized to improve consistency during grouping and aggregation.

Important fields included:

* Make
* Model
* County
* State

For example:

```text
TESLA
Tesla
tesla
```

could otherwise be treated as separate categories.

Standardization ensured consistent grouping during SQL analysis.

---

## 5. Duplicate Detection and Removal

The dataset was checked for duplicate records.

```text
Duplicate Rows : 63
```

The exact duplicate rows were removed.

### Final dataset

```text
1,809,140 records
```

---

## 6. Column Name Standardization

Original column names containing spaces and special characters were converted into SQL/Python-friendly names.

For example:

```text
Electric Range
       ↓
Electric_Range
```

```text
Model Year
       ↓
Model_Year
```

```text
New or Used Vehicle
       ↓
New_or_Used_Vehicle
```

This made the dataset easier to use with Python, SQLite, and SQL.

---

## 7. Data Validation

Important analytical fields were checked before loading the cleaned data into the database.

Validation included:

* Negative electric-range values
* Model-year validity
* Missing values
* Duplicate records
* Numerical distributions

### Electric Range Validation

```text
Negative Electric Range Values : 0
```

### Model Year Validation

```text
Unrealistic Model Year Values : 0
```

---

# 🗄️ SQLite Database

After the data preparation stage, the cleaned Pandas DataFrame was loaded into a SQLite database for analytical SQL queries.

> **Note:** The SQLite database is not included in this repository because of its large file size. It is generated locally from the cleaned dataset when the analysis notebook is executed.

### Main Table

```text
registrations

### Main Table

```text
registrations
```

The final cleaned dataset contained:

```text
1,809,140 records
```

SQLite was used as the database layer for analytical SQL queries.

---

# 🧮 SQL Analysis

The SQL analysis was performed inside:

```text
QUERIES/EV_Analysis.ipynb
```

The analysis was designed around practical EV market questions.

## 🔎 Analytical Questions

The SQL analysis answers business questions related to:

- Total EV registrations
- Top EV manufacturers
- EV adoption by model year
- BEV vs PHEV distribution
- Top counties and geographic concentration
- Average electric range by manufacturer
- New vs used EV distribution
- Top EV models
- Manufacturer growth
- Average range by vehicle technology
- Top-3 manufacturer market share

📌 Complete SQL/Python analysis:
`QUERIES/EV_Analysis.ipynb`

---

## 1. Total EV Registrations

### Question

How many cleaned EV registration records are available?

### Result

```text
1,809,140 registrations
```

This represents the final analytical population used in the project.

---

## 2. Top EV Manufacturers

### Question

Which manufacturers have the highest EV registration volume?

### Results

| Rank | Manufacturer | Registrations |
| ---: | ------------ | ------------: |
|    1 | Tesla        |       721,710 |
|    2 | Nissan       |       205,116 |
|    3 | Chevrolet    |       154,036 |
|    4 | Ford         |       102,216 |
|    5 | BMW          |        79,422 |

### Insight

**Tesla** has the highest registration volume in the analyzed dataset.

---

## 3. EV Adoption by Model Year

### Question

How has EV registration activity changed across model years?

The analysis focused on model years from **2018 to 2026**.

| Model Year | Registrations |
| ---------: | ------------: |
|       2018 |       150,430 |
|       2019 |       103,402 |
|       2020 |       102,219 |
|       2021 |       150,233 |
|       2022 |       183,942 |
|       2023 |       302,893 |
|       2024 |       195,253 |
|       2025 |       107,860 |
|       2026 |        64,277 |

### Highest registration activity

```text
2023 → 302,893 registrations
```

---

## 4. EV Technology Distribution

### Question

What is the distribution between BEVs, PHEVs, and other EV technologies?

| Vehicle Type                           | Registrations |
| -------------------------------------- | ------------: |
| Battery Electric Vehicle (BEV)         |     1,394,647 |
| Plug-in Hybrid Electric Vehicle (PHEV) |       414,448 |
| Hydrogen Powered Vehicle               |            45 |

### Insight

**BEVs represent the majority** of the analyzed EV registration population.

---

## 5. Top Counties

### Question

Which counties have the highest EV registration activity?

| Rank | County    | Registrations |
| ---: | --------- | ------------: |
|    1 | King      |       927,297 |
|    2 | Snohomish |       214,535 |
|    3 | Pierce    |       146,370 |
|    4 | Clark     |       106,186 |
|    5 | Kitsap    |        61,875 |

### Insight

**King County** has the highest registration activity in the analyzed data.

---

## 6. Average Electric Range by Manufacturer

Manufacturers were compared using average electric range with a minimum registration threshold to avoid very small groups dominating the comparison.

| Manufacturer | Average Range |
| ------------ | ------------: |
| Jaguar       |        205.09 |
| Tesla        |         90.18 |
| Chevrolet    |         86.95 |
| Fiat         |         82.50 |
| Nissan       |         80.51 |
| Smart        |         62.41 |
| Porsche      |         47.48 |
| Audi         |         46.56 |
| Kia          |         44.51 |
| Land Rover   |         42.04 |

### Insight

**Jaguar** has the highest average electric range in this filtered manufacturer comparison, while **Tesla** has the largest registration volume.

---

## 7. New vs Used EVs

### Question

What is the distribution between new and used EV registrations?

| Vehicle Status | Registrations |
| -------------- | ------------: |
| Used           |     1,510,017 |
| New            |       299,123 |

### Insight

Used EV registrations represent a substantially larger portion of the analyzed dataset.

---

## 8. Top EV Models

### Question

Which EV models have the highest registration volume?

| Rank | Model              | Registrations |
| ---: | ------------------ | ------------: |
|    1 | Model Y            |       297,368 |
|    2 | Model 3            |       268,871 |
|    3 | Leaf               |       195,252 |
|    4 | Model S            |        93,815 |
|    5 | Volt               |        68,570 |
|    6 | Model X            |        54,096 |
|    7 | Bolt EV            |        53,998 |
|    8 | Prius Prime (PHEV) |        29,633 |
|    9 | Mustang Mach-E     |        29,450 |
|   10 | ID.4               |        29,391 |

### Insight

**Model Y** is the highest-volume EV model in the analyzed dataset.

---

## 9. Manufacturer Growth

### Question

Which manufacturers changed the fastest between 2023 and 2024?

A SQL CTE was used to compare manufacturer registration activity between model years **2023 and 2024**.

The analysis calculated percentage growth using registration counts for both years.

This provides a view of **manufacturer momentum**, rather than simply ranking manufacturers by total registrations.

---

## 10. Average Electric Range by Vehicle Type

### Question

How does average electric range differ between EV technologies?

| Vehicle Type                           | Average Range |
| -------------------------------------- | ------------: |
| Battery Electric Vehicle (BEV)         |         72.84 |
| Plug-in Hybrid Electric Vehicle (PHEV) |         31.57 |
| Hydrogen Powered Vehicle               |          0.00 |

### Insight

BEVs have a substantially higher average recorded electric range than PHEVs in this dataset.

---

## 11. Top-3 Manufacturer Market Share

### Question

How concentrated is the EV market among the leading manufacturers?

| Manufacturer | Registrations | Market Share |
| ------------ | ------------: | -----------: |
| Tesla        |       721,710 |       39.89% |
| Nissan       |       205,116 |       11.34% |
| Chevrolet    |       154,036 |        8.51% |

### Combined Top-3 Market Share

```text
59.74%
```

### Insight

The top three manufacturers account for **59.74%** of the analyzed registration population, indicating significant market concentration.

---

# 📊 Power BI Dashboard

The cleaned data and analytical results were used to build a **three-page Power BI dashboard**.

The dashboard was designed as an analytical story:

```text
Page 1
What does the EV market look like?
        ↓
Page 2
Where is EV adoption concentrated?
        ↓
Page 3
How is the EV market and technology evolving?
```

---

# 📌 Page 1 — Executive Overview

The first page provides a high-level overview of the EV market.

### Main KPIs

* Total Registrations
* Top Manufacturer
* Top Manufacturer Share
* YoY Growth
* Average Electric Range

### Main Visuals

* EV Adoption Trend
* Vehicle Type Mix
* Top EV Manufacturers
* EV Models by Range
* New vs Used EV Distribution

### Purpose

This page provides a quick understanding of the overall EV market before moving into detailed geographic and technology analysis.

---

# 🗺️ Page 2 — Geographic Insights & Regional EV Adoption

The second page focuses on where EV registrations are concentrated.

### Main Visuals

* County-Level EV Adoption
* Top Counties by EV Registrations
* Average Electric Range by Manufacturer
* Electric Utility Distribution
* Top Cities by EV Registrations
* Top ZIP Codes by EV Registrations

### Questions Answered

* Which counties have the highest EV registrations?
* Which cities have the highest EV activity?
* Which ZIP codes show higher EV concentration?
* How does EV adoption vary geographically?
* Which electric utility areas have higher EV activity?

---

# 📈 Page 3 — EV Trend & Technology Insights

The third page focuses on EV technology and market evolution.

### Main Visuals

* BEV vs PHEV Adoption Over Time
* EV Market Leadership Over Time
* Monthly EV Registration Trend
* Fastest-Growing EV Models
* Primary Use Distribution

### Questions Answered

* How are BEVs and PHEVs changing over time?
* How has manufacturer leadership changed?
* Which EV models show growth?
* What are the major vehicle-use categories?
* How has EV activity changed over time?

---

# 🎛️ Interactive Dashboard Features

The Power BI report includes synchronized slicers for:

* **Model Year**
* **Vehicle Type**
* **County**

The slicers are synchronized across the three dashboard pages so users can maintain the same filtering context while moving through the report.

---

# 💡 Key Insights

### 1. Tesla Leads the Market

Tesla recorded:

```text
721,710 registrations
```

making it the leading manufacturer in the analyzed dataset.

### 2. Significant Market Concentration

The top three manufacturers account for:

```text
59.74%
```

of the analyzed registration population.

### 3. BEVs Dominate

BEVs account for:

```text
1,394,647 registrations
```

compared with:

```text
414,448 PHEV registrations
```

### 4. King County Leads

King County recorded:

```text
927,297 registrations
```

making it the largest county in the analyzed dataset.

### 5. Used EVs Represent the Larger Segment

```text
Used : 1,510,017
New  :   299,123
```

### 6. Model Y is the Leading Model

```text
Model Y : 297,368
Model 3 : 268,871
```

### 7. BEVs Have Higher Average Range

```text
BEV  : 72.84
PHEV : 31.57
```

### 8. 2023 Shows the Highest Registration Activity

Among the analyzed model years from 2018 to 2026:

```text
2023 → 302,893 registrations
```

was the highest.

---

# 🛠️ Technologies Used

* Python 3
* Pandas
* NumPy
* Matplotlib
* Seaborn
* SQLite
* SQL
* Jupyter Notebook
* Power BI
* Power Query
* GitHub

---

# 📚 Skills Demonstrated

## Python

* Data loading
* Data cleaning
* Data transformation
* Missing-value handling
* Text standardization
* Duplicate removal
* Data validation
* Pandas
* SQLite integration

## SQL

* `SELECT`
* `WHERE`
* `GROUP BY`
* `ORDER BY`
* `COUNT`
* `AVG`
* `ROUND`
* `CASE`
* `HAVING`
* CTEs
* Ranking
* Percentage calculations
* Growth analysis
* Market-share analysis

## Power BI

* Dashboard development
* KPI cards
* Trend analysis
* Market analysis
* Geographic analysis
* Bar charts
* Column charts
* Line charts
* Area charts
* Ribbon charts
* Donut charts
* Maps
* Slicers
* Slicer synchronization
* Interactive filtering
* Data storytelling

---

# 🏗️ Project Architecture

```text
Washington State Open Data
          ↓
        Python
          ↓
Data Cleaning & Preparation
          ↓
      Cleaned Dataset
          ↓
     SQLite Database
          ↓
       SQL Analysis
          ↓
    Analytical Results
          ↓
       Power BI
          ↓
    3-Page Dashboard
          ↓
       EV Insights
```

---

# 🚀 How to Run

## 1. Clone the Repository

```bash
git clone https://github.com/Shrey2503/EV-Market-Analytics.git
cd EV-Market-Analytics
```

## 2. Install Dependencies

```bash
pip install pandas numpy matplotlib seaborn jupyter
```

## 3. Open the Notebook

Navigate to:

```text
QUERIES/EV_Analysis.ipynb
```

## 4. Launch Jupyter Notebook

```bash
jupyter notebook
```

## 5. Run the Notebook

Run the notebook cells sequentially to:

1. Load the dataset
2. Inspect the data
3. Analyze missing values
4. Clean the data
5. Standardize fields
6. Remove duplicates
7. Validate important fields
8. Create the SQLite database
9. Run SQL analysis

## 6. Open the Power BI Dashboard

Open the `.pbix` file from:

```text
POWER BI/
```

Then explore all three dashboard pages and use the synchronized slicers.

---

# 🎓 Learning Outcomes

This project demonstrates practical experience in:

* Working with real-world public datasets
* Python-based data preparation
* Pandas data manipulation
* Data cleaning
* Missing-value handling
* Duplicate detection
* Data validation
* SQLite database management
* SQL analytical querying
* Market analysis
* Geographic analysis
* EV technology analysis
* Trend analysis
* Power BI dashboard development
* Interactive reporting
* Business insight generation
* Data storytelling

---

# 🔮 Future Improvements

Potential extensions include:

* EV charging-station analysis
* EV-to-charging-station ratio
* Charging infrastructure gap analysis
* EV adoption forecasting
* Advanced DAX measures
* Power BI drill-through pages
* Power BI tooltip pages
* Power BI Service deployment
* Automated data refresh
* Integration with population data
* Integration with charging infrastructure data
* Regional EV adoption forecasting

---

# 👨‍💻 Author

**Shreyash Vats**

B.Tech CSE | Aspiring Data Analyst

### Skills

`Python` `SQL` `Pandas` `SQLite` `Power BI` `Data Analytics` `Data Visualization`

### Profiles

[GitHub](https://github.com/Shrey2503) · [LinkedIn](https://www.linkedin.com/in/shreyash-vats-1a22232a4/)

---

## 📌 Project Focus

**Electric Vehicle Market Analytics**

Python • SQL • SQLite • Power BI • Data Analytics • Business Intelligence • Data Visualization
