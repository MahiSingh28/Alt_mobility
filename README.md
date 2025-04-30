
## 📁 Project Overview

This project analyzes customer orders and payments using **SQL** to discover insights related to:

- Order and sales performance  
- Customer behavior  
- Payment success and failures  

We used the following datasets:

- `cleaned_customer_orders.csv` – order status, amount, and dates  
- `cleaned_payments.csv` – payment methods and statuses  

---

## 🧠 Objectives

### ✅ Sales & Order Analysis
- Measure the percentage of orders that were delivered  
- Find gaps between delivered orders and completed payments  
- Track monthly revenue and detect sales trends  
- Link payment failures to order status  

### ✅ Customer Analysis
- Classify customers into one-time vs repeat  
- Analyze total spend and order frequency per customer  
- Track customer activity and retention  
- Identify high-value customers  

### ✅ Payment Analysis
- Calculate rates of completed, pending, and failed payments  
- Compare failure rates by payment method  
- Spot monthly patterns in payment issues  
- Link failed payments to order outcomes  

---

## 🧾 SQL Approach

We used straightforward SQL queries for each analysis:

| **Goal**                 | **SQL Strategy**                                   |
|--------------------------|----------------------------------------------------|
| Order Status             | `GROUP BY order_status`                            |
| Monthly Revenue          | `DATE_FORMAT(order_date, '%Y-%m')` + `SUM()`       |
| Payment Status           | `JOIN` orders & payments + `GROUP BY payment_status` |
| Customer Segmentation    | `GROUP BY customer_id` + `SUM(order_amount)`       |
| Retention Trends         | `DATEDIFF(MAX, MIN(order_date))`                  |
| Payment Issues           | `JOIN` + `CASE WHEN payment_status = 'fail'`       |

---

## 🧼 Data Handling

- Cleaned CSVs before importing into MySQL Workbench  
- Verified data types: dates, amounts, status fields  
- Ensured relationships using `order_id` as the primary link  

---

## 📈 Tools & Tech

- **SQL_Notebook** – for writing and running SQL queries  
- **Python (optional)** – used for data cleaning  
- **MySQL Workbench** – database environment  
- **CSV Files** – data source  

---

## 📌 Key Insights

- Many delivered orders had **pending or failed payments** → operational gap  
- Certain months saw **revenue spikes** → seasonal trends  
- **Digital wallets** had higher payment failure rates  
- Most customers are **one-time buyers**, but a few **high-value customers** drive revenue  

