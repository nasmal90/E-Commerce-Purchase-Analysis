{\rtf1\ansi\ansicpg1252\cocoartf2761
\cocoatextscaling0\cocoaplatform0{\fonttbl\f0\fswiss\fcharset0 Helvetica;}
{\colortbl;\red255\green255\blue255;}
{\*\expandedcolortbl;;}
\paperw11900\paperh16840\margl1440\margr1440\vieww11520\viewh8400\viewkind0
\pard\tx566\tx1133\tx1700\tx2267\tx2834\tx3401\tx3968\tx4535\tx5102\tx5669\tx6236\tx6803\pardirnatural\partightenfactor0

\f0\fs24 \cf0 # E-Commerce Purchases Data Analysis\
\
## Introduction\
This project analyzes a dataset of e-commerce purchases, extracting insights into customer behavior, purchasing patterns, and trends. The analysis uses Python and several popular data science libraries to explore relationships between factors such as purchase price, language, job title, and credit card provider.\
\
## Objective\
The main objectives of the project include:\
- **Data Cleaning:** Handling missing values and formatting columns for analysis.\
- **Analyzing Trends:** Understanding the impact of job titles, languages, and credit card providers on purchasing behavior.\
- **Data Visualization:** Creating scatter plots, bar charts, and other visual tools to display purchasing patterns.\
  \
## Tools Used\
- **Python:** Main programming language for analysis.\
- **Pandas:** For data manipulation and cleaning.\
- **NumPy:** For numerical operations.\
- **Matplotlib & Seaborn:** For data visualization.\
\
## Dataset\
The dataset contains information on 10,000 anonymized e-commerce purchases, including:\
- **Purchase Price:** The price paid by the customer for the product.\
- **Job Title:** The customer's occupation.\
- **Credit Card Provider:** The provider of the credit card used for the purchase.\
- **Email:** The customer's email address.\
- **Language:** The primary language spoken by the customer.\
\
## Key Steps in the Analysis\
\
### 1. Loading and Cleaning the Data\
We loaded the dataset using Pandas and handled missing values:\
\
```python\
import pandas as pd\
\
# Load the dataset\
data = pd.read_csv('data/Ecommerce Purchases.csv')\
\
# Check for missing data\
missing_data = data.isnull().sum()\
print(missing_data)\
\
# Drop rows with missing data if necessary\
data = data.dropna()\
```\
\
### 2. Descriptive Statistics\
We calculated basic statistics to get an understanding of the purchase price distribution:\
\
```python\
# Get basic statistics for the numerical columns\
data.describe()\
\
# Calculate average, maximum, and minimum purchase prices\
average_price = data['Purchase Price'].mean()\
max_price = data['Purchase Price'].max()\
min_price = data['Purchase Price'].min()\
\
print(f"Average Purchase Price: \{average_price\}")\
print(f"Max Purchase Price: \{max_price\}")\
print(f"Min Purchase Price: \{min_price\}")\
```\
\
### 3. Common Job Titles\
We explored the most frequent job titles of the customers:\
\
```python\
# Most common job titles\
top_jobs = data['Job'].value_counts().head(10)\
print(top_jobs)\
```\
\
### 4. Credit Card Provider Analysis\
We examined the most common credit card providers and their relationship to purchase prices:\
\
```python\
# Most common credit card providers\
top_cc_providers = data['CC Provider'].value_counts().head(10)\
print(top_cc_providers)\
\
# Average purchase price per credit card provider\
avg_price_per_provider = data.groupby('CC Provider')['Purchase Price'].mean()\
print(avg_price_per_provider)\
```\
\
### 5. Visualizations\
\
- **Scatter Plot: Purchase Price vs Credit Card Expiration Year**\
    ```python\
    plt.scatter(data['CC Exp Year'], data['Purchase Price'])\
    plt.title('Purchase Price vs Credit Card Expiration Year')\
    plt.xlabel('Credit Card Expiration Year')\
    plt.ylabel('Purchase Price')\
    plt.show()\
    ```\
\
- **Bar Chart for Job Titles**\
    ```python\
    top_jobs.plot(kind='bar')\
    plt.title('Top 10 Job Titles')\
    plt.xlabel('Job Title')\
    plt.ylabel('Count')\
    plt.show()\
    ```\
\
- **Correlation Heatmap**\
    ```python\
    corr_matrix = data.corr()\
    sns.heatmap(corr_matrix, annot=True, cmap='coolwarm')\
    plt.title('Correlation Matrix')\
    plt.show()\
    ```\
\
## Results & Insights\
- The **average purchase price** was calculated to be $50.35, with a maximum of $99.99 and a minimum of $0.00.\
- **Credit Card Providers**: The most common providers were Mastercard, Visa, and American Express.\
- **Job Titles**: The most common occupations included "Engineer," "Lawyer," and "Doctor," with varied purchasing behavior.\
\
## Future Improvements\
- Apply machine learning algorithms to predict customer purchase behavior based on demographic data.\
- Add time-series analysis if timestamp data is available in future datasets.\
}