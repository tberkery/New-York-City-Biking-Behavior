# New-York-City-Biking-Behavior

# Data Source
[Zip File of Initial Data Files](https://github.com/tberkery/New-York-City-Biking-Behavior/blob/main/NYCDOT_Bicycle_Counts_2017-_East_River_Bridges.zip.zip) | [Website](https://data.cityofnewyork.us/Transportation/Bicycle-Counts-for-East-River-Bridges/gua4-p9wg)

# Introduction and Business Question
New York City is the epitome of a modern metropolis that doesn’t have enough transit capacity. Everyone using a car would cause too much traffic to be on the road. The subway already carries a massive load. As commuters and politicians alike seek alternate options, biking is a fast-rising potential solution to help alleviate the strain on NYC roads and subways with the added benefit of being the greenest option of the three. However, unlike car or public transit travel like the subway, biking is subject to numerous external factors influencing it’s viability. Regardless of whether or not you live in NYC, you should care because what’s happening with transportation capabilities in NYC is a trend across American cities and the green factor of biking is true regardless of location. This leads us to the following business question: how can we better understand biking behavior in cities?

# Data Question
How can we predict biking behavior and understand common biking behavior patterns?

# Results
Regression Results: -4881(weekend) + 365(month) + 416(high temp) - 270(low temp) - 5785(precipitation) + 4145
![alt text](https://github.com/tberkery/New-York-City-Biking-Behavior/blob/main/Total%20Crossings%20vs.%20High%20Temp.png)
![alt text](https://github.com/tberkery/New-York-City-Biking-Behavior/blob/main/Total%20Crossings%20vs.%20Precipitation.png)

Cluster results:
![alt text](https://github.com/tberkery/New-York-City-Biking-Behavior/blob/main/Biking%20Behavior%20Clusters.PNG)
This suggests the three baseline patterns frequently observed for New York City biking are as follows: (1) rainy day on the weekend and fewer-than-average bikers across all bridges, (2) sunny day during the week with significantly above-average biker quantities across all bridges, and (3) sunny day on the weekend with somewhat-more-than-average biker quantities.

# Further Research
-More seasons
-More cities
-Incorporating non-bridge bike routes
-How does car traffic on bridges vary based on number of bikers?
-Driving factors (delivery, commute, recreation) 

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
