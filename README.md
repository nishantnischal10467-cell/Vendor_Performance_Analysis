# Vendor Performance Analysis

This project focuses on **evaluating vendor performance** through **data-driven insights**. It involves **cleaning and analyzing procurement datasets**, identifying **top-performing vendors**, and visualizing key metrics such as **purchase contribution, order frequency, cost efficiency, and inventory trends**. The insights generated support **strategic procurement decisions and business intelligence initiatives**.

---

## 🛠 Technologies Used

* **Python**: Data cleaning, EDA, predictive modeling
* **SQLite**: Database management
* **Power BI**: Interactive dashboards and visualizations
* **Excel**: Data preprocessing and analysis
* **Figma**: Dashboard prototyping
* **Git/GitHub**: Version control

---

## 📊 Features

* Conduct **Exploratory Data Analysis (EDA)** on vendor, purchase, and sales datasets
* Identify **key risk indicators**, such as missed payments and high credit utilization
* Develop **interactive dashboards** for vendor performance, sales trends, and inventory levels
* Generate **actionable insights** for procurement optimization and cost reduction
* Enable **real-time reporting** via Power BI Service

---

## 📂 Dataset

The full dataset is hosted on Kaggle due to GitHub size limits.

* **Kaggle Dataset:** [Vendor Performance Data](https://www.kaggle.com/datasets/harshmadhavan/vendor-performance-analysis)

### Download via Kaggle CLI

```bash
pip install kaggle
# Place kaggle.json in C:\Users\<you>\.kaggle\ (Windows)
kaggle datasets download -d harshmadhavan/vendor-performance-analysis -p data/ --unzip
```

**Files included:**

* purchases.csv
* sales.csv
* begin_inventory.csv
* end_inventory.csv
* purchase_prices.csv
* vendor_invoice.csv
* vendor_sales_summary.csv

---

## 📁 Project Structure

```
Vendor-Performance-Analysis/
│
├── data/                  # Folder for datasets (gitignored)
├── logs/                  # Log files
├── scripts/               # Python scripts
│   ├── get_vendor_summary.py
│   └── ingestion_db.py
├── .gitignore             # Ignored files
├── EDA.ipynb              # Exploratory Data Analysis notebook
├── Untitled.ipynb         # Additional notebook
├── vendor_Performance.pbix # Power BI dashboard
├── inventory.db           # SQLite database
└── README.md              # Project documentation
```

---

## ⚡ Usage

1. Download the dataset from Kaggle (see Dataset section).
2. Use scripts/ for Python-based analysis or open **vendor\_Performance.pbix** in Power BI.
3. Explore interactive dashboards to gain actionable insights on vendor performance.
