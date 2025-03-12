from flask import Flask, render_template, request
import requests

app = Flask(__name__)

# Replace with your OpenWeatherMap API key
API_KEY = '4bebfe350d45998fd96b7d43fcc4e185'
BASE_URL = 'http://api.openweathermap.org/data/2.5/weather'

@app.route('/', methods=['GET', 'POST'])
def index():
    weather_data = None
    if request.method == 'POST':
        city = request.form['city']
        params = {
            'q': city,
            'appid': API_KEY,
            'units': 'metric'  # Use 'imperial' for Fahrenheit
        }
        response = requests.get(BASE_URL, params=params)
        if response.status_code == 200:
            weather_data = response.json()
            print(weather_data)
    return render_template('index.html', weather_data=weather_data)

if __name__ == '__main__':
    app.run(debug=True)
