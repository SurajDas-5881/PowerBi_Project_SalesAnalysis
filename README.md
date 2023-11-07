# PowerBi_Project_SalesAnalysis
here is an small key analysis dashboard of an company showing its sales and revenue trends.hope you will like it..
## Sales Insights Data Analysis Project

### Instructions to setup mysql on your local computer

1. SQL database dump is in db_dump.sql file above. Download `db_dump.sql` file to your local computer and import it as per instructions given in the tutorial video

### Data Analysis Using SQL

1. Show all customer records

    `SELECT * FROM customers;`

1. Show total number of customers

    `SELECT count(*) FROM customers;`

1. Show transactions for Chennai market (market code for chennai is Mark001

    `SELECT * FROM transactions where market_code='Mark001';`

1. Show distrinct product codes that were sold in chennai

    `SELECT distinct product_code FROM transactions where market_code='Mark001';`

1. Show transactions where currency is US dollars

    `SELECT * from transactions where currency="USD"`

1. Show transactions in 2020 join by date table

    `SELECT transactions.*, date.* FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020;`

1. Show total revenue in year 2020,

    `SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and transactions.currency="INR\r" or transactions.currency="USD\r";`
	
1. Show total revenue in year 2020, January Month,

    `SELECT SUM(transactions.sales_amount) FROM transactions
 INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and and date.month_name="January" and (transactions.currency="INR\r" or transactions.currency="USD\r");`

1. Show total revenue in year 2020 in Chennai
`SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020and transactions.market_code="Mark001";`


Data Analysis Using Power BI
.Create measure:

1. Revenue = SUM('sales transactions'[sales_amount])
2. SalesQuantity = SUM('sales transactions'[sales_qty])
3. tagret_profit = BaseMeasures[Total Profit]*1.5
4. Total Customers = COUNTROWS(SUMMARIZE('sales customers', 'sales customers'[customer_code]))
5. Total Orders = COUNTROWS(SUMMARIZE('sales transactions', 'sales transactions'[product_code], 'sales transactions'[Customer_code], 'sales transactions' [order_date]))
6. Total Profit = SUMX('sales transactions', 'sales transactions'[sales_qty] * 'sales transactions'[sales_amount])
7. Total Sales by Month = SUMX(SUMMARIZE('sales date', 'sales date'[date].[Year],'sales date'[date].[MonthNo]),    CALCULATE(SUM('sales transactions'[sales_amount])))
8. traget Revenue = BaseMeasures[Revenue]*1.7


Then Create visuals as shown in the picture:
1.revenue,profit,orders,quantity,customers total-card visual
2. then use line chart to show-sale performance by revenue by month.
3.then donought chart for-revenue bybzone
4.the two guage hart for -profit and profit target, revenue and revenue target.
