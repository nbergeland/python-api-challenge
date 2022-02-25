# python-api-challenge
WeatherPy
Note
Instructions have been included for each segment. You do not have to follow them exactly, but they are included to help you think through the steps.
# Dependencies and Setup
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import requests
import time
from scipy.stats import linregress

# Import API key
from api_keys import weather_api_key

# Incorporated citipy to determine city based on latitude and longitude
from citipy import citipy

# Output File (CSV)
output_data_file = "output_data/cities.csv"

# Range of latitudes and longitudes
lat_range = (-90, 90)
lng_range = (-180, 180)
Generate Cities List
# List for holding lat_lngs and cities
lat_lngs = []
cities = []

# Create a set of random lat and lng combinations
lats = np.random.uniform(low=-90.000, high=90.000, size=1500)
lngs = np.random.uniform(low=-180.000, high=180.000, size=1500)
lat_lngs = zip(lats, lngs)

# Identify nearest city for each lat, lng combination
for lat_lng in lat_lngs:
    city = citipy.nearest_city(lat_lng[0], lat_lng[1]).city_name
    
    # If the city is unique, then add it to a our cities list
    if city not in cities:
        cities.append(city)

# Print the city count to confirm sufficient count
len(cities)
613
Perform API Calls
Perform a weather check on each city using a series of successive API calls.
Include a print log of each city as it'sbeing processed (with the city number and city name).
url = "http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=" + weather_api_key + "&q="
weather_list[]

for city in cities:
    city_url = url + city
    try: 
        result = request.get(city_url).json()
        Cloudiness = result["clouds"]["all"]
        Country =
        weather_list.append({"city":city,"Cloudiness":Cloudiness})
    except:
        print("City not found!")
  File "<ipython-input-12-07a9204a566b>", line 1
    weather_list[]
                 ^
SyntaxError: invalid syntax
 
Convert Raw Data to DataFrame
Export the city data into a .csv.
Display the DataFrame
 
City          535
Cloudiness    535
Country       535
Date          535
Humidity      535
Lat           535
Lng           535
Max Temp      535
Wind Speed    535
dtype: int64
 
City	Cloudiness	Country	Date	Humidity	Lat	Lng	Max Temp	Wind Speed
0	severo-kurilsk	92	RU	1534988024	93	50.68	156.12	54.27	2.73
1	darhan	8	MN	1534988024	71	49.49	105.92	72.81	8.55
2	tarakan	48	ID	1534988024	100	3.30	117.63	80.10	4.41
3	komsomolskiy	48	RU	1534987754	72	67.55	63.78	54.46	15.46
4	souillac	0	FR	1534986000	73	45.60	-0.60	71.60	3.36
Plotting the Data
Use proper labeling of the plots using plot titles (including date of analysis) and axes labels.
Save the plotted figures as .pngs.
Latitude vs. Temperature Plot
 

Latitude vs. Humidity Plot
 

Latitude vs. Cloudiness Plot
 

Latitude vs. Wind Speed Plot
 

Linear Regression
# OPTIONAL: Create a function to create Linear Regression plots
# Create Northern and Southern Hemisphere DataFrames
Northern Hemisphere - Max Temp vs. Latitude Linear Regression
 
The r-squared is: -0.8151657406810827

Southern Hemisphere - Max Temp vs. Latitude Linear Regression
 
The r-squared is: 0.760263355051646

Northern Hemisphere - Humidity (%) vs. Latitude Linear Regression
 
The r-squared is: 0.10358336015746494

Southern Hemisphere - Humidity (%) vs. Latitude Linear Regression
 
The r-squared is: 0.14689473425583055

Northern Hemisphere - Cloudiness (%) vs. Latitude Linear Regression
 
The r-squared is: -0.08733547918934018

Southern Hemisphere - Cloudiness (%) vs. Latitude Linear Regression
 
The r-squared is: 0.21881426893991618

Northern Hemisphere - Wind Speed (mph) vs. Latitude Linear Regression
 
The r-squared is: 0.1071382774388479

Southern Hemisphere - Wind Speed (mph) vs. Latitude Linear Regression
 
The r-squared is: -0.322483077139538

 
