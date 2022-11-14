# 
Tyrone Fraley
UC Berkley Extension
August 31, 2022

## Overview of the Analysis
Working at Pyber - a Python-based ridesharing app company worth $2.3 billion. I recieved a task to perform an analysis on rideshare data. In addition, the CEO, V. Isualize has asked for comprehensive ride share data in our January to early May 2019 rural, urban, and subruban city territories. V. Isualize and the other stake holders want to make critical decisions around which cities need more support. 

To properly vizualize the data I wrote Python scrips using Pandas libraries, Jupyter Notebook, and Matplotlib. This way charts could display the correlation between the different types of cities, rides, and fares. By collecting, calculating, and amalgamating the ride sharing/city data into a data frame. All collected data was then presented in a line graph. 

To combine the ride sharing data and the city data I used pandas merge function (pyber_data_df = pd.merge(ride_data_df, city_data_df, how="left", on=["city", "city"]). This allowed me to carefully parse my merged data frames into not only one data set, but organize my data as well. The data frame at this point was more readable at this point with "city" as the first column and "type" as the final column. This data frame was adjusted throughout the analysis to make the data more user friendly. 

To collect the total rides for each city .groupby("type").count().ride_id was used. This function returned the total rides for each city type. The rides were presented as an integer (int64). 

The total drivers for each city type was grouped within the data frame by type of city and sum of all drivers (.groupby("type").sum().driver_count). Which allowed me to analyze the total amount of drivers for each city. In turn the utilized function within the data set returned integers (int64).

The total fares for each city was placed organized within the data frame through the groupby method (.groupby("type").sum().fare). This function allowed me to collect all of the total fares for each city type and organize them from least to greatest. Considering the totals for the fares included decimial points they were presented as floating numbers (float64) within the data frame. 

The average fare per ride for each city used the groupby method as well. However, in this instance I had to utilize a measure of central tendency (average) within the function (.groupby("type").mean().fare). Thankfully, this function returned the average for each city as a floating number within the data set. 

To obtain the average fare per driver for each city type the methods within the function were similar to that of the average fare per ride for each city. However, in this instance it was vital to use .sum and divide the fare by total city drivers (.groupby("type").sum().fare/total_city_drivers).

At this point in the analysis I organized the data frame with a dicitionary function to reflect the data in the following order: total rides, total drivers, total fares, average fare per ride, and average fare per driver. This was an essential step in the evolution of the ride share data frame because the more organized the data is the more readable it is. 

Cleaning up the data frame (df.index.name = Name) and formating columns was a necessary next step in the analysis process before moving onto merging data frames again before creating a line plot. TO format the columns the data frame included the column name and formatting functions (pyber_summary_df["Total Rides"] = pyber_summary_df["Total Rides"].map("{:,}".format)). Before creating the multiple line plot the data frame is observed through the .head() function to ensure the data frame was formatted properly. At this point it was importanat to create a new data frame and include dates within the data frame (.groupby(["type", "date"]).sum()["fare"]). The data frame was then placed ina pivot table ((index="date", columns="type", values="fare")) where I could identify dates, fares, and city types. Moving further into the analysis another data frame was created with the "resample()" function to observe the sum of the fares per week (.resample("W").sum()). Finally, by using matplotlib the dataframe could now be placed into a multiple line chart. Plotting the x and ylabels, initiating a style (style.use('fivethirtyeight), plotting the title, and saving the multiple line chart was the final step in the analysis.




### Results

The ride sharing data for each city type produced interesting results. For rural cities there were 125 total rides, 78 total drivers, and $4,327.93 in total fares. The average fare for rural cities was $34.62 and teh average fare per driver was $55.49. For the suburban cities there were 625 total rides, 490 total driverss, and $19,356.33 total fares. The average fare per ride for subruban areas was $30.97 and the average fare per driver was $39.50. Finally, for the urban cities there were 1,625 total rides, 2,405 total drivers, and $39,854.38 total fares. The urban cities also had $24.53 in average fares per ride and $16.57 for average fares per driver. 

## Summary

There is a statement summarizing three business recommendations to the CEO for addressing any disparities among the city types.

The ride sharing data analysis project provided interesting results for each city. Knowing that rural city urban cities hold more total rides than the suburban and rural cities comes down to population sizes. It would be important in the future to focus heavily on promotions within the urban cities to boost ride sales. Currently, the average fare for urban cities is $24.53. Special promotions could include $5 off for rides on certain dates. Especially, when considering that the highest fares for urban rides were between late February and early March this may be a good time to offer promotions to keep consumers interested in booking rides. 

Suburban cities had an average ride fare of $30.97. Knowing that suburban cities ranked second in for most rides in the analysis they still had a higher average ride fare than urban rides. Suburban cities could definitely benefit from not only promotions similar to rural cities, but also lower driver fares. Driver fares for urban cities on average were $7.96 lower than the average ride fare in urban cities. However, when it comes to suburban cities the driver fares were $8.53 cents more expensive than the average fare per ride. Projections would be needed to be made in this case to anticipate how a reduction in driver fares for suburban areas would affect the business. However, it should also be noted that suburban cities had different results in rises and falls in fares than rural cities. Fares for suburban cities rose in mid January, late February, and late April. Competitive marketing promotions could possibly gain more customers if the promotions targeted suburbuan cities during those times of the first six months of the year. A disruptive marketing campaign might be useful in this situation to stimulate consumer interest.

The final results for the rural areas came with the most unfavorable results amongst the entire data set. However, without knowing population sizes it is tough to say if there was a low performance in urban areas. Once population sizes for each city can be determined then we can compare results at a ratio level to see if rural cities are really an outlier within our market footprint. When observing average fare per ride ($34.62) and average fare per driver ($55.49). Like the suburban cities the rural cities' average fare per driver was higher than that of it's fares per ride. This means that the average fare per driver is $20.87 higher than the average fare per ride. Adressing this major gap through pricing structures could greatly assist in producing more drivers and reducing the costs for rides could increase sales. However, competitive rates have to be analyzed for urban areas at this point to ensure we are performing within the margins of our market's average rates for rural areas. Rural cities saw the highest fares in late February and throughout April. However, it should be noted that in the month of March that the fares were volatile in that they would drop and rise week by week. Such rises and falls in fares within a single month could upset customers. 

References:

Teague, K. (2019). Google Maps [Photograph]. https://www.cnet.com/tech/services-and-software/use-google-maps-to-see-how-fast-youre-driving/
