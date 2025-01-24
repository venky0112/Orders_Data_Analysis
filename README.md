# Orders Data Analysis
This repository contains the Orders Data Analysis project, which demonstrates skills in data wrangling, visualization, and Python programming, alongside SQL queries for data analysis.

## Files
### `data_analysis_project.ipynb`
This Jupyter Notebook contains Python code for analyzing and visualizing the `orders.csv` dataset.

#### Key Features:

1. **Data Loading and Cleaning**
   ```python
   # Importing libraries
   import pandas as pd

   # Loading the dataset
   orders = pd.read_csv('orders.csv')
   
   # Data cleaning: Dropping duplicates
   orders = orders.drop_duplicates()

   # Displaying the first few rows of the dataset
   print(orders.head())
   ```
   - **Importing libraries**: The code imports the `pandas` library to handle data.
   - **Loading the dataset**: Reads the `orders.csv` file into a DataFrame.
   - **Dropping duplicates**: Removes duplicate rows to ensure data integrity.
   - **Displaying rows**: Outputs the first five rows to verify the dataset.

2. **Data Visualization**
   ```python
   import matplotlib.pyplot as plt
   import seaborn as sns

   # Visualizing order status distribution
   sns.countplot(data=orders, x='order_status')
   plt.title('Order Status Distribution')
   plt.show()
   ```
   - **Importing libraries**: Imports `matplotlib.pyplot` and `seaborn` for creating visualizations.
   - **Order status distribution**: Uses a count plot to show the frequency of each order status.
   - **Title and display**: Adds a title and displays the plot.

   ```python
   # Visualizing order category distribution
   sns.countplot(data=orders, x='category')
   plt.title('Order Category Distribution')
   plt.show()
   ```
   - **Order category distribution**: Similar to the previous snippet, this visualizes the frequency of orders in each category.
   - **Title and display**: Adds a title and displays the plot.

3. **Data Aggregation**
   ```python
   # Analyzing total sales by status
   sales_by_status = orders.groupby('order_status')['total_amount'].sum()
   print("Total Sales by Status:")
   print(sales_by_status)
   ```
   - **Grouping data**: Groups the dataset by `order_status`.
   - **Calculating total sales**: Sums up the `total_amount` for each status.
   - **Printing results**: Displays total sales for each order status.

### `orders.csv`
This CSV file contains raw data for the analysis, including columns such as:
- `order_id`: Unique identifier for each order.
- `customer_id`: Unique identifier for each customer.
- `order_status`: Current status of the order (e.g., Completed, Cancelled).
- `order_date`: Date when the order was placed.
- `total_amount`: Total value of the order.
- `category`: Category of the order.

Example:
```csv
order_id,customer_id,order_status,order_date,total_amount,category
1,123,Completed,2023-01-01,100.50,Electronics
2,124,Cancelled,2023-01-02,200.75,Apparel
3,125,Pending,2023-01-03,150.20,Groceries
```

### `sql_code.sql`
This SQL script contains queries to analyze the dataset.

#### Example Queries:

1. **Calculate Total Sales by Order Status**
   ```sql
   SELECT order_status, SUM(total_amount) AS total_sales
   FROM orders
   GROUP BY order_status
   ORDER BY total_sales DESC;
   ```
   - **Group by order status**: Aggregates sales based on `order_status`.
   - **Calculate total sales**: Sums up the `total_amount` for each status.
   - **Sort results**: Orders the statuses by total sales in descending order.

2. **Find Top 5 Customers by Total Spend**
   ```sql
   SELECT customer_id, SUM(total_amount) AS total_spend
   FROM orders
   GROUP BY customer_id
   ORDER BY total_spend DESC
   LIMIT 5;
   ```
   - **Group by customer ID**: Aggregates sales for each customer.
   - **Calculate total spend**: Sums up the `total_amount` for each customer.
   - **Sort and limit**: Orders customers by their total spending and selects the top 5.

3. **Analyze Monthly Sales Trends**
   ```sql
   SELECT DATE_FORMAT(order_date, '%Y-%m') AS month, SUM(total_amount) AS monthly_sales
   FROM orders
   GROUP BY month
   ORDER BY month;
   ```
   - **Format dates**: Extracts the year and month from `order_date`.
   - **Calculate monthly sales**: Sums up the `total_amount` for each month.
   - **Sort results**: Orders the months chronologically.

## Getting Started
1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/orders-data-analysis.git
   cd orders-data-analysis
   ```
2. Open the Jupyter Notebook to explore the Python code and results.
3. Use your preferred SQL client to run the queries from `sql_code.sql`.

## Contribution
Contributions are welcome! Feel free to fork the repository and submit pull requests for improvements or additional features.
