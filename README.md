# 🌧️ Hyderabad City Weather Report Analysis

## 📌 Overview
This project focuses on collecting and analyzing weather data for **Hyderabad** using Python. The primary goal is to identify patterns, trends, and anomalies in historical weather data such as temperature, humidity, rainfall, and air quality to understand the local climate.

## 🎯 Objective
To demonstrate skills in:
- Python programming
- Data manipulation
- Open data API access
- Data visualization

---

## 🔢 Python Libraries Used
- `pandas`
- `numpy`
- `matplotlib`
- `seaborn`
- `plotly`
- `requests`

---

## 📚 Sample API Access Script (Open-Meteo)
```python
import requests
import pandas as pd

# Open-Meteo API for Hyderabad Coordinates
url = (
    "https://archive-api.open-meteo.com/v1/archive?latitude=17.3850"
    "&longitude=78.4867&start_date=2024-01-01&end_date=2024-03-31"
    "&daily=temperature_2m_max,temperature_2m_min,precipitation_sum"
    "&timezone=Asia%2FKolkata"
)

response = requests.get(url)
data = response.json()

# Transform to DataFrame
df = pd.DataFrame({
    "date": data["daily"]["time"],
    "temperature_max": data["daily"]["temperature_2m_max"],
    "temperature_min": data["daily"]["temperature_2m_min"],
    "rainfall": data["daily"]["precipitation_sum"]
})

df.to_csv("hyderabad_weather_api.csv", index=False)
print(df.head())
