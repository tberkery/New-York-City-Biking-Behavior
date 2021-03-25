# New-York-City-Biking-Behavior

# Data Source
[Zip File of Initial Data Files](https://github.com/tberkery/New-York-City-Biking-Behavior/blob/main/NYCDOT_Bicycle_Counts_2017-_East_River_Bridges.zip.zip) | [Website](https://data.cityofnewyork.us/Transportation/Bicycle-Counts-for-East-River-Bridges/gua4-p9wg)

# Introduction and Business Question
New York City is the epitome of a modern metropolis that doesn’t have enough transit capacity. Everyone using a car would cause too much traffic to be on the road. The subway already carries a massive load. As commuters and politicians alike seek alternate options, biking is a fast-rising potential solution to help alleviate the strain on NYC roads and subways with the added benefit of being the greenest option of the three. However, unlike car or public transit travel like the subway, biking is subject to numerous external factors influencing it’s viability. Regardless of whether or not you live in NYC, you should care because what’s happening with transportation capabilities in NYC is a trend across American cities and the green factor of biking is true regardless of location. This leads us to the following business question: how can we better understand biking behavior in cities?

# Data Question
How can we predict biking behavior and understand common biking behavior patterns?
We obtained data from the New York City Department of Transportation on total bicycle crossings from April 2017 to October 2017. The data included information about the date, precipitation levels, and corresponding high and low temperatures. In order to assess whether these metrics factor into bicycle crossings we conducted a two part analysis to determine 1) whether we could predict biking behavior and 2) whether there are common biking behavior patterns we can extrapolate from. To predict biking behavior, we ran a multivariate regression with total crossings as the dependent variable. To determine whether there are common biking behavioral patterns, we ran a cluster analysis with three anchors. 

# Results

Regression Results: -4881(weekend) + 365(month) + 416(high temp) - 270(low temp) - 5785(precipitation) + 4145
![alt text](https://github.com/tberkery/New-York-City-Biking-Behavior/blob/main/Total%20Crossings%20vs.%20High%20Temp.png)
![alt text](https://github.com/tberkery/New-York-City-Biking-Behavior/blob/main/Total%20Crossings%20vs.%20Precipitation.png)

Cluster results:
![alt text](https://github.com/tberkery/New-York-City-Biking-Behavior/blob/main/Biking%20Behavior%20Clusters.PNG)

The cluster analysis reveals three common patterns for biking behavior: (1) it's a rainy day filled with precipitation and there are fewer bikers across all bridges, (2) it's a weekday with warm weather and no rain, and the number of bikers on all bridges is above average, and (3) it's a weekend with decent weather and no rain and there is an about average number of bikers on all bridges. Much like the regression analysis, this underscores the importance of whether or not it rains and whether it is a weekend or weekday in determining how many bikers there are on a given day. Relating this back to the business question, this suggests that on rainy weekdaysays city roads and public transit will likely have to carry a heavier load but that on days where there is not problematic weather biking is an extremely effective way to alleviate traffic on roadways and key bridges.

# Further Research
To further build on this project, we would love to integrate more winter data (our dataset's earliest data point is April) to investigate how winter impacts bike-riding behavior. Given biking in the winter is often a problematically cold activity and snow and ice can make biking treacherous, we suspect accounting for winter would significantly upgrade our model's usefulness and predictive power. In addition, we would love to generalize this analysis to more cities. New York City is far from the only city suffering from it's highways being inundated with cars, and it would be worthwhile to explore how biking behaviors are similar or differnt in other dense, hustling cities.

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
