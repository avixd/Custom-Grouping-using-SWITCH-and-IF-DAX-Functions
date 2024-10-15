# Custom-Grouping-using-SWITCH-and-IF-DAX-Functions
## Problem Statement:

Based on given lowerbound and upperbound thresholds, create a grouping between the given range such as “0-50K”, “50K-100K” etc.

![](Capture.png align="center")

## Solution:

Create a column or measure with the code below:

Grouped Income (Switch) = SWITCH( TRUE() , AND(DimCustomer\[YearlyIncome\]&gt;= 0,DimCustomer\[YearlyIncome\]&lt; 50000), "0-50K", AND(DimCustomer\[YearlyIncome\]&gt;= 50000,DimCustomer\[YearlyIncome\]&lt; 100000), "50-100K", AND(DimCustomer\[YearlyIncome\]&gt;= 100000,DimCustomer\[YearlyIncome\]&lt; 150000), "100-150K", "150k+" )

Grouped Income (IF) = IF( AND(DimCustomer\[YearlyIncome\]&gt;= 0,DimCustomer\[YearlyIncome\]&lt; 50000), "0-50K", IF( AND(DimCustomer\[YearlyIncome\]&gt;= 50000,DimCustomer\[YearlyIncome\]&lt; 100000), "50-100K", IF( AND(DimCustomer\[YearlyIncome\]&gt;= 100000,DimCustomer\[YearlyIncome\]&lt; 150000), "100-150K", "150k+" )))

Any similar groupings could be established by replacing

“DimCustomer” → Table Name

“YearlyIncome” → Column Name

### Links:

[SWITCH documentation:](https://learn.microsoft.com/en-us/dax/switch-function-dax)

[IF documentation:](https://learn.microsoft.com/en-us/dax/if-function-dax)
