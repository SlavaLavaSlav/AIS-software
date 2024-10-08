from flask import Flask, render_template
import random  # For simulating sensor data; replace with actual reading code
import requests

app = Flask(__name__)

# Function to read moisture from sensor
def read_moisture():
    # Replace this with actual code to read from GPIO pin
    return random.uniform(0, 30)  # Simulated moisture value

# Function to get weather data from an API
def get_weather():
    api_key = "YOUR_API_KEY"
    city = "YOUR_CITY"
    url = f"http://api.openweathermap.org/data/2.5/weather?q={city}&appid={api_key}&units=metric"
    response = requests.get(url)
    return response.json() if response.status_code == 200 else {}

@app.route('/')
def index():
    moisture = read_moisture()
    weather = get_weather()
    
    moisture_level = ""
    if moisture <= 10.0:
        moisture_level = "Low"
    elif moisture <= 20.0:
        moisture_level = "Medium"
    else:
        moisture_level = "High"

    return render_template('index.html', moisture=moisture, moisture_level=moisture_level, weather=weather)

if __name__ == '__main__':
    app.run(host='0.0.0.0', port=5000)
