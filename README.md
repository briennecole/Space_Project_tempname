# Spacex Launch Project

![spacex2](https://user-images.githubusercontent.com/75045133/111883300-af4b6700-8977-11eb-855d-d0a18e29fa94.jpg)

## Team Members:
- Elizabeth Sanchez
- Henry Deane
- Brienne Cole

## Project Objective
Combine data from SpaceX and weather api's to forecast weather info on upcoming launch date/location.

## Data Sources and Extraction
- SpaceX API (no api key required) https://docs.spacexdata.com/#bc65ba60-decf-4289-bb04-4ca9df01b9c1
- Weatherbit API (api key stored in config.py file) https://www.weatherbit.io/api

#### DataFrame 1 (space_df)
For our eventual app that could be used to view a 16 day weather forecast for upcoming launches, our team first used the Spacex API to pull in data on all launches in JSON. (*Note* Wanting only, future launches for this project, we first attempted to use the field "upcoming=True" to filter to exclude past launches but we found that field to be inaccurate). 
url = "https://api.spacexdata.com/v4/launches/upcoming"

#### DataFrame 2 (pads_df)
The first request only returned the unique identifiers for the launch pads but we needed the lat and long coordinates to pull the corresponding weather data. So we did a second request using the launch pad ID to pull the lat and long coordinates into our (pads_df) dataframe.
url_b="https://api.spacexdata.com/v4/launchpads"

#### DataFrame 3 (launch_location)
From the two dataframes, we merged them into a combined dataframe on launchpad_id called launch_location.

Once we had our combined launch_location dataframe, we applied the following data cleaning steps:
- split date and time into two separate columns using a string split
- rounded lat and long coordinates to 2 decimals

#### DataFrame 4 (weather_df)
Next, we passed the latitude and longitude fields from the extracted SpaceX data into the Weatherbit API to return weather data for the 13 launches to create a third pandas dataframe (weather_df).
weath_url="http://api.weatherbit.io/v2.0/forecast/daily?key=api_key&lat=28.561857&lon=-80.577366"

#### DataFrame 5 (launch_location_weather)
Merged weather_df and launch_location to create our 5th and final dataframe (launch_location_weather). 

Applied the following cleaning steps to launch_location_weather:
- dropped duplicates
- reset index

## MongoDB Creation 
Using an iterrows function in a for loop, we imported the 224 unique data rows into a mongo database called spacex_launch_db. The collection titled launches successfully imported and displays 224 individual documents.
