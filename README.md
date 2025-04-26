# Excel_AquaFizz-Employee-Compliance-and-Sales-Analysis
####  Project Overview
●	Objective:
 The main goal of this project is to analyze employee working hours and customer order data to ensure compliance with AquaFizz’s policies and optimize sales. The analysis involves examining data on working hours for compliance and generating business insights from customer and sales data.
●	Company Background:
 AquaFizz is a newly established beverage startup offering health-focused sparkling water beverages. The company aims to provide refreshing, nutrient-enhanced drinks while promoting overall wellness.
●	Business Task:
 The tasks include analyzing employee working hours for compliance with the company's standards and analyzing sales data to gain insights into customer behavior and identify top-performing products.
________________________________________
#### Data Understanding
●	Employee Working Hours Data:- Workers Timing Dataset
○	Dataset Name: Workers Timing Dataset
 The dataset includes:

■	Time of entry
■	Time of exit
●	Orders Data:
○	Dataset Name: Orders Dataset
Dataset Link:- Orders Dataset
 This dataset includes:
■	date: Date the order was placed
■	order_id: Unique identifier for each order
■	customer_id: Identifier linking the order to a customer
■	beverage: The type of beverage ordered
■	cost_price: The cost price of the beverage
■	selling_price: The price at which the beverage was sold
●	Customers Data:
○	Dataset Name:Customer Dataset
Dataset Link :-  Customer Dataset 
 This dataset includes:

■	customer_id: Unique identifier for each customer
■	first_name: Customer’s first name
■	last_name: Customer’s last name
■	email: Customer’s email address
■	city: The city where the customer is located
■	country: The country of residence for the customer
■	user: User type identifier
■	code: Customer code for internal use
________________________________________


### 1. Set Up Your Excel File (ETL: Load Stage)
Ensure your Excel has these 3 sheets:

Orders (e.g., order_id, order_date, product, customer_id, cost_price, selling_price)

Customers (e.g., customer_id, name, gender, city, email, phone)

Workers (if needed later for worker-based analysis)

Make sure:

Each sheet has proper headers

No merged cells

Clean data (no extra blank rows)

2. merging
   -----------
Go to Data > Get & Transform > From Table/Range

Load Orders as a query.

Load Customers as a query.

In Power Query:

Use Merge Queries

Join on customer_id

Expand to include customer name, city, etc.

Close & Load to a new sheet.

for example____
--------
Step 1: Load Both Tables into Power Query
Go to Orders Sheet → Click inside your table.

Go to the Data tab → Click From Table/Range.

If not formatted as a table, Excel will prompt you — click OK.

Rename the query as Orders.

Repeat the same steps for the Customers Sheet — name that query as Customers.

🔧 Step 2: Clean customerid in Customers Query
In the Customers query, click the customerid column (e.g., cust_00382).

Go to the Transform tab → Click Extract → Text After Delimiter.

Type _ as the delimiter.

This will keep only the numeric part (00382).

Select the new column → Go to Transform tab → Click Data Type → Select Whole Number.

✅ Now cust_00382 becomes 382.

✨ Optional: Rename the cleaned column as customerid (to match the Orders sheet).
🔁 Step 3: Join the Two Queries
Go to Home tab → Click Merge Queries → Choose Orders as the first table.

Select the customerid column in both queries.

Choose Join Kind: use Inner Join (only matching rows) or Left Join (all orders, with customer data if matched).

Merge first_name and last_name into full_name
1️⃣ Profit Calculation
Goal: Add a Profit column in the Orders table
Formula (in Power Query or Excel):

excel
Copy
Edit
= [selling_price] - [cost_price]
In Power Query:

Add Column → Custom Column → Profit = [selling_price] - [cost_price]

2️⃣ Top 5 Customers by Sales
Goal: Aggregate total sales (selling_price) by customer_id
Steps:

Use Pivot Table:

Rows: customer_id

Values: Sum of selling_price

Sort Descending

Filter: Top 5 (or just pick top 5 after sorting)

✅ You can add customer names from merged Customers data.

3️⃣ Top Cities by Sales
Goal: Sum of sales grouped by city
Steps:

Make sure city is merged from Customers data

Pivot Table:

Rows: city

Values: Sum of selling_price

Sort Descending → Top Cities

4️⃣ Monthly Sales Analysis
Goal: Calculate monthly total profit
Steps:

Add a column for Month in Power Query:

Add Column → Date → Month → Name or Number

Pivot Table:

Rows: Month

Values: Sum of Profit

Insert a Line Chart or Column Chart

✅ Helps visualize sales trends over time.

5️⃣ Highest Profit % Beverage
Goal: Identify beverage with highest profit margin
Formula:

excel
Copy
Edit
Profit % = ([selling_price] - [cost_price]) / [cost_price]
Add this column in Power Query or Excel.

Filter for Category = "Beverage" (if category exists).

Sort Profit % descending → Top 1 item.

6️⃣ Top 10 Beverage Purchasers
Goal: Count of beverage orders per customer
Steps:

Filter Orders where product category = Beverage

Pivot Table:

Rows: customer_id

Values: Count of order_id

Sort Descending → Top 10

✅ Add customer name if needed from merged table.

7️⃣ Excel Dashboard Creation
Combine:

Top 5 Customers Table/Chart

Top Cities Chart

Monthly Sales Line Chart

KPI Boxes for Highest Margin Beverage

Top 10 Purchasers Table

Total Profit Summary

Use:

Slicers (e.g., by month or city)

Conditional formatting

Clean layout: Left = charts, Right = stats


