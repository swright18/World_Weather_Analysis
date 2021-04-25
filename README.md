# World Weather Analysis
## Project Overview
In this project, we will practice your analysis, visualization, and statistical skills by retrieving and analyzing weather data for a hypothetical travel company, PlanMyTrip. 

## Resources
- Data Source: [https://openweathermap.org/api](https://openweathermap.org/api), https://console.cloud.google.com/apis 
- Software: Jupyter Notebook, Pandas Library, CityPy, Python Request, APIs, JSON Traversals

## Summary
In this projects, using API's we generated 2000 random Latitude and Longitude coordinate pairs across the world. We then found the closest city to each of those coordinate pairs. We then retrieved, collected, and cleaned weather data from each city coordinate pair. The weather data was then used to help prospective vacationers find a city and hotel that meet their weather preferences. 
We then added weather description to the weather data. Weather presences were added to identify ideal travel destinations and hotels nearby. Four cities were chosen to create a travel itinerary. Using Google Maps Directions API, a travel route was created between those four cities and a marker layer was added to the map. 

### Retrieving Weather Data
A set of 2000 random Latitude and Longitude coordinates was created. Then a list of cities were created by using the coordinate pairs and finding the nearest city to each pair. By doing this, we found 738 cities. 
![Lat and long](https://user-images.githubusercontent.com/79758494/116000320-504fc200-a5b5-11eb-906c-94a9efc25422.PNG)
An empty list was created to hold weather data and then a loop was created to iterate through all the cities on the list. An API request was run to obtain City, Country, and multiple weather conditions. 
![city data 1](https://user-images.githubusercontent.com/79758494/116000317-504fc200-a5b5-11eb-8367-3a26c0d267c6.PNG)
![City data 2](https://user-images.githubusercontent.com/79758494/116000318-504fc200-a5b5-11eb-8815-cec27bf68112.PNG)
This array of dictionaries was created into a Pandas DataFrame, and then the columns were reordered. Below is the DataFrame created. 
![dataframe](https://user-images.githubusercontent.com/79758494/116000319-504fc200-a5b5-11eb-8cd0-b39ae57ddc7b.PNG)
![reorder](https://user-images.githubusercontent.com/79758494/116000321-50e85880-a5b5-11eb-8247-fcc6decabb08.PNG)

### Creating Travel Destinations Map
By importing the above DataFrame, we asked the customer the minimum and maximum temperature preferences for their vacation. The DataFrame was filtered with those temperature preferences and a new DataFrame was created. 
![1](https://user-images.githubusercontent.com/79758494/116000693-e9330d00-a5b6-11eb-8cf2-26245523c7c8.PNG)
This DataFrame was then cleaned, ensuring there were no empty rows and dropping rows that had any NaN's. That cleaned DataFrame was used to create another DataFrame used to hold hotel names, city name, country, max temp, or coordinates. Using gmap API, hotels were located within 5000 meters of each city. If no hotel was located within 5000 meters, that city was skipped. 
![2](https://user-images.githubusercontent.com/79758494/116000694-e9330d00-a5b6-11eb-8091-7e57f8c21b2e.PNG)
All rows that did not have a Hotel name were dropped. This DataFrame was then saved as a CSV file. 
![3](https://user-images.githubusercontent.com/79758494/116000695-e9330d00-a5b6-11eb-893d-8c97b7e0272d.PNG)
Info box was created and the data from each row of the above dataframe was added to the info boxes. 
![4](https://user-images.githubusercontent.com/79758494/116000740-08ca3580-a5b7-11eb-852f-6c0fa7e80790.PNG)
This produced the map below: 
![WeatherPy_vacation_map(with hotel)](https://user-images.githubusercontent.com/79758494/116000731-02d45480-a5b7-11eb-94c4-1dd2b89f18a8.png)

### Creating a Travel Itinerary Map
Using all the information gathered above, 4 cities were selected to create an Travel Itinerary route. The loc method was utilized to create DataFrames for each of the four cities. The latitude and longitude pairs from each city were found using the "to_numpy" function. 
![1 2](https://user-images.githubusercontent.com/79758494/116001147-bbe75e80-a5b8-11eb-893f-b31a9e329bd8.PNG)
These latitude-longitude pairs were used to create a direction layer map. 
![1 3](https://user-images.githubusercontent.com/79758494/116001145-bb4ec800-a5b8-11eb-9471-dea6c56a1be4.PNG)
The direction layer map for our travel itinerary is below: 
![weather_travel_map](https://user-images.githubusercontent.com/79758494/116001180-d588a600-a5b8-11eb-905a-de12f4f03487.png)
A DataFrame was created using the concat() function, to hold the information for the four cities on the itinerary. 
![1 4](https://user-images.githubusercontent.com/79758494/116001161-c73a8a00-a5b8-11eb-9cef-c61a861eff33.PNG)
Info box was created to display hotel, city, country, weather description and maximum temperature. And a marker layer was created to display this information. 
![1 5](https://user-images.githubusercontent.com/79758494/116001160-c6a1f380-a5b8-11eb-8565-90679fb03f84.PNG)
Below is the resulting map: 
![WeatherPy_travel_map_markers(with hotel)](https://user-images.githubusercontent.com/79758494/116001186-d91c2d00-a5b8-11eb-906e-c5f096e4f43e.png)

### Findings
This project can now be used to filter down specific weather preferences and create itineraries for traveling based on those preferences. 
