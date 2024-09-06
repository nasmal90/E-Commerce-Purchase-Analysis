# E-Commerce Purchases Data Analysis

## 📖 Introduction
This project focuses on analyzing a dataset of e-commerce purchases to gain insights into customer behavior, purchasing patterns, and trends. Using Python and popular data science libraries, we explore relationships between factors such as purchase price, customer occupation, and credit card provider.

## 🎯 Objective
The main goals of this project are:
- **Data Cleaning:** Handling missing values and formatting data for analysis.
- **Analyzing Trends:** Understanding the influence of job titles, languages, and credit card providers on purchasing behavior.
- **Data Visualization:** Using various visual tools like scatter plots and bar charts to display purchasing patterns.

## 🛠️ Tools Used
- **Python:** Main programming language for analysis.
- **Pandas:** For data manipulation and cleaning.
- **NumPy:** For numerical operations.
- **Matplotlib & Seaborn:** For data visualization.

## 📊 Dataset Overview
The dataset contains information on 10,000 anonymized e-commerce purchases, including:
- **Purchase Price:** The amount spent by the customer.
- **Job Title:** Customer’s occupation.
- **Credit Card Provider:** The company that issued the credit card used for the purchase.
- **Email:** Customer’s email address.
- **Language:** The customer’s primary language.

## 🔑 Key Steps in the Analysis

### 1. Loading and Cleaning the Data
We begin by loading the dataset using Pandas and handling any missing values.
```python
import pandas as pd

# Load the dataset
data = pd.read_csv('data/Ecommerce Purchases.csv')

# Check for missing data
missing_data = data.isnull().sum()
print(missing_data)

# Drop rows with missing data if necessary
data = data.dropna()
```
### 2. Descriptive Statistics
We calculated key statistics to understand the purchase price distribution.
```
# Basic statistics for numerical columns
data.describe()

# Calculate average, maximum, and minimum purchase prices
average_price = data['Purchase Price'].mean()
max_price = data['Purchase Price'].max()
min_price = data['Purchase Price'].min()

print(f"Average Purchase Price: {average_price}")
print(f"Max Purchase Price: {max_price}")
print(f"Min Purchase Price: {min_price}")
```
### 3. Common Job Titles
We explored the most frequent job titles among the customers.
```
# Most common job titles
top_jobs = data['Job'].value_counts().head(10)
print(top_jobs)
```
### 4. Credit Card Provider Analysis
We examined the most common credit card providers and their relationship with purchase prices.
```
# Most common credit card providers
top_cc_providers = data['CC Provider'].value_counts().head(10)
print(top_cc_providers)

# Average purchase price per credit card provider
avg_price_per_provider = data.groupby('CC Provider')['Purchase Price'].mean()
print(avg_price_per_provider)
```
### 5. Visualizations
Scatter Plot: Purchase Price vs Credit Card Expiration Year
```
import matplotlib.pyplot as plt

plt.scatter(data['CC Exp Year'], data['Purchase Price'])
plt.title('Purchase Price vs Credit Card Expiration Year')
plt.xlabel('Credit Card Expiration Year')
plt.ylabel('Purchase Price')
plt.show()
```
Bar Chart: Top 10 Job Titles
```
top_jobs.plot(kind='bar')
plt.title('Top 10 Job Titles')
plt.xlabel('Job Title')
plt.ylabel('Count')
plt.show()
```
Correlation Heatmap
```
import seaborn as sns

corr_matrix = data.corr()
sns.heatmap(corr_matrix, annot=True, cmap='coolwarm')
plt.title('Correlation Matrix')
plt.show()
```
## 📈 Results & Insights
The average purchase price was $50.35, with a maximum of $99.99 and a minimum of $0.00.
Credit Card Providers: The most common providers were Mastercard, Visa, and American Express.
Job Titles: Common occupations included "Engineer," "Lawyer," and "Doctor," each showing different purchasing behaviors.
## 🚀 Future Improvements
Incorporate machine learning algorithms to predict customer purchasing behavior based on demographics.
Time-series analysis could be applied if timestamp data is available in future datasets.
