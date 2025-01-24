# Orders Data Analysis

This repository contains various data analysis projects demonstrating skills in data wrangling, visualization, SQL queries, and Python programming. Below is an overview of the files included and how to use them.

---

## Files

### 1. `data_analysis_project.ipynb`
This Jupyter Notebook contains the Python code and analysis for data wrangling and visualization using the provided dataset.

#### Key Features:
- Data Cleaning
- Exploratory Data Analysis (EDA)
- Visualizations (e.g., bar plots, scatter plots, etc.)
- Insights derived from the data

#### How to Run:
1. Install the required dependencies:
   ```bash
   pip install pandas matplotlib seaborn
   ```
2. Open the notebook:
   ```bash
   jupyter notebook data_analysis_project.ipynb
   ```

#### Example Code:
```python
# Importing libraries
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Loading the dataset
orders = pd.read_csv('orders.csv')

# Displaying the first few rows
print(orders.head())

# Visualizing order status distribution
sns.countplot(data=orders, x='order_status')
plt.title('Order Status Distribution')
plt.show()
```

---

### 2. `orders.csv`
This CSV file contains the raw dataset used in the analysis. It includes information such as:
- Order ID
- Customer ID
- Order Status
- Order Date
- Total Amount

#### Example Preview:
```csv
order_id,customer_id,order_status,order_date,total_amount
1,123,Completed,2023-01-01,100.50
2,124,Cancelled,2023-01-02,200.75
3,125,Pending,2023-01-03,150.20
...
```

---

### 3. `sql_code.sql`
This SQL script contains queries to analyze the dataset from a relational database perspective.

#### Key Queries:
1. Calculate total sales by order status.
2. Find the top 5 customers by total spend.
3. Analyze monthly sales trends.

#### Example Query:
```sql
-- Calculate total sales by order status
SELECT order_status, SUM(total_amount) AS total_sales
FROM orders
GROUP BY order_status
ORDER BY total_sales DESC;
```

#### How to Use:
1. Import the `orders.csv` into your database.
2. Run the SQL queries using your preferred SQL client (e.g., MySQL Workbench, pgAdmin).

---

## Getting Started
1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/data-analyst-projects.git
   cd data-analyst-projects
   ```
2. Follow the instructions under each file to explore the analysis and insights.

---

## Contribution
Feel free to fork the repository and submit pull requests for improvements or additional features!
