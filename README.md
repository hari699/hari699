- 👋 Hi, I’m @hari699
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
hari699/hari699 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->import requests
import json

def get_weather_data(city, date):
    api_url = "https://api.openweathermap.org/data/2.5/weather?q={}&appid=YOUR_API_KEY&dt={}".format(city, date)
    response = requests.get(api_url)
    if response.status_code == 200:
        data = json.loads(response.content)
        return data
    else:
        return None

def main():
    while True:
        print("1. Get weather")
        print("2. Get Wind Speed")
        print("3. Get Pressure")
        print("0. Exit")
        option = int(input("Enter your option: "))
        if option == 1:
            date = input("Enter the date: ")
            data = get_weather_data("London", date)
            if data:
                print("Temp: {} degrees Fahrenheit".format(data["main"]["temp"]))
            else:
                print("No data found for the specified date.")
        elif option == 2:
            date = input("Enter the date: ")
            data = get_weather_data("London", date)
            if data:
                print("Wind Speed: {} miles per hour".format(data["wind"]["speed"]))
            else:
                print("No data found for the specified date.")
        elif option == 3:
            date = input("Enter the date: ")
            data = get_weather_data("London", date)
            if data:
                print("Pressure: {} millibars".format(data["main"]["pressure"]))
            else:
                print("No data found for the specified date.")
        elif option == 0:
            break
        else:
            print("Invalid option.")

if __name__ == "__main__":
    main()

