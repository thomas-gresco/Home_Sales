# Home Sales Analysis with PySpark

This repository contains a PySpark script for analyzing home sales data. The script performs various SQL queries on the data to answer specific questions and demonstrates the use of caching and Parquet file storage for optimized data processing.

## Prerequisites

Before running the script, ensure that you have the following prerequisites installed:

- Python (3.7+)
- Apache Spark
- PySpark
- Jupyter Notebook (optional for running in a Jupyter environment)

## Script Overview

1. **Importing Libraries and Initializing Spark**  
   The script starts by importing the necessary libraries and initializing a Spark session.

2. **Reading Data from AWS S3**  
   It reads home sales data from an AWS S3 bucket into a PySpark DataFrame and creates a temporary view.

3. **Analyzing Home Prices**

   3.1. **Average Price for Four-Bedroom Houses**  
   The script calculates the average price for four-bedroom houses sold in each year, rounded to two decimal places.

   3.2. **Average Price of Homes by Year Built (3 Bedrooms, 3 Bathrooms)**  
   It calculates the average price of homes for each year they were built, considering only those with 3 bedrooms and 3 bathrooms, rounded to two decimal places.

   3.3. **Average Price of Homes by Year Built (3 Bedrooms, 3 Bathrooms, 2 Floors, >= 2000 sqft)**  
   This query calculates the average price of homes by year built, considering homes with 3 bedrooms, 3 bathrooms, 2 floors, and a minimum of 2000 sqft of living space, rounded to two decimal places.

   3.4. **Average Price of Homes with a View (Runtime Measurement)**  
   It calculates the average price of homes with a view rating, rounding to two decimal places. The script also measures the runtime for this query.

4. **Caching Data**  
   The script caches the temporary table `home_sales` for optimized querying.

5. **Querying Cached Data**  
   It reruns the query for homes with a view rating, using the cached data, and measures the runtime for comparison.

6. **Partitioning and Storing Data in Parquet Format**  
   The script partitions the data by the `date_built` field and stores it in Parquet format.

7. **Querying Parquet Data**  
   It reads the formatted Parquet data, creates a temporary table, and reruns the query for homes with a view rating using the Parquet DataFrame, measuring the runtime.

8. **Uncaching Data**  
   The script unloads the cached `home_sales` temporary table.

## Conclusion

This PySpark script demonstrates various data analysis tasks on home sales data, including SQL queries, caching, and Parquet file storage. It provides insights into average home prices based on different criteria and compares query runtimes with and without caching.
