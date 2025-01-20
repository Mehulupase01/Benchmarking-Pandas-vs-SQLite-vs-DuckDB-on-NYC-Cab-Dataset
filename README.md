# Benchmarking Pandas vs SQLite vs DuckDB on NYC Cab Dataset
 This project compares the performance of three data-processing systems—Pandas, SQLite, and DuckDB—on the NYC Cab dataset (2016). The comparison includes data loading, counting distinct values, grouping by day and hour, and machine learning tasks like fare estimation. DuckDB outperforms both Pandas and SQLite, particularly in complex queries and large datasets

## Task / Problem Statement  
The goal of this project is to compare the performance of Pandas, SQLite, and DuckDB on various tasks, such as loading data, executing queries, and performing machine learning tasks like fare estimation. The performance differences between these systems are analyzed based on execution times for each task.

## Sub-Tasks  
1. **Data Loading**: Load the NYC Cab dataset into Pandas, SQLite, and DuckDB.  
2. **Query 1 - Counting Distinct Values**: Compare the performance of counting distinct values across all three systems.  
3. **Query 2 - Grouping by Day and Hour**: Implement and compare the performance of a grouping operation across all three systems.  
4. **Machine Learning - Fare Estimation**: Implement a regression model to predict fare costs and compare the performance of Pandas, SQLite, and DuckDB.

## Implementation Details  
### 1. **Data Loading**  
   - **DuckDB**: Native support for Parquet files led to fast data loading without the need for conversions.
   - **Pandas**: Loaded data using its built-in functions.
   - **SQLite**: Data was loaded into SQLite with custom scripts, but slower than DuckDB due to its row-based storage.

### 2. **Query 1 - Counting Distinct Values**  
   - Task: Count distinct values in a dataset column.  
   - **Pandas**: Execution time: 6.34 seconds.  
   - **SQLite**: Execution time: 64.07 seconds.  
   - **DuckDB**: Execution time: 1.93 seconds.  
   - **Analysis**: DuckDB performed the fastest, followed by Pandas. SQLite struggled due to its row-based storage format.

### 3. **Query 2 - Grouping by Day and Hour**  
   - Task: Group data by day and hour for aggregation.  
   - **Pandas**: Execution time: 0.99 seconds.  
   - **SQLite**: Execution time: 22.10 seconds.  
   - **DuckDB**: Execution time: 0.04 seconds.  
   - **Analysis**: DuckDB was significantly faster than both Pandas and SQLite, showcasing its strengths for OLAP queries.

### 4. **Machine Learning - Fare Estimation**  
   - Task: Implement a regression model (linear regression) to predict fare costs.  
   - **Pandas**: Execution time: 1.33 seconds (Alpha: 4.6516, Beta: 2.6614).  
   - **SQLite**: Execution time: 8.30 seconds (Alpha: 4.6516, Beta: 2.6614).  
   - **DuckDB**: Execution time: 0.02 seconds (Alpha: 4.6516, Beta: 2.6614).  
   - **Analysis**: DuckDB was the fastest due to its optimized support for machine learning functions. SQLite was much slower, as it does not natively support advanced statistical operations.

## Metrics and Results

### **Execution Time per Task**

| Task                          | Pandas (s)   | SQLite (s)   | DuckDB (s)   |
|-------------------------------|--------------|--------------|--------------|
| Data Loading                   | Fast         | Slow         | Very Fast    |
| Query 1 - Counting Distinct    | 6.34         | 64.07        | 1.93         |
| Query 2 - Grouping by Day/Hour | 0.99         | 22.10        | 0.04         |
| Machine Learning - Fare Estimation | 1.33       | 8.30         | 0.02         |

### **Machine Learning Results**

| System     | Alpha (α) | Beta (β) | Execution Time (s) |
|------------|-----------|----------|--------------------|
| Pandas     | 4.6516    | 2.6614   | 1.33               |
| SQLite     | 4.6516    | 2.6614   | 8.30               |
| DuckDB     | 4.6516    | 2.6614   | 0.02               |

## Conclusion  
DuckDB outperformed both Pandas and SQLite across all tasks, especially for aggregation and machine learning. Its columnar storage format and built-in statistical functions made it particularly efficient for large datasets and complex queries. Pandas performed well for smaller datasets but was slower than DuckDB for larger and more complex operations. SQLite showed limitations, particularly in OLAP-style queries and machine learning tasks.

## Future Work  
- **Extended Scale Testing**: Perform tests on larger datasets to further evaluate the scalability of DuckDB, Pandas, and SQLite.  
- **Parallelization**: Investigate the use of multi-threading or parallel processing to improve the performance of Pandas and SQLite for large queries.  
- **Optimizations**: Explore optimization techniques for SQLite to improve its performance on analytical tasks.

## References  
- **Pandas**: [Pandas Website](https://pandas.pydata.org/)  
- **SQLite**: [SQLite Website](https://www.sqlite.org/index.html)  
- **DuckDB**: [DuckDB Website](https://duckdb.org/)  
- **NYC Cab Dataset**: [NYC TLC Data](https://www1.nyc.gov/site/tlc/about/tlc-trip-record-data.page)

