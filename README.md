# Alt_mobility


## 📁 Project Overview

This project focuses on analyzing customer orders and payments using SQL to uncover insights related to:

- **Order and Sales Analysis**
- **Customer Analysis**
- **Payment Status Analysis**
- **Order Details Report:**

The datasets used include:
- `cleaned_customer_orders.csv` – contains order details such as status, amount, and date.
- `cleaned_payments.csv` – contains payment transactions with their method and status.

---

## 🧠 Objectives

### ✅ **Sales and Order Analysis**
- Calculate the percentage of orders that are successfully delivered.
- Identify mismatches between delivered orders and completed payments.
- Track monthly revenue and detect sales spikes or drops.
- Understand how payment failures are associated with order statuses.

### ✅ **Customer Analysis**
- Segment customers into repeat vs one-time purchasers.
- Analyze ordering frequency and total spend per customer.
- Track customer activity over time to identify retention patterns.
- Use ordering patterns to segment high-value customers.

### ✅ **Payment Analysis**
- Calculate proportions of completed, pending, and failed payments.
- Analyze failure rates across payment methods (e.g., credit card, wallet).
- Track monthly trends in payment failures.
- Identify correlation between order status and payment success/failure.

---

## 🧾 SQL Approach

Each analysis point was handled through clear, efficient SQL queries:

| Analysis Type | SQL Queries Used |
|---------------| ------------------|
| Order Status   |  `GROUP BY order_status` |
| Monthly Revenue | `DATE_FORMAT(order_date)` with `SUM(order_amount)` |
| Payment Status | `GROUP BY payment_status`, `JOIN` with orders |
| Customer Segmentation | `GROUP BY customer_id`, `SUM(order_amount)` |
| Retention Trends | `DATEDIFF(MAX(order_date), MIN(order_date))` |
| Payment Issues | `JOIN payments ON order_id` and `CASE WHEN payment_status = 'fail'` |

---

## 🧼 Data Handling

- CSV files were cleaned before import to MySQL Workbench.
- Data types were verified: dates (`order_date`, `payment_date`) were formatted, numeric fields (`order_amount`, `payment_amount`) checked for consistency.
- Primary key relationships between `order_id` fields in both tables were preserved.

---

## 📈 Tools & Tech

- **SQL_Notebook** – for SQL querying and data joining
- **Python (optional for viz)** – for cleaning 
- **CSV Files** – data source

## 📌 Key Insights

- A large portion of delivered orders still had pending or failed payments, signaling operational issues.
- Certain months showed strong sales spikes, suggesting seasonal demand.
- Digital wallet methods had a higher failure rate than others.
- Most customers are one-time buyers, though a small group contributes disproportionately to revenue.

