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
-----
2. merging
Go to Data > Get & Transform > From Table/Range

Load Orders as a query.

Load Customers as a query.

In Power Query:

Use Merge Queries

Join on customer_id

Expand to include customer name, city, etc.

Close & Load to a new sheet.
------
for example____
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
------
