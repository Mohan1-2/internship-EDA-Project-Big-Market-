# internship-EDA-Project-Big-Market-
# Importing neccesary libraries.

import pandas as pd

import numpy as np

import matplotlib.pyplot as plt

import seaborn as sns

%matplotlib inline

# 1.Reading and Inspection

df = pd.read_csv('/content/drive/MyDrive/1. BigMart.csv')

df.head(5)

df.teil(5)

# Check number of rows and columns in the dataset

num_rows, num_columns = df.shape

print("Number of rows:", num_rows)

print("Number of columns:", num_columns)

# Get unique OutletTypes and count of records for each type

outlet_types_count = df['OutletType'].value_counts()

print("Different types of OutletTypes and their count:")

print(outlet_types_count)

# Calculate average Weight

average_item_weight = df['Weight'].mean()

# Plot histogram of ProductVisibility	

plt.hist(df['ProductVisibility'], bins=20, color='blue', alpha=0.7)

plt.xlabel('ProductVisibility')

plt.ylabel('Frequency')

plt.title('Histogram of ProductVisibility')

plt.show()

# Calculate average MRP for each OutletType

average_item_mrp_by_outlet_type = df.groupby('OutletType')['MRP'].mean()

print("Average MRP for each OutletType:")

print(average_item_mrp_by_outlet_type)

print("Average ItemWeight across all products:", average_item_weight)

# Find OutletSize with highest total ItemOutletSales

highest_total_sales_outlet_size = df.groupby('OutletSize')['OutletSales'].sum().idxmax()

print("OutletSize with highest total OutletSales:", highest_total_sales_outlet_size)

# Identify and list the top 5 most common ItemTypes

top_5_item_types = df['OutletType'].value_counts().head(5)

print("Top 5 most common OutletType:")

print(top_5_item_types)

# Plot a boxplot of ItemOutletSales for each OutletSize

plt.figure(figsize=(8, 6))

sns.boxplot(x='OutletSize', y='OutletSales', data=df)

plt.title('Boxplot of OutletSales for each OutletSize')

# Calculate correlation between Weight and OutletSales

correlation = df['Weight'].corr(df['OutletSales'])

print("Correlation between Weight and OutletSales:", correlation)

plt.show()

# Create a pivot table showing the average OutletSales for each OutletType and LocationType

pivot_table = pd.pivot_table(df, values='OutletSales', index='OutletType', columns='LocationType', aggfunc='mean')

print("Pivot table showing the average OutletSales for each OutletType and LocationType:")

print(pivot_table)

# conclusion

1.The dataset has 8523 row and 12 columns

2.The average Weight across all products is 12.85764

3.OutletSize has the highest total OutletSales is Medium

4. The correlation between Weight and OutletSales is 0.01412
