# Global Electronics Sales Analytics Dashboard

An end-to-end analytics project built around a **single EDA/ETL notebook workflow**.  
The notebook performs data cleaning, merging, feature engineering (Revenue/Cost/Profit), exports a final master dataset as CSV, and (optionally) loads the data into **MySQL** and creates **SQL Views** for Power BI reporting.

---

## What This Project Does

### 1) Data Preparation (ETL inside notebook)

The notebook:

* Loads all CSVs from `dataset/`
* Cleans & standardizes fields (dates, numeric columns, missing values)
* Merges Sales + Customers + Products + Stores + Exchange Rates
* Engineers business metrics:

  * `Revenue`, `Cost`, `Profit`
* Exports final dataset:

  * `output/Global_Electronics_Master.csv`

### 2) Exploratory Data Analysis (EDA)

The notebook includes EDA such as:

* Customer age & gender distribution
* Revenue trends over time
* Product and store performance analysis
* Category-wise profitability insights

### 3) Database + SQL Views (for Power BI)

If you run the database section inside the notebook, it:

* Connects to MySQL
* Creates the `global_electronics` database (if missing)
* Creates the `Global_Electronics_Master` table dynamically
* Inserts the CSV data into the table
* Creates SQL **Views** for KPI reporting (used in Power BI)

---

## Input Datasets

All raw datasets are in the `/dataset` folder:

| File                  | Description                  |
| --------------------- | ---------------------------- |
| `Customers.csv`       | Customer demographic details |
| `Products.csv`        | Product catalog              |
| `Sales.csv`           | Sales transactions           |
| `Stores.csv`          | Store metadata               |
| `Exchange_Rates.csv`  | Currency exchange rates      |
| `Data_Dictionary.csv` | Dataset column definitions   |

---

## Outputs

### Primary Output

* `output/Global_Electronics_Master.csv`
  Final merged dataset used for analysis and BI.

### Outputs To Insert In PowerBI Dashboard (if DB section is executed)

* MySQL table: `Global_Electronics_Master`
* MySQL views (examples):

  * Total Revenue & Profit
  * Monthly Revenue Trend
  * Top Products / Customers / Stores
  * Profit by Category
  * Revenue by Currency
  * Average Order Value

---

## Power BI Dashboard (`DataSpark.pbix`)

### What’s inside

* Multiple pages for Sales, Customers, Products, Stores
* KPI cards, trend charts, geography insights, profitability breakdowns
* Uses the final dataset (via CSV or via MySQL Views)

### How to use

1. Open `DataSpark.pbix` in **Power BI Desktop**
2. Load data using one of these methods:

   * **Recommended:** Import `output/Global_Electronics_Master.csv`
   * **Optional:** Connect to MySQL and use the created SQL Views
3. Refresh and explore the report pages

> Note: A `.pbix` file cannot be “deployed” directly in Streamlit Cloud. You either publish it to Power BI Service and embed it, or rebuild visuals in Streamlit.

---

## How to Run (Notebook Workflow)

### 1) Install requirements

```bash
pip install pandas numpy matplotlib seaborn plotly mysql-connector-python
```

### 2) Run ETL + EDA Notebook

Open and run:

* `EDA_Analysis.ipynb` (recommended)

This generates:

* `output/Global_Electronics_Master.csv`

### 3) (Optional) Run MySQL + Views section

Inside the notebook/script, update:

* `host`, `user`, `password`, `database_name`

Then execute the database + view creation cells.

---

## Tech Stack

| Layer               | Tools                       |
| ------------------- | --------------------------- |
| Language            | Python                      |
| Notebook            | Jupyter                     |
| Data                | pandas, numpy               |
| EDA/Viz             | matplotlib, seaborn, plotly |
| Database (optional) | MySQL                       |
| BI                  | Power BI Desktop            |

---

## Author

* Abhishek Chakraborty
* Email: [abbhicse@gmail.com](mailto:abbhicse@gmail.com)
