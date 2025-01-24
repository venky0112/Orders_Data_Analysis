# Orders Data Analysis

This repository contains the Orders Data Analysis project demonstrating skills in data wrangling, visualization, and Python programming.

## Files

### `data_analysis_project.ipynb`
```python
# Importing libraries
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Loading the dataset
orders = pd.read_csv('orders.csv')

# Data cleaning: Dropping duplicates
orders = orders.drop_duplicates()

# Visualizing order status distribution
sns.countplot(data=orders, x='order_status')
plt.title('Order Status Distribution')
plt.show()

# Analyzing total sales by status
sales_by_status = orders.groupby('order_status')['total_amount'].sum()
print(sales_by_status)

# Displaying the first few rows
print(orders.head())

# Visualizing order category distribution
sns.countplot(data=orders, x='category')
plt.title('Order Category Distribution')
plt.show()
```

### `orders.csv`
This CSV file contains the raw dataset used in the analysis.

### `sql_code.sql`
```sql
-- Calculate total sales by order status
SELECT order_status, SUM(total_amount) AS total_sales
FROM orders
GROUP BY order_status
ORDER BY total_sales DESC;
```
bution
Feel free to fork the repository and submit pull requests for improvements or additional features!
