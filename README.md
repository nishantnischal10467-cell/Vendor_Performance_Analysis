# 📦 Vendor Performance Analysis

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white"/>
  <img src="https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black"/>
  <img src="https://img.shields.io/badge/SQLite-003B57?style=for-the-badge&logo=sqlite&logoColor=white"/>
  <img src="https://img.shields.io/badge/Jupyter-F37626?style=for-the-badge&logo=jupyter&logoColor=white"/>
  <img src="https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white"/>
  <img src="https://img.shields.io/badge/License-MIT-green?style=for-the-badge"/>
</p>

> A comprehensive **end-to-end data analytics pipeline** for evaluating vendor performance in procurement workflows — combining Python-based EDA, SQLite data warehousing, and interactive Power BI dashboards to deliver actionable procurement intelligence.

---

## 📌 Table of Contents

- [Overview](#-overview)
- [Key Objectives](#-key-objectives)
- [Technologies Used](#️-technologies-used)
- [Dataset](#-dataset)
- [Project Architecture](#️-project-architecture)
- [Project Structure](#-project-structure)
- [Key Metrics & KPIs](#-key-metrics--kpis)
- [Insights & Features](#-insights--features)
- [Usage in Industry](#-usage-in-industry)
- [Getting Started](#-getting-started)
- [Results & Outputs](#-results--outputs)
- [Contributing](#-contributing)

---

## 🔍 Overview

This project builds a **data-driven vendor evaluation framework** that processes raw procurement data across purchases, sales, and inventory to surface insights about vendor efficiency, cost contribution, and supply reliability. The pipeline ingests multi-source CSV data into a structured SQLite database, performs exploratory data analysis, and visualizes strategic KPIs in a Power BI dashboard — enabling procurement managers and supply chain analysts to make smarter sourcing decisions.

---

## 🎯 Key Objectives

- Identify **top-performing and underperforming vendors** based on volume, cost, and consistency
- Analyze **purchase contribution** and order frequency per vendor
- Track **inventory turnover** and detect stocking inefficiencies
- Measure **cost efficiency** by comparing purchase prices vs. sales revenue
- Deliver **interactive dashboards** for real-time procurement reporting
- Generate automated **vendor summary reports** via Python scripts

---

## 🛠️ Technologies Used

| Technology | Purpose |
|---|---|
| **Python 3.10+** | Data ingestion, cleaning, EDA, statistical analysis, vendor summary generation |
| **Pandas / NumPy** | Data manipulation and transformation |
| **Matplotlib / Seaborn** | Exploratory data visualizations inside Jupyter |
| **SQLite** | Lightweight relational database for structured data storage |
| **Jupyter Notebook** | Interactive analysis and reproducible reporting |
| **Power BI (.pbix)** | Interactive dashboards and business intelligence reporting |
| **Microsoft Excel** | Data preprocessing and spot-check analysis |
| **Figma** | Dashboard wireframing and UI prototyping |
| **Git / GitHub** | Version control and project collaboration |

---

## 📂 Dataset

The full dataset is sourced from **Kaggle** (hosted externally due to GitHub file size limits).

🔗 **Kaggle Dataset:** [Vendor Performance Analysis — harshmadhavan](https://www.kaggle.com/datasets/harshmadhavan/vendor-performance-analysis)

### Download via Kaggle CLI

```bash
pip install kaggle
# Place kaggle.json in ~/.kaggle/ (Linux/Mac) or C:\Users\<you>\.kaggle\ (Windows)
kaggle datasets download -d harshmadhavan/vendor-performance-analysis -p data/ --unzip
```

### Files Included

| File | Description |
|---|---|
| `purchases.csv` | All vendor purchase transactions with dates, quantities, and amounts |
| `sales.csv` | Sales records linked to purchased inventory |
| `begin_inventory.csv` | Opening inventory snapshot per item/vendor |
| `end_inventory.csv` | Closing inventory snapshot per item/vendor |
| `purchase_prices.csv` | Vendor-wise unit purchase prices per SKU |
| `vendor_invoice.csv` | Invoice-level data for payment and vendor reconciliation |
| `vendor_sales_summary.csv` | Aggregated vendor-level sales and contribution metrics |

> 📁 After downloading, place all CSV files inside a `/data` directory in the project root (already `.gitignored`).

---

## 🏗️ Project Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                        DATA SOURCES                         │
│   purchases.csv │ sales.csv │ inventory CSVs │ invoices     │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│                   INGESTION LAYER (Python)                  │
│              scripts/ingestion_db.py                        │
│     • Reads CSVs  • Cleans & validates  • Loads to SQLite   │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│                  DATA WAREHOUSE (SQLite)                    │
│                     inventory.db                            │
│   Tables: purchases | sales | inventory | vendor_invoices   │
└──────────────┬──────────────────────────┬───────────────────┘
               │                          │
               ▼                          ▼
┌──────────────────────┐    ┌─────────────────────────────────┐
│  ANALYSIS LAYER      │    │     REPORTING LAYER             │
│  (Jupyter Notebooks) │    │   (Power BI Dashboard)          │
│  • EDA.ipynb         │    │   vendor_Performance_Dashboard  │
│  • Vendor Analysis   │    │   • Vendor KPIs                 │
│  • Statistical tests │    │   • Trend visualizations        │
│  • Visualizations    │    │   • Procurement insights        │
└──────────────────────┘    └─────────────────────────────────┘
               │
               ▼
┌─────────────────────────────────────────────────────────────┐
│                  SUMMARY EXPORT (Python)                    │
│              scripts/get_vendor_summary.py                  │
│         Automated vendor performance summary reports        │
└─────────────────────────────────────────────────────────────┘
```

---

## 📁 Project Structure

```
Vendor_Performance_Analysis/
│
├── data/                              # ⚠️ Gitignored — download from Kaggle
│   ├── purchases.csv
│   ├── sales.csv
│   ├── begin_inventory.csv
│   ├── end_inventory.csv
│   ├── purchase_prices.csv
│   ├── vendor_invoice.csv
│   └── vendor_sales_summary.csv
│
├── scripts/                           # Python utility scripts
│   ├── ingestion_db.py                # Data ingestion pipeline → SQLite
│   └── get_vendor_summary.py          # Vendor performance summary generator
│
├── logs/                              # Pipeline execution logs
│
├── desktop-workspaces/                # Power BI workspace configs
│
├── __pycache__/                       # Python bytecode cache
│
├── EDA.ipynb                          # Main Exploratory Data Analysis notebook
├── Vendor Performance Analysis.ipynb  # Core vendor analysis notebook
├── Untitled.ipynb                     # Supplementary analysis notebook
│
├── vendor_Performance_Dashboard.pbix  # Power BI interactive dashboard
├── inventory.db                       # SQLite database (generated after ingestion)
│
├── .gitignore
├── .gitattributes
└── README.md
```

---

## 📊 Key Metrics & KPIs

The analysis evaluates vendors across the following dimensions:

| KPI | Description |
|---|---|
| **Purchase Contribution (%)** | Share of total procurement spend attributed to each vendor |
| **Order Frequency** | Number of purchase orders placed per vendor over the analysis period |
| **Cost per Unit** | Average purchase price per SKU across vendors |
| **Inventory Turnover Rate** | How efficiently vendor-supplied stock is sold through |
| **Sales-to-Purchase Ratio** | Revenue generated relative to procurement cost (margin proxy) |
| **Invoice Settlement Rate** | Proportion of invoices cleared on time vs. overdue |
| **Stock Contribution** | Beginning vs. ending inventory delta per vendor |

---

## 💡 Insights & Features

- **Vendor Ranking** — Rank vendors by spend, sales contribution, and profitability
- **Pareto Analysis** — Identify the 20% of vendors driving 80% of procurement value
- **Inventory Health** — Detect overstocked or understocked SKUs linked to specific vendors
- **Cost Efficiency Benchmarking** — Compare vendor pricing against category averages
- **Trend Analysis** — Time-series view of purchasing patterns and seasonal demand
- **Interactive Power BI Dashboards** — Filter by vendor, category, time period, and KPI
- **Automated Summary Generation** — Python script outputs tabular vendor scorecards

---

## 🏭 Usage in Industry

This type of vendor performance analysis is widely adopted across industries for strategic procurement management:

| Industry | Use Case |
|---|---|
| **Retail & E-Commerce** | Evaluate supplier reliability, pricing, and stock contribution for inventory planning |
| **Manufacturing** | Assess raw material vendors on cost efficiency, delivery frequency, and quality consistency |
| **Healthcare / Pharma** | Monitor medical supply vendors for compliance, price fluctuations, and order fulfillment |
| **FMCG / CPG** | Track vendor margins, inventory turnover, and sales performance across product categories |
| **Logistics & Distribution** | Identify vendor bottlenecks affecting supply chain flow and distribution costs |
| **Government & Public Sector** | Audit procurement spend, detect vendor concentration risk, and enforce compliance |
| **Financial Services** | Operational procurement analytics to optimize vendor contracts and reduce indirect spend |

> **Business Value:** Organizations using data-driven vendor evaluation typically achieve **10–20% reduction in procurement costs** and significantly improved supplier relationship management.

---

## 🚀 Getting Started

### Prerequisites

```bash
Python 3.10+
pip
Power BI Desktop (for .pbix dashboard)
Kaggle account (for dataset download)
```

### Installation

```bash
# 1. Clone the repository
git clone https://github.com/nishantnischal10467-cell/Vendor_Performance_Analysis.git
cd Vendor_Performance_Analysis

# 2. Install Python dependencies
pip install pandas numpy matplotlib seaborn jupyter sqlite3

# 3. Download dataset from Kaggle
pip install kaggle
kaggle datasets download -d harshmadhavan/vendor-performance-analysis -p data/ --unzip

# 4. Run the ingestion pipeline to load data into SQLite
python scripts/ingestion_db.py

# 5. Launch Jupyter for analysis
jupyter notebook EDA.ipynb
```

### Power BI Dashboard

1. Open **Power BI Desktop**
2. Load `vendor_Performance_Dashboard.pbix`
3. Update the data source path to your local `/data` folder
4. Refresh the dataset and explore the interactive visuals

---

## 📈 Results & Outputs

After running the full pipeline, you will have:

- ✅ A cleaned, queryable **SQLite database** (`inventory.db`) with normalized procurement tables
- ✅ Jupyter notebooks with **EDA plots**, statistical summaries, and vendor rankings
- ✅ An **interactive Power BI dashboard** with filterable KPIs and trend visualizations
- ✅ Exported **vendor performance summaries** from the Python reporting script

---

## 🤝 Contributing

Contributions are welcome! To contribute:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/your-feature`)
3. Commit your changes (`git commit -m 'Add: your feature description'`)
4. Push to the branch (`git push origin feature/your-feature`)
5. Open a Pull Request

---

## 👤 Author

**Nishant Nischal**
- GitHub: [@nishantnischal10467-cell](https://github.com/nishantnischal10467-cell)

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

---

<p align="center">
  <i>If you found this project useful, please ⭐ star the repository!</i>
</p>
