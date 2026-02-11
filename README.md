## Retail Sales Dataset: Comprehensive Exploratory Data Analysis (EDA) Description

This EDA provides a comprehensive analysis of the retail sales dataset, covering data integrity, distribution, temporal patterns, performance metrics, and the impact of promotions and pricing.

### 1. Setup and Data Loading
-   **Libraries**: Imports essential libraries including `pandas` for data manipulation, `seaborn` and `matplotlib.pyplot` for visualization, `numpy` for numerical operations, and `warnings` to manage warnings.
-   **Plot Style**: Configures `matplotlib` and `seaborn` for readable, report-quality visuals with a specific color palette.
-   **Data Ingestion**: Loads the `retail_sales.csv` file.
-   **Data Type Assignment**: Explicitly sets data types for columns like `store_id`, `item_id` (category), `sales` (int32), `price`, `promo`, and `weekday` (float32 to handle potential NA values), and `month` (int8).
-   **Date Parsing**: Parses the `date` column into datetime objects.
-   **Derived Fields**: Creates new columns for analysis:
    -   `year`: Extracts the year from the `date` column.
    -   `day_name`: Extracts the day of the week name as an ordered categorical variable.
    -   `is_weekend`: A binary indicator (0 or 1) for weekend days.
-   **Memory Usage**: Reports the memory footprint of the DataFrame after loading and initial processing.

### 2. Dataset Overview
-   **Summary Metrics**: Provides key statistics about the dataset:
    -   Total number of rows and columns.
    -   Date range (minimum and maximum dates).
    -   Number of distinct days, stores, and items.
    -   Calculated total number of possible store-item combinations.

### 3. Data Quality Checks
-   **Integrity Validation**: Performs checks to ensure data cleanliness and completeness:
    -   `missing_values_total`: Sum of all missing values across the DataFrame.
    -   `duplicate_store_item_date_rows`: Counts rows with identical `date`, `store_id`, and `item_id` combinations.
    -   `invalid_promo_values`: Checks if `promo` values are strictly 0 or 1.
    -   `negative_sales_rows`: Identifies records with sales less than zero.
    -   `non_positive_price_rows`: Detects records where price is less than or equal to zero.
    -   `weekday_mismatch_with_date`: Verifies consistency between the `date`'s actual weekday and the `weekday` column.
    -   `month_mismatch_with_date`: Verifies consistency between the `date`'s actual month and the `month` column.
    -   **Grid Completeness**: Compares the actual number of rows to the expected number of rows for a full store-item-day grid, indicating any missing combinations.

### 4. Descriptive Statistics
-   **Numerical Summaries**: Generates descriptive statistics (count, mean, std, min, percentiles, max) for `sales` and `price`.
-   **Distributions**: Visualizes the distributions of daily sales and price using histograms to show their patterns and ranges.
-   **Promotion Share**: Calculates and visualizes the proportion of observations under promotion versus no promotion using a bar plot.

### 5. Time-Series Patterns
-   **Daily Sales Trend**: Aggregates daily total sales and computes a 30-day moving average to smooth out fluctuations and highlight long-term trends. Visualized with a line plot.
-   **Monthly Sales Heatmap**: Creates a heatmap of aggregated monthly sales by year, revealing annual and seasonal sales patterns.
-   **Weekly Sales Patterns**: Analyzes average sales by day of the week using a bar plot. Further explores the impact of promotions on average sales across weekdays using a line plot, differentiating between promotional and non-promotional days.

### 6. Store and Item Performance
-   **Store Performance**: Groups data by `store_id` to calculate average sales, total sales, average price, and promotion rate per store. Identifies and visualizes the top 15 stores by average daily sales.
-   **Item Performance**: Similar to store performance, groups data by `item_id` to assess average sales, total sales, average price, and promotion rate per item. Identifies and visualizes the top 15 items by average daily sales.
-   **Demand Variability**: Computes the Coefficient of Variation (CV) for sales across each store-item pair to quantify demand variability. Visualizes the distribution of CVs using a histogram and displays the top 10 store-item pairs with the highest variability.

### 7. Promotions and Pricing Effects
-   **Promotion Impact**: Quantifies the average sales under promotion versus no promotion and calculates the percentage uplift in sales due to promotions. Visualized with a bar plot.
-   **Promo Lift Distribution**: Computes the promotional uplift for each store and visualizes the distribution of this uplift across all stores using a histogram.
-   **Price Decile Analysis**: Divides prices into deciles and analyzes the relationship between mean price within each decile, mean sales, and promotion rate. Visualizes this relationship using a dual-axis line plot.

### 8. Correlation Analysis
-   **Correlation Matrix**: Calculates and visualizes the correlation matrix for numerical features (`sales`, `price`, `promo`, `weekday`, `month`, `is_weekend`) using a heatmap to understand inter-variable relationships.

### 9. Year-over-Year Summary
-   **Annual Trends**: Aggregates data by `year` to analyze annual trends in total sales, average sales, average price, and promotion rates. Visualizes these trends with line plots.

### 10. Auto-Generated Insight Snapshot
-   **Key Insights**: A summary table of key metrics derived from the EDA, including date range, total rows, number of stores and items, promotion share percentage, average daily sales, average price, promotion sales lift percentage, best store/item average sales, and highest store promotion lift percentage.
