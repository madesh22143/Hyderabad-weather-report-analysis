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
Key Analyses Performed
Monthly Temperature Trends

Line plots of max and min temperatures by month

Rainfall Patterns

Total monthly rainfall

Identification of monsoon months

Humidity vs Temperature Correlation

Heatmap or scatter plot analysis

Wind Speed Insights (if data available)

Average wind speed by season

Stormy day identification

Air Quality Assessment (if data available)

AQI trends

Days exceeding safe AQI limits

Extreme Weather Detection

Days > 40°C or < 10°C

Sudden outlier events

🌟 Project Highlights
Accessed real weather data from public APIs

Cleaned and wrangled data using pandas

Created visualizations with seaborn, matplotlib, and plotly

Generated insights for residents, city planners, and travelers

📄 Output Files
hyderabad_weather_api.csv – Cleaned weather dataset

weather_analysis_plots.png / HTML – Graphs and plots

weather_report_summary.txt or Notebook – Key findings

🚀 Next Steps
Automate data updates with scheduled Python script

Implement backup scraping if API fails

Build an interactive dashboard using Plotly Dash or Streamlit

Extend project to include weather forecasting (e.g., regression models)

📈 Sample Python Analysis Code
python
Copy
Edit
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Load dataset
df = pd.read_csv('hyderabad_weather_api.csv', parse_dates=['date'])
df['month'] = df['date'].dt.month

# Plot temperature trends
plt.figure(figsize=(12, 6))
sns.lineplot(x='month', y='temperature_max', data=df, label='Max Temp')
sns.lineplot(x='month', y='temperature_min', data=df, label='Min Temp')

plt.title('Monthly Temperature Trends in Hyderabad')
plt.xlabel('Month')
plt.ylabel('Temperature (°C)')
plt.legend()
plt.grid(True)
plt.tight_layout()
plt.savefig('weather_analysis_plots.png')
plt.show()
