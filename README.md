# Final-Project-Statistical-Modelling-with-Python

Hello, this is **Tashrif Mahmud** and welcome to my Python Project for Lighthouse Labs!

We will use the CityBikes API to gather bike station data for a selected location(in this project its Toronto city), followed by collecting point of interest (POI) data using the Foursquare and Yelp APIs. All tasks will be performed in Python, including creating an SQLite database. Finally, we will build a DataFrame from the database to conduct regression analysis, exploring whether a relationship exists between the number of bikes at a station and nearby POIs (e.g., bars, restaurants, banks).

## Project/Goals

The main goal of this project is to effectively use Python and APIs to gather meaningful data and perform the desired analysis. To achieve this, we need to ensure the correct use of specific tools and techniques.

* Python functions, modules, and loops are essential for driving the project
* Proper API usage is critical to obtain the necessary data for analysis
* Data storage, joining, and cleaning are important steps throughout the project
* SQL will be used to create the required database
* Exploratory Data Analysis (EDA) will be performed to assess data quality
* Finally, statistical tools will help analyze and interpret the data using a regression model.

There are 4 notebooks in this project and some additional data in data folder:
* **Part 1:** In **city_bikes.ipynb**, we connect to the CityBikes API to retrieve bike station data (name, latitude, longitude, number of bikes) for a chosen city, then convert the API response into a PD DataFrame for analysis.
* **Part 2:** In **yelp_foursquare_EDA.ipynb**, we connect to the Foursquare and Yelp APIs to retrieve information on restaurants, bars, and banks near bike stations from Part 1. We then create DataFrames for the results and compare the coverage and completeness of the data from both APIs.
* **Part 3:** In **joining_data.ipynb**, we join the bike station data from Part 1 with the POI data from Part 2 into a new dataframe. We use data visualization to explore the combined dataset, then create an SQLite database to store the collected POI data, ensuring the database is properly structured and validated.
* **Part 4:** In **model_building.ipynb**, we build a regression model using Python’s statsmodels module to analyze the relationship between the number of bikes at a station and nearby POIs. We interpret the model's results and derive insights.
* In the data folder you will find various .csv and .pkl files alongside **stations_institutions.db** database file, which we use in Part 4.

With these goals and overall project in mind, we will start this journey!

## Process
* We will be utilizing various python libraries and modules which we will be importing throughout the project
* In Part 1, we start with CityBikes API, we go through the documentation and call the data using the API
* For location, we will choose Toronto, we will also use all the station's location for our Part 2's API call
* We get station names, number of free bikes, bikes in use alongside the latitude and longitude of the station and we save it in our Pandas dataframe
* Then we start with Foursquare and Yelp API. We choose bars, restaturant and banks as our points of interest (POI)
* We use each station's location to get information on our POIs.
* Yelp gives additional information like rating, review count and price. But due to API limitation, we got most number of observations from Foursquare
* We use the Foursquare data, which shows the number of POIs surrounding each of our Bike Stations in Toronto 
* We also conduct some EDA throughout the project to ensure data quality 
* In Part 3, we join the data from Part 1 and Part 2 to make a new dataframe
* We then conduct EDA and put that data in a SQLite3 database, this **stations_institutions.db** can be found in data folder
* In Part 4, we use extensive EDA techniques to further check the quality of the data, also doing some cleaning as necessary 
* We then use statsmodel to create a OLS regression analysis on our data
* Finally, we interpret our results and also look into the possibility of turning our regression model into a classification model 

## Results
* We choose Toronto city as our location, and we got 852 station names and their information using CityBikes API
* Yelp API got the overall higher amount of information per location for our points of interest but the API call limited our capability to explore on it
* Without a choice, we use the data from Foursquare API, and we got 2,101 bars, banks and restaurant information surrounding our Toronto Bike Stations
* We find that out of 852 stations, only 444 stations has establishments in the category of bars, banks and restaurants
* During EDA we find that distribution for total bikes, bank count, bar count and restaurant count all are heavily skewed to the left
* The skewed distribution indicates some stations have very high amount of bikes, as well as high amount of POIs surrounding them, which can be potentially outliers
* We use regressional analysis along with the outliers to find the following results:
> 1. R-squared is 0.016, indicates a weak fit, explaining only 1.6% of the variance in total_bikes.
> 2. F-statistic 2.359 and p-value 0.0710 which suggests the model is not statistically significant at the 0.05 level, although it approaches significance.
> 3. Coef of bank_count is 0.8951 with a significant p value of 0.011 means each additional bank is associated with approximately 0.895 more bikes.
> 4. Coef of bar_count is -0.1903 and restaurant_count is 0.0459, which is not significant, indicating no meaningful impact on bike counts.
* Overall, the model suggests a weak relationship between bike numbers and nearby POIs, with only bank_count showing a significant positive effect.

## Challenges 
The limit on API call can be a major challenge as it can limit the quality and quantity of the data. Data with many outliers can distort the result.

## Future Goals
In the future, I would like to run different regression models on different variables, and answer questions like: How does the rating and review count of extablishment affect on how many bike stations are near it?
