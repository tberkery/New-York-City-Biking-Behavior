# Steps for Regression Analysis
1. Use WEEKDAY function to convert date-time format to day of week by number
2. Use MOD function to shift the day of week number to start the week at Saturday 
3. Use MONTH function to extract month number from date-time format
4. Use IF statement to convert trace precipitation entries to 0.01 inches
5. Run a multivariate regression using ToolPak with total crossings as y and day of week, month, precipitation, high temp, low temp as x variables
6. Use IF statement to determine whether day of week is weekend or not. Use 1 for weekend and 0 for weekday to make binary variable
7. Run a multivariate regression using ToolPak with total crossings as y and weekend status, month, precipitation, high temp, low temp as x variables
8. On a scatterplot, graph total crossings vs high temp and total crossings vs precipitation amount
9. Fit a linear trendline to the graphs and determine line of best fit + R-squared value
10. Analyze results

# Steps for Cluster Analysis
1. Duplicate the workbook containing the data fed into the regression.
2. Assign each day in the data set a cluster ID number.
3. Use STANDARDIZE to compute z-scores for the variables in each column for each day in the dataset.
4. Insert 8 columns at the top of the workbook and choose three initial anchor clusters ID numbers.
5. Use VLOOKUP to get the z-scores for each variable in the dataset (i.e. each column header) for the anchor clusters.
6. Use SUMXMY2 to compute the square distance of the z-scores for each variable for every day in the dataset from the z-scores of the respective variables in each anchor cluster.
7. Use the MINIMUM function to identify the minimum square distance relative to the anchor clusters for each day.
8. Use the SUM function to sum the minimum square distance values for all days in the dataset.
9. Use the MATCH function to identify which anchor cluster the minimum square distance corresponds to.
10. Using Solver, set the objective to be minimizing the cell you just created in the prior step.
11. Using Solver, set the cells containing the anchor cluster ID numbers created in step 4 to be the variable cells that Solver will change.
12. Using Solver, set the constraints that the cluster ID number must be between 1 and 214 and be a valid integer. Uncheck the option of making unconstrained variables non-negative.
13. Using Solver, select the "Evolutionary" solver option and set the mutation rate to 0.5
14. Run Solver and interpret your results, making use of conditional formatting to make tables and visuals more readable and intuitive.
