# Day-50---Working-with-APIs
As part of a 75-day data analysis challenge, this work on Python covers working of APIs


## Assignment: Weather Data Fetcher
### Objective:

Build a Python script to fetch weather data for a city using the OpenWeatherMap API and display the temperature, weather condition, and humidity.

### Steps:
#### Set up the Environment:

Install the required library: requests.

#### Sign Up for OpenWeatherMap:

Go to OpenWeatherMap and create a free account.
Generate an API key from your account.

#### Write the Script:

Fetch weather data using the requests library.
Parse the JSON response to extract the required information (temperature, weather condition, humidity).
Display the results in a user-friendly format.


import requests

# Function to fetch weather data
def fetch_weather_data(city, api_key):
    try:
        # API endpoint
        url = f"http://api.openweathermap.org/data/2.5/weather?q={city}&appid={api_key}&units=metric"
        
        # Sending a GET request
        response = requests.get(url)
        
        if response.status_code == 200:
            data = response.json()
            
            # Extracting required data
            city_name = data['name']
            temperature = data['main']['temp']
            weather_condition = data['weather'][0]['description']
            humidity = data['main']['humidity']
            
            # Displaying the data
            print(f"Weather in {city_name}:\n")
            print(f"Temperature: {temperature}°C")
            print(f"Condition: {weather_condition.capitalize()}")
            print(f"Humidity: {humidity}%")
        else:
            print(f"Error: Unable to fetch weather data. Status Code: {response.status_code}")
    
    except Exception as e:
        print(f"An error occurred: {e}")

# Main function
if __name__ == "__main__":
    # Input city name
    city = input("Enter the name of the city: ").strip()
    
    # Your OpenWeatherMap API key
    api_key = "your_api_key_here"  # Replace with your API key
    
    # Fetch and display weather data
    fetch_weather_data(city, api_key)
