# Home_Sales

![Home_sales](https://github.com/s0uravk/Home_Sales/assets/144293972/df119c39-e0aa-4501-8932-6936c88e4b05)

## Introduction
In this challenge, I used SparkSQL to determine key metrics about home sales data. Then used Spark to create temporary views, partition the data, cache and uncache a temporary table, and verify that the table has been uncached. It also highlights the use of temporary views, partition of data, caching the temporary view to optimize the queries to reduce runtime.

## Workflow
1. Imported the necessary PySpark SQL functions for this assignment.
2. Read the home_sales_revised.csv data into a Spark DataFrame.
3. Created a temporary table called home_sales.
4. Answered the following questions using SparkSQL:
  * What is the average price for a four-bedroom house sold for each year? Round off your answer to two decimal places.
  * What is the average price of a home for each year the home was built, that has three bedrooms and three bathrooms? Round off your answer to two decimal places.
  * What is the average price of a home for each year the home was built, that has three bedrooms, three bathrooms, two floors, and is greater than or equal to 2,000 square feet? Round off your answer to two decimal places.
  * What is the average price of a home per "view" rating having an average home price greater than or equal to $350,000? Determine the run time for this query, and round off your answer to two decimal places.
5. Cached the temporary table home_sales to optimize the runtime.
6. Checked if the temporary table was cached.
7. Using the cached data, ran the last query that calculated the average price of a home per "view" rating having an average home price greater than or equal to $350,000. The runtime reduced by half as compared to uncached runtime as the data was read from the cache memory.
8. Partitioned by the "date_built" field on the formatted parquet home sales data.
9. Created a temporary table for the parquet data.
10. Ran the last query that calculated the average price of a home per "view" rating having an average home price greater than or equal to $350,000. The runtime was more as compared to uncached runtime, reason being the query was aggregating the output by 'view' column while we partitioned the data by 'date_built', hence the Spark had to shuffle the data to get the desired output. Data should be partitioned by the column that would be frequently used for aggregating to optimize the runtime.
11. Uncached the home_sales temporary table.
12. Verifed that the home_sales temporary table is uncached using PySpark.
