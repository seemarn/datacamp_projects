### Total Sales
Count the number of sales
> Total_Rows = COUNTROWS(Sales)

### Total Customers
Count the number of customers
> Number of Customers = DISTINCTCOUNTNOBLANK(Sales[Customer ID])

### Customer LTV (avg)
Calculates the average customer lifetime value by dividing the total sales by the number of unique customers.
> Customer LTV(avg) = SUM(Sales[Sales])/[Number of Customers]
 						
### Profit %
Calculates the profit percentage by dividing the total profit by the total sales.
> Profit % = SUM(Sales[Profit (Baseline)])/SUM(Sales[Sales])

### Baseline Running Total
Calculates the running total of baseline shipping costs up to the maximum transaction date, considering all selected sales.
> Baseline Running Total = SUMX(FILTER(ALLSELECTED(Sales), Sales[Transaction Date] <= MAX('Market Basket'[Transaction Date])), [Shipping (Baseline)])

### COGS
Calculates the cost of goods sold by multiplying the quantity of products sold by the landed cost per product.
>  COGS = Sales[Quantity]*RELATED(Products[Landed Cost])

### Difference Running Total
Calculates the running total difference between baseline and what-if shipping costs up to the maximum transaction date.
> Difference Running Total = SUMX(FILTER(ALLSELECTED(Sales), Sales[Transaction Date] <= MAX('Market Basket'[Transaction Date])), [Shipping Difference])

### Shipping (Baseline)
Calculates the baseline shipping cost, considering a tiered shipping cost structure based on the quantity of products purchased.
> Shipping (Baseline) = SUMX(Sales, IF(Sales[Quantity]=1,Sales[Shipping Cost],Sales[Shipping Cost]+(((Sales[Quantity])-1)*(Sales[Shipping Cost]*0.7))))

### Shipping (What-if)
Calculates the what-if shipping cost, considering a blended shipping cost factor based on the quantity of products purchased.
> Shipping (What-if) = SUMX(Sales, IF(Sales[Quantity]=1,Sales[Shipping Cost],Sales[Shipping Cost]+(((Sales[Quantity])-1)*(Sales[Shipping Cost]*
   [Blended Shipping Cost Factor]))))

### Shipping Difference
Calculates the difference between baseline and what-if shipping costs.
> Shipping Difference = [Shipping (Baseline)] - [Shipping (What-if)]

### What-if Running Total
Calculates the running total of what-if shipping costs up to the maximum transaction date.
> what - if running total = SUMX(FILTER(ALLSELECTED(Sales), Sales[Transaction Date] <= MAX('Market Basket'[Transaction Date])), [Shipping (What-if)])

### Blended Shipping Cost Factor
Assigns a blended shipping cost factor based on the quantity of products purchased, determining the discount applied to shipping costs.
> Blended Shipping Cost Factor = IF('What - if quantity'[What - if quantity Value] <=1,1, IF('What - if quantity'[What - if quantity Value]<=2,0.8,IF('What - if quantity'[What - if quantity Value]<=4,0.6,IF('What - if quantity'[What - if quantity Value]<=7,0.5,IF('What - if quantity'[What - if quantity Value]<=9,0.4,0.3)))))


