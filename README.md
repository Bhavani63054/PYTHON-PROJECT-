# PYTHON-PROJECT
import requests

def get_weather(api_key, city):
    base_url = "http://api.openweathermap.org/data/2.5/weather"
    params = {"q": city, "appid": api_key, "units": "metric"}

    response = requests.get(base_url, params=params)

    if response.status_code == 200:
        data = response.json()
        print(f"Weather in {city}:")
        print(f"Temperature: {data['main']['temp']}°C")
        print(f"Humidity: {data['main']['humidity']}%")
        print(f"Description: {data['weather'][0]['description']}")
    else:
        print(f"Failed to retrieve weather data. Status code: {response.status_code}")

if __name__ == "__main__":
    # Replace 'your_api_key' with your actual OpenWeatherMap API key
    api_key = "your_api_key"
    city = input("Enter city name: ")
    
    get_weather(api_key, city)
    
