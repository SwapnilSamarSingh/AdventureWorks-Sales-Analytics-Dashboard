# Business Logic & DAX

## Overview

This project uses DAX (Data Analysis Expressions) to create calculated columns and measures that support business reporting, time intelligence, customer segmentation, and sales analysis.

---

# Calculated Columns

## Week Start

**Purpose**

Creates the first day of the week (Monday) for each date, enabling weekly trend analysis.

```DAX
Week_Start =
'Calendar'[Date] - WEEKDAY('Calendar'[Date], 2) + 1
```

---

## Previous Quarter (Quarters_IND)

**Purpose**

Creates a custom quarter index where Q1 maps to 4 and all other quarters shift back by one. This supports comparisons with the previous quarter.

```DAX
Quarters_IND =
IF(
    QUARTER('Calendar'[Date]) = 1,
    4,
    QUARTER('Calendar'[Date]) - 1
)
```

---

## Age Group

**Purpose**

Groups customers into age ranges using Power BI's Data Group feature, making demographic analysis easier.

**Example Groups**

- 20–29
- 30–39
- 40–49
- 50+

---

## Income Category

**Purpose**

Categorizes customers into income segments for customer analysis.

```DAX
Income_Category =
IF(
    Customers[AnnualIncome] < 30000,
    "Low",
    IF(
        Customers[AnnualIncome] > 80000,
        "High",
        "Average"
    )
)
```

---

## Weekend / Weekday

**Purpose**

Identifies whether an order was placed on a weekday or weekend.

```DAX
Weekend/Weekday =
IF(
    OR(
        WEEKDAY(Sales[OrderDate]) = 1,
        WEEKDAY(Sales[OrderDate]) = 7
    ),
    "Weekend",
    "Weekday"
)
```

---

# Measures

## Revenue

**Purpose**

Calculates total sales revenue.

```DAX
Revenue =
SUMX(
    Sales,
    Sales[OrderQuantity] *
    RELATED(Products[ProductPrice])
)
```

**Functions Used**

- `SUMX()`
- `RELATED()`

---

## Average Retail Price

**Purpose**

Calculates the average retail price across all products.

```DAX
Average_RetailPrice =
AVERAGE(Products[ProductPrice])
```

---

## Total Return Amount

**Purpose**

Calculates the monetary value of returned products.

```DAX
Total_Return_Amount =
SUMX(
    Returns,
    Returns[ReturnQuantity] *
    RELATED(Products[ProductPrice])
)
```

**Functions Used**

- `SUMX()`
- `RELATED()`

---

## High Ticket Orders

**Purpose**

Counts orders where the product price is greater than the average product price.

```DAX
High_Ticket =
CALCULATE(
    [Total_Orders],
    Products[ProductPrice] >
    AVERAGE(Products[ProductPrice])
)
```

**Functions Used**

- `CALCULATE()`
- `AVERAGE()`

---

## Previous Month Orders

**Purpose**

Returns the total number of orders from the previous month for month-over-month comparison.

```DAX
Prev_Month_Orders =
CALCULATE(
    [Total_Orders],
    DATEADD(
        'Calendar'[Date],
        -1,
        MONTH
    )
)
```

**Functions Used**

- `CALCULATE()`
- `DATEADD()`

---

## Previous Month Revenue

**Purpose**

Calculates revenue generated during the previous month.

```DAX
Prev_Month_Revenue =
CALCULATE(
    [Revenue],
    DATEADD(
        'Calendar'[Date],
        -1,
        MONTH
    )
)
```

**Functions Used**

- `CALCULATE()`
- `DATEADD()`

---

# DAX Concepts Demonstrated

This project demonstrates the practical use of several DAX concepts:

- Row Context
- Filter Context
- Time Intelligence
- Iterator Functions (`SUMX`)
- Context Transition (`CALCULATE`)
- Relationship Navigation (`RELATED`)
- Conditional Logic (`IF`)
- Date Functions (`DATEADD`, `WEEKDAY`, `QUARTER`)
- Statistical Functions (`AVERAGE`)

---

# Business Value

These calculations enable stakeholders to:

- Monitor sales performance.
- Compare monthly trends.
- Analyze customer demographics.
- Evaluate product pricing.
- Measure the financial impact of returns.
- Identify high-value orders.
- Perform weekly and quarterly analysis.
