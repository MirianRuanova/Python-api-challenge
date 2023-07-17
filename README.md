# Python-api-challenge

## Background
What is the weather like as we approach the equator?"

Now, we know what you may be thinking: “That’s obvious. It gets hotter.” But, if pressed for more information, how would you prove that?

# Part 1: WeatherPy

This project involves analyzing weather data retrieved from the OpenWeatherMap API. It includes generating random geographic coordinates, fetching weather data for cities based on the coordinates, creating scatter plots to visualize relationships between weather variables and latitude, and computing linear regression for each relationship.

## Prerequisites

Before running the code, make sure you have the following dependencies installed:

- `matplotlib.pyplot`
- `pandas`
- `numpy`
- `requests`
- `time`
- `scipy.stats.linregress`
- The OpenWeatherMap API key stored in the `weather_api_key` variable.
- The Citipy library installed.

## Step 1: Generating Random Geographic Coordinates and City List

The starter code generates random latitude and longitude combinations and uses the Citipy library to identify the nearest city for each coordinate pair. The resulting cities are stored in a list called `cities`.

## Step 2: Retrieving Weather Data

In this step, the OpenWeatherMap API is utilized to retrieve weather data for each city in the `cities` list. The code loops through the cities and makes API requests to fetch weather information. The retrieved data, including latitude, longitude, temperature, humidity, cloudiness, wind speed, country, and date, is appended to the `city_data` list.

## Step 3: Creating the City Data DataFrame

The `city_data` list is converted into a Pandas DataFrame called `city_data_df`. The DataFrame provides a structured representation of the weather data for further analysis.

## Step 4: Scatter Plots

Several scatter plots are created to visualize the relationships between weather variables and latitude. The scatter plots include:

- Latitude vs. Temperature
- Latitude vs. Humidity
- Latitude vs. Cloudiness
- Latitude vs. Wind Speed

Each plot is generated using the `plt.scatter()` function, and appropriate titles, labels, and gridlines are incorporated. The plots are saved as PNG images.

## Step 5: Linear Regression

The code defines a function called `create_linear_regression_plot()` to create linear regression plots. This function takes the x-axis data, y-axis data, x-axis label, y-axis label, and plot title as parameters. The function performs linear regression using `linregress()` from `scipy.stats`, calculates the regression values, and plots the scatter plot along with the regression line. The r-value and linear regression equation are printed for each plot.

The linear regression plots are generated for the following relationships:

- Max Temperature vs. Latitude in the Northern Hemisphere
- Humidity vs. Latitude in the Northern Hemisphere
- Cloudiness vs. Latitude in the Northern Hemisphere
- Wind Speed vs. Latitude in the Northern Hemisphere

## Part 2


# VacationPy

This project involves analyzing weather data to identify ideal vacation destinations. It includes creating maps, filtering data based on weather conditions, and finding nearby hotels using the Geoapify API.

## Prerequisites

Before running the code, make sure you have the following dependencies installed:

- `hvplot.pandas`
- `pandas`
- `requests`

Additionally, you need to obtain an API key for the Geoapify API and store it in the `geoapify_key` variable.

## Step 1: Creating a Map

The first step involves creating a map that displays a point for every city in the `city_data_df` DataFrame. The size of the point represents the humidity in each city. The map is generated using the `hvplot.points()` function with the specified parameters.

## Step 2: Narrowing Down the Data

In this step, the `city_data_df` DataFrame is filtered to find cities that meet specific weather conditions. The code filters cities with a maximum temperature lower than 27 degrees and wind speed less than 4.5 m/s. Null values are dropped from the resulting DataFrame.

## Step 3: Creating the Hotel DataFrame

A new DataFrame called `hotel_df` is created using the `copy()` function on the relevant columns of the `city_data_df` DataFrame. An empty column called "Hotel Name" is added to store hotel information obtained from the Geoapify API.

## Step 4: Finding Nearby Hotels

Using the Geoapify API, the code iterates through the `hotel_df` DataFrame to find the nearest hotel within 10,000 meters of each city's coordinates. The latitude and longitude values are obtained from the DataFrame, and a request is made to the Geoapify API with the appropriate parameters. The API response is then converted to JSON format, and the hotel name is extracted and stored in the "Hotel Name" column of the `hotel_df` DataFrame.

## Final Map Display

Finally, a map is generated to display the cities along with the hotel names. The `hvplot.points()` function is used with the `hover_cols` parameter to include the city name, country, and hotel name in the hover message for each city.

