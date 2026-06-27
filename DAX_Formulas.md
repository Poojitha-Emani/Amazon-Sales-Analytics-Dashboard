## 🧮 DAX Formulas

-- 💰 SALES & PROFIT

Total Sales = SUM(AmazonSales[Sales])

Total Profit = SUM(AmazonSales[Profit])

Profit Margin % = DIVIDE([Total Profit], [Total Sales]) * 100


-- 📦 ORDERS & QUANTITY

Total Orders = DISTINCTCOUNT(AmazonSales[Order ID])

Total Quantity = SUM(AmazonSales[Quantity])

AOV (Average Order Value) = DIVIDE([Total Sales], [Total Orders])


-- 🚚 SHIPPING & RETURNS

Total Shipping Cost = SUM(AmazonSales[Shipping Cost])

Return Rate % =
DIVIDE(
    SUM(AmazonSales[Returned Orders]),
    [Total Orders]
) * 100


-- 📈 TREND ANALYSIS

Monthly Sales =
CALCULATE(
    [Total Sales],
    DATESMTD(AmazonSales[Order Date])
)

Yearly Sales =
CALCULATE(
    [Total Sales],
    YEAR(AmazonSales[Order Date])
)

Sales Growth % =
DIVIDE(
    [Total Sales] - CALCULATE([Total Sales], PREVIOUSYEAR(AmazonSales[Order Date])),
    CALCULATE([Total Sales], PREVIOUSYEAR(AmazonSales[Order Date]))
) * 100


-- 🏆 PRODUCT ANALYSIS

Category Sales = SUM(AmazonSales[Sales])

Top Products Rank =
RANKX(
    ALL(AmazonSales[Product Name]),
    [Total Sales],
    ,
    DESC
)
