# plp-weather-project
import requests

def get_weather(city_name, api_key):
    base_url = "http://api.openweathermap.org/data/2.5/weather?"
    complete_url = base_url + "q=" + city_name + "&appid=" + api_key + "&units=metric
    response = requests.get(complete_url)
    data = response.json()
    if data["cod"] == 200:
        main_data = data["main"]
        weather_data = data["weather"][0
        temperature = main_data["temp"]
        pressure = main_data["pressure"]
        humidity = main_data["humidity"]
        description = weather_data["description"]
        print(f"Weather in {city_name}:")
        print(f"Temperature: {temperature}°C")
        print(f"Pressure: {pressure} hPa")
        print(f"Humidity: {humidity}%")
        print(f"Weather description: {description.capitalize()}")
    else:
        print("City not found or an error occurred.")

def main():
    city_name = input("Enter the city name: ")
    api_key = "YOUR_API_KEY"  # Replace with your own API key
    get_weather(city_name, api_key)

if __name__ == "__main__":
    main()
