# spacex_launch_etl_project

### Tried-tested-terrified Team Members:
- Elizabeth Sanchez
- Henry Deane
- Brienne Cole

### Project Objective
Combine data from SpaceX and weather api's to forecast weather info on upcoming launch date/location.

### Data Sources and Extraction
- SpaceX API
- OpenWeatherMap API

For our eventual app that could be used to view a 16 day weather forecast for upcoming launches, our team first used the Spacex API to pull in data on all launches in JSON (*Note* Wanting only, future launches for this project, we first attempted to use the field "upcoming=True" to filter to exclude past launches but we found that field to be inaccurate).

Second, we used the latitude and longitude fields from the extracted Spacex 


-----------------------------------------------------------------------
# NOTES
-----------------------------------------------------------------------
- Tried to use upcoming = true as a filter in the SpaceX API app but we found that it wasn't accurate.
