# Basic_Sales_Analysis
 Data Cleaning and Exploratory Data Analysis on Sales Data of 1 Year using python
## Sales Analysis with Pandas

This Jupyter Notebook performs an in-depth analysis of a year's worth of sales data. 

**Key Libraries:**

* pandas: Used for data manipulation, cleaning, and analysis
* matplotlib: Used for data visualization (charts)

**Data Preparation:**

1. **Merging Monthly Data:**
    * The script reads 12 separate CSV files (one per month) from a specified directory.
    * It iterates through each file, creating a DataFrame, and concatenates them into a single DataFrame named `all_months_data`.
    * This combined data is then saved to a new CSV file named "all_data.csv".

2. **Data Cleaning:**
    * The script identifies and removes rows containing missing values (NaN) in any column.
    * It also removes rows where the 'Order Date' starts with "Or" (considered inconsistent data).

3. **Feature Engineering:**
    * A new 'Month' column is created by extracting the first two characters from the 'Order Date' (assuming MM format). The data type is converted to integer for better manipulation.
    * A new 'Sales' column is created by multiplying 'Quantity Ordered' and 'Price Each', representing the total sale amount per order.

**Data Analysis:**

1. **Best Month for Sales:**
    * The script groups the data by 'Month' and calculates the total sales for each month using `.groupby()` and `.sum()`.
    * A bar chart is created using matplotlib to visualize the monthly sales trend.

2. **City with Highest Sales:**
    * A new 'City' column is created by extracting relevant parts (city and state) from the 'Purchase Address' column using a lambda function.
    * The script groups the data by 'City' and calculates the average sales for each city using `.groupby()` and `.mean()`.
    * A bar chart is generated using matplotlib to compare average sales across different cities.

3. **Optimal Time for Advertisements:**
    * Two approaches are presented to analyze peak purchase times:
        * A simpler approach extracts the hour from the 'Order Date' string and groups the data by 'Hour' to calculate total sales per hour. A bar chart visualizes the hourly sales trend.
        * A more robust approach converts the 'Order Date' into datetime format, allowing extraction of both hour and minute. It then groups by 'Hour' and displays the count of sales per hour. This provides a more granular view of purchase behavior.

4. **Products Frequently Sold Together:**
    * The script identifies orders with duplicate 'Order ID' (representing multiple items bought together).
    * It creates a new 'grouped' column using a lambda function within `.groupby()`, which combines all products within an order into a comma-separated string.
    * The script attempts to calculate the frequency of product co-occurrence using `.value_counts()`, but encounters a limitation where the order of product names within the string affects the count.
    * An alternative solution using `itertools` and `collections` is hinted at, requiring further exploration for implementation.

5. **Top-Selling Product Analysis:**
    * The script groups the data by 'Product' and calculates the total quantity sold for each product. This reveals the product with the highest sales volume.

**Conclusion:**

This Jupyter Notebook demonstrates the power of pandas for data manipulation, cleaning, and analysis. It showcases techniques for merging data, creating new features, and visualizing trends to gain valuable insights from sales data. 

**Further Exploration:**

* Implement a more robust solution to identify frequently sold products together.
* Analyze factors influencing sales, such as product category, price, and marketing campaigns.
* Explore customer segmentation for targeted marketing strategies.
