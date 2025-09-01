# Python-Project
'''

1.	Import All data from data sheet in Frame and find the sum, average of Sales and Profit of data
 by region wise and plot it with Appropriate Chart Like a.	Bar Chart, Line Chart, Pie Chart and
 Histogram
'''



import pandas as pd
import matplotlib.pyplot as plt

file_path = r"D:\Data.xlsx"

df = pd.read_excel(file_path)

pd.set_option('display.max_columns',None)
'''

Total_sales = round(df["Sales"].sum(),1)
Average_sales = round(df["Sales"].mean(),1)
Profit_by_region = round(df.groupby("Region")["profit"].sum(),1)
Total_Sales_region = round(df.groupby("Region")["Sales"].sum(),1)

print(df)
print("Total Sales :-",Total_sales)
print("Average Sales :-",Average_sales)
print("-----Proft by Region------",Profit_by_region)
print("------Total Sales by Region",Total_Sales_region)


# Profit by Region (bar chart)

plt.figure(figsize=(10,4))
Profit_by_region.plot(kind="bar")
plt.title("Profit by Region")
plt.xlabel("Region")
plt.ylabel("profit")
plt.xticks(rotation=45)
plt.show()



# Profit by Region (line chart)

plt.figure(figsize=(10,4))
Profit_by_region.plot(kind="line",marker="o")
plt.title("Profit by Region")
plt.xlabel("Region")
plt.ylabel("profit")
plt.xticks(rotation=45)
plt.show()



# Profit by Region (histogram)

plt.figure(figsize=(10,4))
plt.hist(Profit_by_region,bins=8,edgecolor="black")
plt.title("Profit by Region")
plt.xlabel("profit")
plt.ylabel("Frequency")
plt.show()




# Profit by Region (Pie Chart)

plt.pie(Profit_by_region,autopct="%1.f%%")
plt.title("Profit by Region")
plt.show()




# Total Sales by Region (bar chart)

plt.figure(figsize=(10,4))
Total_Sales_region.plot(kind="bar")
plt.title("Total Sales by Region")
plt.xlabel("Region")
plt.ylabel("Sales")
plt.xticks(rotation=45)
plt.show()




# Total Sales by Region (line chart)

plt.figure(figsize=(10,4))
Total_Sales_region.plot(kind="line",marker="o")
plt.title("Total Sales by Region")
plt.xlabel("Region")
plt.ylabel("Sales")
plt.xticks(rotation=45)
plt.show()


# Total Sales by Region (Histogram)

plt.figure(figsize=(10,4))
plt.hist(Total_Sales_region,bins=5,edgecolor="black")
plt.title("Total Sales by Region")
plt.xlabel("Sales")
plt.ylabel("Frequency")
plt.show()



# Total Sales by Region (Pie chart)

plt.pie(Total_Sales_region,autopct="%1.f%%")
plt.title("Total Sales by Region")
plt.show()




2.	Import All data from data sheet in Frame and sum, average of Sales and Profit of data by 
Region wise of data by Province and Product Category wise and plot it with Appropriate Chart Like
b.	Bar Chart, Line Chart, Pie Chart and Histogram
'''

Region_summary = round(df.groupby("Region")[["Sales","profit"]].agg(["sum","mean"]),1)
Province_summary= round(df.groupby("Province")[["Sales","profit"]].agg(["sum","mean"]),1)
Product_cat_ssummary = round(df.groupby("Product Category")[["Sales","profit"]].agg(["sum","mean"]),1)



print("-----------Region wise Sum and Profit--------------")
print(Region_summary)


print("-----------Province wise Sum and Profit--------------")
print(Province_summary)

print("-----------Province Category wise Sum and Profit--------------")
print(Product_cat_ssummary)




# Bar chart

Region_summary.plot(kind="bar",figsize=(10,4))
plt.title("Region Wise sales and profit")
plt.xlabel("Region")
plt.ylabel("Vales")
plt.xticks(rotation=45)
plt.show()


# Line Chart

Region_summary.plot(kind="line",marker="o",figsize=(10,4))
plt.title("Profit by Region")
plt.xlabel("Region")
plt.ylabel("Values")
plt.xticks(rotation=45)
plt.show()




