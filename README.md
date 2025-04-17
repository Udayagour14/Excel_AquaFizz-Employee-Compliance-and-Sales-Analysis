# Excel_AquaFizz-Employee-Compliance-and-Sales-Analysis
1. Set Up Your Excel File (ETL: Load Stage)
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
---
You said:
in excel i two sheets one is orders, another is customers both have customerid column but in order customerid is like 382,367 like number but in customers sheet customerid is like cust_00382 so how to handle and how to clean to data analysis
ChatGPT said:
Great question, Udaya! To clean and prepare this kind of data for analysis, your goal is to match the customer IDs in both sheets even though they are in different formats.

Let’s walk through a beginner-friendly, step-by-step guide in Excel:

🔧 Problem Recap:
Orders Sheet: customerid values like 382, 367 (numbers).

Customers Sheet: customerid values like cust_00382, cust_00367 (text with prefix and leading zeros).

You want to join/match these correctly for analysis (like VLOOKUP, Power Query, etc.)

✅ Goal:
Make both customerid formats matchable.

💡 Step-by-Step Solution (Inside Excel):
Option 1: Clean the customerid in Customers Sheet to match Orders Sheet
Go to Customers Sheet.

Suppose the customerid column is in Column A (cust_00382, cust_00367, etc.)

In a new column (say B), extract the numeric part:

excel
Copy
Edit
=VALUE(RIGHT(A2, 5))
✅ This will turn cust_00382 into 382 (number).
Use VALUE() to convert it from text to number so it matches the Orders sheet format.

Option 2: Clean the customerid in Orders Sheet to match Customers Sheet
Suppose the Orders Sheet has customerid like 382 in Column A.

In a new column, add this formula to match the customers format:

excel
Copy
Edit
="cust_" & TEXT(A2, "00000")
✅ This will turn 382 into cust_00382, matching the Customers sheet format.

🎯 Which Option to Choose?
If you plan to use VLOOKUP, XLOOKUP, or Power Query joins, it's usually easier to standardize both sides to the same format.

So either:

Extract numbers from cust_00382 → 382, OR

Format 382 → cust_00382.

🔄 Extra Tip (Power Query Way):
If you're using Power Query:

Use Transform Column → Extract Text After Delimiter "_" to get the numeric part from cust_00382.

Then change the data type to number.

Would you like me to walk you through this in Power Query too?

Let me know if you’d like a sample Excel file or formulas tailored to your actual column names!

You said:
yes i 
Would you like me to walk you through this in Power Query too
ChatGPT said:
​

You said:
yes i 
Would you like me to walk you through this in Power Query too
ChatGPT said:
Perfect! Here's a step-by-step guide to handle your customerid mismatch using Power Query in Excel 👇

🧩 Scenario Recap:
Orders Sheet: customerid is like 382 (number).

Customers Sheet: customerid is like cust_00382 (text with prefix).

You want to match/join both using Power Query.

✅ Step-by-Step: Cleaning in Power Query
🎯 Step 1: Load Both Tables into Power Query
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

Click OK.

✅ You’ll see a new column with a “Table” icon. Click the expand icon (↧) to choose which fields you want from the Customers table.

✅ Step 4: Finish
Click Close & Load to bring the cleaned, joined data into Excel.

🎉 You’re Done!
Now your customerid fields from both sheets are aligned and merged for analysis.

Would you like me to generate a mock Excel file for this example so you can try it out with real data?

You said:
in will do in power query and i have upload all sheets
ChatGPT said:
Awesome! Once you’ve uploaded the Excel file with your Orders and Customers sheets, I’ll help you step through the Power Query cleaning and merging process based directly on your data.

Go ahead and upload the file when you’re ready — I’ll take it from there!

You said:
yes
ChatGPT said:
Great! Please upload your Excel file now — just drag and drop it here, and I’ll guide you step-by-step using your actual data.

You said:
Customers.xlsx
Spreadsheet
Orders.xlsx
Spreadsheet
ChatGPT said:
Perfect, thanks for uploading both:

✅ Customers.xlsx

✅ Orders.xlsx

Now let’s walk through the Power Query steps using your actual files.

🧩 Goal:
Match customerid from:

Orders.xlsx: like 382

Customers.xlsx: like cust_00382

✅ Step-by-Step in Excel (Power Query)
1️⃣ Load Both Files into Power Query
For Customers.xlsx:

Open a blank Excel file (or one of the files).

Go to Data tab → Click Get Data → From File → From Workbook.

Select Customers.xlsx → Choose the correct sheet/table (e.g., Sheet1) → Click Load To → Only Create Connection.

Do the same for Orders.xlsx.

2️⃣ Transform customerid in Customers Table
In Power Query Editor, select the Customers query.

Click the customerid column (e.g., cust_00382).

Go to Transform tab → Click Extract → Text After Delimiter.

Type _ as the delimiter → Click OK.

You will get values like 00382.

Still selected → Go to Transform tab → Click Data Type → Select Whole Number.

It becomes like 382.

✅ Now, both Orders and Customers use numbers for customerid.

3️⃣ Merge the Two Tables
In Power Query Editor, go to the Orders query.

Click Home → Merge Queries → Choose Customers as the second table.

Select the customerid column from both.

Choose Join Kind:

Use Left Join if you want all orders, even unmatched ones.

Use Inner Join if you only want matched customers.

Click OK.

Click the expand icon (↧) on the new column → Select fields you want (like name, email, etc.) → Click OK.

4️⃣ Load Final Result
Click Close & Load → Load to a new worksheet.

✅ You now have a cleaned and merged dataset for analysis!
Would you like me to show you what the merged result would look like based on your data? I can preview it for you if you'd like.

You said:
which one suitable Use Left Join if you want all orders, even unmatched ones.

Use Inner Join if you only want matched customers.
ChatGPT said:
Great question, Udaya — here's how to decide based on your analysis goal:

🔁 Use LEFT JOIN when:
✅ You want to see all orders, even if a customer's details are missing.

Example use case:
You're doing sales analysis or want to find orders that don’t have matching customer data (maybe due to data entry issues).

You’ll get:


order_id	customerid	order_date	...	customer_name
101	382	2023-05-01	...	John Doe
102	888	2023-05-02	...	null
🟡 Notice how unmatched customers (like 888) still show up.

🔗 Use INNER JOIN when:
✅ You only want orders where customer info exists (fully matched).

Example use case:
You're doing customer behavior analysis and need full customer profiles for all records.

You’ll get:


order_id	customerid	order_date	...	customer_name
101	382	2023-05-01	...	John Doe
❌ Unmatched customer orders are excluded.

🎯 Recommendation for You:
Since you're cleaning and preparing for analysis:

Start with LEFT JOIN to preserve all orders.

Later, you can filter out null customer info if needed.

Would you like help visualizing unmatched orders using Power BI or a formula in Excel later on?

You said:
●Orders and Customers Data Processing:
○Profit Calculation:
 Calculate profit per sale as the difference between selling_price and cost_price for each order in the Orders dataset.
○Top 5 Customers by Sales:
 Using the Orders dataset, aggregate sales by customer_id and identify the top 5 customers with the highest total sales.
○Top Cities by Sales:
 Aggregate sales by city (from the Customers dataset) and identify the top cities contributing the most to sales.
○Monthly Sales Analysis:
 Extract the month from the order date and calculate the total profit for each month. Create a chart to visualize monthly sales trends.
○Highest Profit % Beverage:
 Calculate profit margin for each beverage ((Selling Price - Cost Price) / Cost Price) and identify the beverage with the highest profit margin.
○Top 10 Beverage Purchasers:
 Identify the top 10 customers who have purchased the most beverages by total number of orders.
○Excel Dashboard Creation:
 Combine the results from the analysis into a comprehensive Excel dashboard for easy visualization of key insights.
ChatGPT said:
Updated saved memory
Awesome, Udaya! You’ve outlined a solid project plan — this is a perfect case for Power Query + Pivot Tables + Charts in Excel. Let's break it down step-by-step and tackle each point.

✅ Step-by-Step Plan for Excel Dashboard Project
-----
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

