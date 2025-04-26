# Sales_Analysis_for_an_Automobile_Company_USA
A data science project that analysed the sales performance of an automobile company based in the United States. The company’s sales transaction data generated over the past years was used for this analysis.
## PROBLEM STATEMENT
What are the Top Most-Profitable 5 States for the Bike Product Category in the United States?
## DATA PRE-PROCESSING
#### DATA LOADING
```Python
## importing the necessary python packages 

import numpy as np 
import pandas as pd 
import matplotlib.pyplot as plt

print("The packages have been imported")





```
```Python
# reading the sale data into a pandas dataframe 

bikes_df = pd.read_csv("C:/Users/Windows/OneDrive/Desktop/DATA SCIENCE FILES/DATA SETS/bikes.csv")

bikes_df.head()




```
## DATA MODIFICATION
```Python
# Adding the following 3 columns to the pansdas Dataframe: bikes_df


# TotalCostPrice : To be obtained by (OrderQuantity x CostPrice_usd)


bikes_df["TotalCostPrice"] = bikes_df["OrderQuantity"] * bikes_df["CostPrice_usd"] 


# SalesRevenue : To be obtained by (OrderQuantity x SellingPrice_usd)


bikes_df["SalesRevenue"] = bikes_df["OrderQuantity"] * bikes_df["SellingPrice_usd"] 


# Profit : To be obtained by (SalesRevenue - TotalCostPrice)


bikes_df["Profit"] = bikes_df["SalesRevenue"] - bikes_df["TotalCostPrice"]


bikes_df.head()



```
## DATA ANALYSIS
## DATA FILTERING
```Python
# Extracting bikes sales data from the US 

is_USA = bikes_df["CustomerCountry"] == "United States"

is_bikes = bikes_df["ProductCategory"] == "Bikes"

bikes_in_US = bikes_df[(is_USA) & (is_bikes)]

bikes_in_US.head()



```
