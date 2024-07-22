# Using SparkSQL to analyze large data sets

# Data prep

- Imported the tools needed for the analysis.  
- Created a Spark session to enable the work.  
- Read the AWS data file and formatted in a dataframe.  

# Using a temp view

- Created a temp view to improve processing time of the large data set.  
- Created 4 SQL queries to answer the following questions:  
    - What is the average price for a four-bedroom house sold for each year? Round off your answer to two decimal places.  
    - What is the average price of a home for each year the home was built, that has three bedrooms and three bathrooms? Round off your answer to two decimal places.  
    - What is the average price of a home for each year the home was built, that has three bedrooms, three bathrooms, two floors, and is greater than or equal to 2,000 square feet? Round off your answer to two decimal places.  
    - What is the average price of a home per "view" rating having an average home price greater than or equal to $350,000? Determine the run time for this query, and round off your answer to two decimal places.  

![image](https://github.com/user-attachments/assets/d3226573-d135-4d66-accf-235a2992a87e)

![image](https://github.com/user-attachments/assets/142fec24-1ac2-4640-b5a5-baaf02667679)


# Compare options to decrease run time

Ran the same query 3 different ways to view differences in run time.  
Added a run time calculation for the 4th query above.  
    -Time: 1.2482097148895264 seconds      
Cached the temporary table and verified.  
    -Time: 0.529306173324585 seconds      
-Partitioned the data.  
    -Time: 0.9826006889343262 seconds  

# Conclusion

We can see that caching the temporary table significantly decreased the run time. The cached data set ran in less than half the time of the uncached query.  
The expectation was that partitioning the data would further increase the speed of the query but that wasn't true in this case. 
Possible reasons:  
    -Small data set (33,000 rows)  
    -Data was partitioned on 'date built' but the was grouping by views and filtering by price.  

Note that each time I've run the 3 test queries, the run time has been slightly different. My analysis is based on the output at the time I saved the notebook and downloaded it from collab. If the queries are run again, the time notations above will be different.  
