# Project Structure

This document describes the organization of the repository and the purpose of each directory.

---

# Repository Layout

```text
AdventureWorks-Sales-Analytics-Dashboard/
│
├── Dashboard/
│   └── Adven_project.pbix
│
├── Dataset/
│   ├── Customers.csv
│   ├── Products.csv
│   ├── Sales.csv
│   ├── Returns.csv
│   ├── Calendar.csv
│   ├── Categories.csv
│   ├── Subcategories.csv
│   └── Territories.csv
│
├── Documentation/
│   ├── Business-Logic-and-DAX.md
│   ├── Data-Model.md
│   └── Project-Structure.md
│
├── Images/
│   ├── adventure-works-banner.png
│   ├── homepage.png
│   ├── executive-summary.png
│   ├── category-analysis.png
│   ├── product-analysis.png
│   ├── customer-analysis.png
│   ├── dynamic-x-axis.png
│   ├── dynamic-y-axis.png
│   ├── dynamic-visual.png
│   └── data-model.png
│
├── LICENSE
└── README.md
```

---

# Directory Description

## Dashboard

Contains the Power BI report (`.pbix`) with the complete data model, DAX calculations, report pages, and interactive visualizations.

---

## Dataset

Stores the source datasets used in the report. These files provide the data for products, customers, sales transactions, returns, calendar, territories, and product hierarchy.

---

## Documentation

Contains technical documentation that complements the project:

- **Business-Logic-and-DAX.md** – Business rules, calculated columns, measures, and DAX logic.
- **Data-Model.md** – Star schema design, relationships, and data model explanation.
- **Project-Structure.md** – Repository organization and file descriptions.

---

## Images

Contains screenshots and visual assets used throughout the documentation, including the dashboard pages, data model diagram, and project banner.

---

# Repository Organization

The repository separates source data, report files, documentation, and visual assets into dedicated folders. This structure improves maintainability, simplifies navigation, and makes it easier to update individual components without affecting the rest of the project.
