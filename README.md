# Superstore Data Analysis Project

Superstore Data Analysis project delves into sales patterns, product performance, and customer behavior, providing insights that inform strategic decisions for the continued success and refinement of the Superstore.

Source code — Github

Table of Contents:
Introduction
Project Objectives
Requirements
Data Exploration and Cleaning
Data Collection
Data Exploration
Data Cleaning
Exploratory Data Analysis
a. Count of sub-category
b. Best Performing Category
c. Which customer segment is the most profitable?
d. Which is the preferred Ship Mode?
e. Customer Regional Analysis
Conclusion
Summary
References
Introduction
The Superstore Data Analysis Project focuses on extracting meaningful insights from a retail superstore dataset. The dataset contains information about sales, customers, products, and orders from a fictional retail superstore. Through analyzing this data, the goal is to uncover trends, patterns, and actionable insights that can help improve business operations and guide decision-making.

Project Objectives
The main objectives of this project are:

Data Exploration: Initially, i will explore the dataset to understand its structure and contents, providing context for the analysis.

Data Cleaning: Next, i'll clean and preprocess the data to ensure its suitability for analysis. This includes handling missing values, correcting data types, and removing duplicates.

Data Analysis: i will conduct in-depth analysis, examining sales trends, customer behavior, and product performance to generate meaningful insights.

Data Visualization: Visualization techniques will be employed to make the analysis more accessible and interpretable. We will create various types of charts, including bar charts, pie charts, and scatter plots, to highlight key findings.

Insights and Recommendations: Finally, based on the analysis, we will derive insights and offer actionable recommendations to improve business strategies, sales, and customer engagement.

Requirements
Before you begin, make sure you have the following installed:

Python 3.7 or higher
Jupyter Notebook or Google Colab
Pandas for data manipulation
Matplotlib for plotting graphs
Seaborn for statistical data visualization
NumPy for numerical operations
Data Exploration and Cleaning
This project begins with importing the dataset and exploring its structure. We will use the Pandas library to handle the data, Matplotlib and Seaborn for visualization, and NumPy for numerical operations. After loading the dataset, we will clean it by:

Removing duplicate entries.
Converting columns to the appropriate data types (e.g., converting 'OrderDate' from string to datetime).
Identifying and handling any missing values or anomalies.

Data Collection

import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

# Load the dataset
file_path = "superstore.csv"
superstore_data = pd.read_csv(file_path)

# Display the first row of the dataset
print(superstore_data.head(1))
Data Exploration
We use the info() method to examine the structure of the dataset and describe() for basic statistics.

# Explore the structure of the dataset
print(superstore_data.info())

# Display basic statistics of numerical columns
print(superstore_data.describe())
Data Cleaning
Now, i clean the dataset by removing duplicates, ensuring data consistency, and converting columns to appropriate data types:


# Drop duplicate rows
df.drop_duplicates(keep='first', ignore_index=True, inplace=True)

# Check for duplicates
print(df.duplicated().sum())

# Convert 'OrderDate' column to datetime format
df['OrderDate'] = pd.to_datetime(df['OrderDate'])
print(df['OrderDate'].dtype)
Exploratory Data Analysis
Now that the data is clean, we move to Exploratory Data Analysis (EDA). Here, we analyze the dataset in-depth to uncover patterns and trends.

a. Count of Sub-Category
 i start by analyzing the distribution of products across different sub-categories.


sns.countplot(x='SubCategory', data=df)
sns.set(rc={'figure.figsize':(12,5)})
plt.title('Count of SubCategory')
plt.show()
b. Best Performing Category
Next, we visualize the distribution of items across various categories:



sns.countplot(x='Category', data=df)
plt.title('Count of Category')
plt.show()

c. Which Customer Segment is the Most Profitable?
Here, we calculate the average profit for each customer segment.


df_segment_profit = df.groupby(['Segment'])[['Profit']].mean().reset_index()
sns.barplot(x='Segment', y='Profit', data=df_segment_profit)
plt.title('Customer Segment Profitability')
plt.show()
d. Which is the Preferred Ship Mode?
We analyze how different shipping modes contribute to sales and profit.

python
Copy
df_ship_mode = df.groupby(['ShipMode'])[['Sales', 'Profit']].sum().reset_index()

# Visualizing the Stacked Bar Chart
plt.figure(figsize=(10, 6))
plt.bar(df_ship_mode['ShipMode'], df_ship_mode['Sales'], color='skyblue')
plt.bar(df_ship_mode['ShipMode'], df_ship_mode['Profit'], bottom=df_ship_mode['Sales'], color='green')
plt.title('Sales & Profit Across Ship Modes')
plt.legend(['Sales', 'Profit'])
plt.xticks(rotation=45)
plt.show()
e. Customer Regional Analysis
Lastly, we analyze the total profit generated by each region:


region_analysis = df.groupby(['Region'])['Profit'].sum().reset_index()
plt.pie(region_analysis['Profit'], labels=region_analysis['Region'], autopct='%1.1f%%', startangle=90, explode=[0, 0, 0, 0.1])
plt.title('Most Profitable by Region')
plt.show()
Conclusion
In conclusion, this project explores various aspects of the Superstore Dataset, including sales trends, customer segments, product performance, and regional analysis. Our goal is to provide actionable insights that can help refine business strategies and drive profitability.

Summary
Data Exploration and Cleaning: Explored dataset structure, cleaned the data, and converted columns to suitable data types.
Exploratory Data Analysis: We investigated key factors such as sub-categories, best-performing categories, customer profitability, and regional analysis.
References
Pandas Documentation
NumPy Documentation
Matplotlib Documentation
Seaborn Documentation
