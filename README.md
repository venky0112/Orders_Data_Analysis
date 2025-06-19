# Orders Data Analysis
This repository contains the Orders Data Analysis project, which demonstrates skills in data wrangling, visualization, and Python programming, alongside SQL queries for data analysis.

## Files
### `data_analysis_project.ipynb`
This Jupyter Notebook contains Python code for analyzing and visualizing the `orders.csv` dataset.

#### Key Features:

1. **Data Loading and Cleaning**
   ```python
   #read data from the file and handle null values

   import pandas as pd
   df = pd.read_csv('orders.csv', na_values=['Not Available', 'unknown'])
   df['Ship Mode'].unique()
   ```
   Importing libraries: The code imports the pandas library to handle data.

   Loading the dataset: Reads the orders.csv file into a DataFrame and treats specific strings as missing values.

   Inspecting a column: Displays unique values in the Ship Mode column.

2. **Column Normalization**
   ```python
   #rename columns names ..make them lower case and replace space with underscore

   df.rename(columns={'Order Id': 'order_id', 'City': 'city'})
   df.columns = df.columns.str.lower()
   df.columns = df.columns.str.replace(' ', '_')
   df.head(5)
   ```
   Renaming columns: Standardizes column names to lowercase and replaces spaces with underscores.

3. **Basic Analysis**
   ```python
   df['segment'].value_counts()
   ```
   Segment distribution: Analyzes frequency of values in the segment column.

4. **Data Visualization**
   ```python
   import matplotlib.pyplot as plt
   import seaborn as sns

   # Displaying the first few rows
   print(df.head())

   # Visualizing order category distribution
   sns.countplot(data=df, x='category')
   plt.title('Order Category Distribution')
   plt.show()
   ```
   Importing libraries: Imports matplotlib.pyplot and seaborn for creating visualizations.

   Sample data: Prints the top rows to verify the data structure.

   Order category distribution: Uses a count plot to show the frequency of each category.

   Title and display: Adds a title and displays the plot.

5. **Feature Engineering**
   ```python
   #derive new columns discount , sale price and profit

   df['discount'] = df['list_price'] * df['discount_percent'] * 0.01
   df['sale_price'] = df['list_price'] - df['discount']
   df['profit'] = df['sale_price'] - df['cost_price']
   df
   ```
   Derived columns: Calculates the discount, final sale price after discount, and profit by subtracting cost price from sale price.

   Final output: Displays the updated DataFrame with new columns.

### `orders.csv`
This CSV file contains raw data for the analysis, including columns such as:

- `order_id`: Unique identifier for each order.
- `customer_id`: Unique identifier for each customer.
- `order_date`: Date when the order was placed.
- `list_price`: Listed price before any discount.
- `discount_percent`: Percentage discount applied.
- `cost_price`: Cost to the company.
- `segment`: Customer segment.
- `category`: Category of the order.

Example:
```csv
order_id,customer_id,order_date,list_price,discount_percent,cost_price,segment,category
1,123,2023-01-01,100.50,10,80.00,Consumer,Electronics
2,124,2023-01-02,200.75,5,150.00,Corporate,Apparel
3,125,2023-01-03,150.20,15,120.00,Home Office,Groceries
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
   Group by order status: Aggregates sales based on order_status.

   Calculate total sales: Sums up the total_amount for each status.

   Sort results: Orders the statuses by total sales in descending order.

2. **Find Top 5 Customers by Total Spend**
   ```sql
   SELECT customer_id, SUM(total_amount) AS total_spend
   FROM orders
   GROUP BY customer_id
   ORDER BY total_spend DESC
   LIMIT 5;
   ```
   Group by customer ID: Aggregates sales for each customer.

   Calculate total spend: Sums up the total_amount for each customer.

   Sort and limit: Orders customers by their total spending and selects the top 5.

3. **Analyze Monthly Sales Trends**
   ```sql
   SELECT DATE_FORMAT(order_date, '%Y-%m') AS month, SUM(total_amount) AS monthly_sales
   FROM orders
   GROUP BY month
   ORDER BY month;
   ```
   Format dates: Extracts the year and month from order_date.

   Calculate monthly sales: Sums up the total_amount for each month.

   Sort results: Orders the months chronologically.

## Getting Started
Clone the repository:
```bash
git clone https://github.com/your-username/orders-data-analysis.git
cd orders-data-analysis
```
Open the Jupyter Notebook to explore the Python code and results.

Use your preferred SQL client to run the queries from `sql_code.sql`.

## Contribution
Contributions are welcome! Feel free to fork the repository and submit pull requests for improvements or additional features.
