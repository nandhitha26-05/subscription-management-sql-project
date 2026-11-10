Subscription Management System

📌 Project Overview

The Subscription Management System is a MySQL-based database project designed to manage customers, subscription plans, payments, usage details, and discounts.

The project demonstrates how SQL can be used to store, manage, retrieve, and analyze subscription-related business data.

🎯 Problem Statement

Subscription-based businesses need to efficiently manage customer subscriptions, plans, payments, discounts, and usage information.

This project provides a relational database structure that helps answer questions such as:

- Which customers are subscribed to which plans?
- Which subscriptions are active or expired?
- How much revenue is generated?
- Which plans are most popular?
- Which customers have the highest spending?
- What is the monthly revenue?
- What is the subscription churn status?

🛠️ Technologies Used

- MySQL
- MySQL Workbench
- SQL

🗂️ Database Tables

The database contains the following tables:

Table| Purpose
"Customers"| Stores customer information
"Plans"| Stores subscription plan details
"Subscriptions"| Stores customer subscription information
"Payments"| Stores payment transactions
"Usage_Details"| Stores subscription usage information
"Discounts"| Stores discount information for plans

🔗 Database Relationships

Customers
    │
    │ customer_id
    ▼
Subscriptions
    │
    ├──────────► Plans
    │
    ├──────────► Payments
    │
    └──────────► Usage_Details

Plans
    │
    └──────────► Discounts

📊 Database Operations

1. Basic Queries

The project includes queries for:

- Finding plans with price greater than ₹500
- Displaying active subscriptions
- Finding customers registered after 2024
- Finding subscriptions ending in the current month

Example:

SELECT *
FROM Plans
WHERE price > 500;

2. Joins

Multiple tables are combined using SQL joins to generate meaningful business information.

Examples include:

- Customer names with subscription plans
- Subscription details with payment information
- Plans with discount details
- Usage details with customer names
- Customer payment history

Example:

SELECT c.name, p.plan_name
FROM Customers c
JOIN Subscriptions s
ON c.customer_id = s.customer_id
JOIN Plans p
ON s.plan_id = p.plan_id;

3. Subqueries

The project uses subqueries for analytical questions such as:

- Finding customers without subscriptions
- Finding expired subscriptions
- Finding plans priced above the average
- Finding subscriptions with the highest usage

Example:

SELECT *
FROM Plans
WHERE price > (
    SELECT AVG(price)
    FROM Plans
);

4. Views

Reusable SQL views were created for:

- Customer subscriptions
- Payment history
- Active subscriptions
- Plan discounts
- Customer spending

Example:

CREATE VIEW Customer_Subscriptions AS
SELECT c.name, p.plan_name, s.status
FROM Customers c
JOIN Subscriptions s
ON c.customer_id = s.customer_id
JOIN Plans p
ON s.plan_id = p.plan_id;

5. Stored Procedures

The project also includes stored procedures for:

- Inserting a new customer
- Creating a subscription
- Getting customer subscriptions
- Calculating total revenue
- Filtering plans by price range

Example:

CALL TotalRevenue();

📈 Business Reports & Analysis

The project generates reports such as:

Top 5 Most Popular Plans

SELECT plan_id,
       COUNT(*) AS total
FROM Subscriptions
GROUP BY plan_id
ORDER BY total DESC
LIMIT 5;

Customers With Highest Spending

SELECT s.customer_id,
       SUM(p.amount) AS total_spent
FROM Payments p
JOIN Subscriptions s
ON p.subscription_id = s.subscription_id
GROUP BY s.customer_id
ORDER BY total_spent DESC
LIMIT 5;

Monthly Revenue

SELECT DATE_FORMAT(payment_date, '%Y-%m') AS month,
       SUM(amount) AS revenue
FROM Payments
GROUP BY month
ORDER BY month;

Subscription Churn Analysis

SELECT status,
       COUNT(*) AS total
FROM Subscriptions
GROUP BY status;

🔍 Key SQL Concepts Demonstrated

- "CREATE TABLE"
- Primary Keys
- Foreign Keys
- "INSERT"
- "SELECT"
- "WHERE"
- "UPDATE"
- "DELETE"
- "JOIN"
- "GROUP BY"
- "ORDER BY"
- Aggregate Functions
- Subqueries
- Views
- Stored Procedures
- "COUNT()"
- "SUM()"
- "AVG()"
- "MAX()"
- Date Functions
- Data Analysis

📂 Project Structure

Subscription-Management-System/
│
├── README.md
│
├── subscription_management.sql
│
└── SUBSCRIPTION.pdf

«The ".sql" file contains the database tables, sample data, queries, views, stored procedures, and analysis queries.»

💡 Key Insights

The project demonstrates how relational databases can be used to analyze:

- Customer subscription behavior
- Revenue generation
- Plan popularity
- Customer spending
- Subscription status
- Usage patterns
- Discount information

🚀 Future Enhancements

- Build a Power BI dashboard using the subscription database
- Add automated subscription renewal
- Add payment transaction tracking
- Add customer churn-rate calculations
- Add monthly and yearly revenue dashboards
- Add more advanced SQL analytics using window functions

👩‍💻 Author

Nanditha Reddy

Skills Demonstrated

"SQL" "MySQL" "Database Management" "Data Analysis" "Joins" "Subqueries" "Views" "Stored Procedures"
