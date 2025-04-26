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
<img width="755" alt="DATA PREPROCESSING" src="https://github.com/user-attachments/assets/c0356585-e451-497d-b32f-397b9e9de5e1" />


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
<img width="175" alt="DATA MODIFICATION" src="https://github.com/user-attachments/assets/57714133-f806-4035-8603-40b81f1face8" />

## DATA ANALYSIS
## DATA FILTERING
```Python
# Extracting bikes sales data from the US 

is_USA = bikes_df["CustomerCountry"] == "United States"

is_bikes = bikes_df["ProductCategory"] == "Bikes"

bikes_in_US = bikes_df[(is_USA) & (is_bikes)]

bikes_in_US.head()



```
<img width="758" alt="DATA FILTERING 1" src="https://github.com/user-attachments/assets/b9e865d0-846f-4eb1-8bde-081cbe71768a" />
<img width="357" alt="DATA FILTERING 2" src="https://github.com/user-attachments/assets/7ba83bfe-4a82-4b85-bf56-247c2763f6d7" />

#### DATA AGGREGATION
```Python
# aggregating and summarising data for bike sales

bikes_in_US.pivot_table(values = "Profit", index = "CustomerState", aggfunc = np.sum)

Total_profit_by_state = bikes_in_US.pivot_table(values = "Profit", index = "CustomerState", aggfunc = np.sum)

Total_profit_by_state


```
<img width="198" alt="DATA AGGREGATION 1" src="https://github.com/user-attachments/assets/2140c6ae-356d-4308-9886-6a4b9df91a59" />
<img width="133" alt="DATA AGGREGATION 2" src="https://github.com/user-attachments/assets/4d82a4eb-bd35-4a7a-a1b0-7bba52249096" />

#### DATA SORTING
```Python
# sorting the aggregated bike sales data to rank the states according to the most profitable states

Total_profit_by_state.sort_values("Profit", ascending = False)

top_5_profitable_states_USA = Total_profit_by_state.sort_values("Profit", ascending = False)

top_5_profitable_states_USA.head()


```
<img width="146" alt="DATA SORTING" src="https://github.com/user-attachments/assets/3b9cf7e2-b724-4c6a-8758-db63410f6a20" />

#### RESULT
```Python
# What are the Top Most-Profitable 5 States for the Bike Product Category in the United States?

top_5_profitable_states_USA.head()


```
<img width="125" alt="SCREENSHOT FOR THE ONE BEFORE THE BAR" src="https://github.com/user-attachments/assets/4dae00b3-0b92-4ebe-8d96-5a3e038165e0" />


## DATA VISUALIZATION
```Python
# Visualising the aggregated and sorted data

top_5_profitable_states_USA.plot(kind = "bar")

plt.title("The Top 5 Most Profitable States in the US for Bikes")

plt.ylabel("Total profit in million dollars")

plt.xlabel("States")

plt.show()



```
<img width="346" alt="PROJECT_1_SCREENSHOT" src="https://github.com/user-attachments/assets/a3509c2b-6fd9-44f5-988c-a8ec6893f99e" />

