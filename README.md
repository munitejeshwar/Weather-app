# Build a Weather App using React

# Name: K Muni Tejeshwar

# Date:19/4/25

# Reg no.-212223040102

Objective
Create a simple weather application using React that allows the user to enter a city name and view simulated weather data such as temperature, wind speed, and sky condition.

Task Description
Develop a weather app that:

Accepts a city name from the user

Displays weather information (temperature, wind speed, sky condition) only for predefined cities

Shows an error message for cities not in the mock data

Requirements
React functional component (WeatherApp)

Text input to enter city name

A button or "Enter" key to trigger search

Display of weather data (if city is valid)

Error message for invalid cities

Basic styling using external or inline CSS

# App.js
```
import React, { useState } from 'react';
import './App.css';

const weatherData = {
  hyderabad: { temperature: "32°C", wind: "15 km/h", sky: "Sunny" },
  delhi: { temperature: "28°C", wind: "10 km/h", sky: "Cloudy" },
  mumbai: { temperature: "30°C", wind: "8 km/h", sky: "Humid" },
  chennai: { temperature: "34°C", wind: "12 km/h", sky: "Hot" },
};

function WeatherApp() {
  const [city, setCity] = useState('');
  const [weather, setWeather] = useState(null);
  const [error, setError] = useState('');

  const handleSearch = () => {
    const cityKey = city.toLowerCase();
    if (weatherData[cityKey]) {
      setWeather(weatherData[cityKey]);
      setError('');
    } else {
      setWeather(null);
      setError('City not found in our database.');
    }
  };

  const handleKeyPress = (e) => {
    if (e.key === 'Enter') handleSearch();
  };

  return (
    <div className="app">
      <h1>Weather App</h1>
      <input
        type="text"
        placeholder="Enter city name..."
        value={city}
        onChange={(e) => setCity(e.target.value)}
        onKeyPress={handleKeyPress}
      />
      <button onClick={handleSearch}>Search</button>

      {weather && (
        <div className="weather-info">
          <p><strong>Temperature:</strong> {weather.temperature}</p>
          <p><strong>Wind Speed:</strong> {weather.wind}</p>
          <p><strong>Sky:</strong> {weather.sky}</p>
        </div>
      )}
      {error && <p className="error">{error}</p>}
    </div>
  );
}

export default WeatherApp;
```
# App.css
```
body {
  background-color: #fff7f0;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  color: #9e2b2b;
  margin: 0;
  padding: 0;
}

.app {
  text-align: center;
  padding-top: 70px;
}

h1 {
  font-size: 36px;
  color: #ab009d;
  margin-bottom: 30px;
}

input {
  padding: 12px;
  width: 250px;
  border: 2px solid #ffd6e0;
  background-color: #fff0f6;
  color: #333;
  border-radius: 8px;
  font-size: 16px;
  outline: none;
  transition: border 0.3s ease;
}

input:focus {
  border-color: #ffb6c1;
}

button {
  padding: 12px 18px;
  margin-left: 10px;
  background-color: #92ab57;
  color: #85ac5e;
  border: none;
  border-radius: 8px;
  font-weight: bold;
  font-size: 16px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

button:hover {
  background-color: #61c78c;
}

.weather-info {
  margin-top: 30px;
  background-color: #bf7190;
  display: inline-block;
  padding: 25px 35px;
  border-radius: 12px;
  border: 2px solid #ffccd5;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  font-size: 18px;
}

.error {
  margin-top: 30px;
  color: #ff4d6d;
  font-weight: bold;
}

```
# Output:
![Screenshot 2025-04-19 134509](https://github.com/user-attachments/assets/31df23a7-ef32-4b51-abb9-1ec0fb3b892d)
![Screenshot 2025-04-19 134523](https://github.com/user-attachments/assets/0125fc24-556a-421f-8f23-fbfd2d36f159)
![Screenshot 2025-04-19 134542](https://github.com/user-attachments/assets/ce733647-09b4-4ea8-905b-65d029d58dae)


