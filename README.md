#  Indian Cities Weather EDA — OpenWeatherMap API

Live weather data fetched for 50 Indian cities, cleaned, analyzed, and clustered to uncover climate patterns across the country.

---

#  Project Overview

This project uses the **OpenWeatherMap API** to collect real-time weather data and perform Exploratory Data Analysis (EDA).

The goal is to move beyond just temperature analysis and understand how atmospheric variables — **humidity, wind speed, pressure, visibility** — interact to shape a city's climate.

**Key question:**
Can we group Indian cities into meaningful climate patterns using weather data alone?

---

#  Project Structure

```
OpenWeather_EDA.ipynb    # Main analysis notebook
weather_api_eda.csv      # Exported dataset (50 cities)
README.md
insights.md              # Key findings and takeaways
```

---

#  Tech Stack

| Tool                 | Purpose                            |
| -------------------- | ---------------------------------- |
| Python               | Core programming language          |
| requests             | API calls to OpenWeatherMap        |
| pandas / numpy       | Data wrangling                     |
| matplotlib / seaborn | Visualizations                     |
| scikit-learn         | StandardScaler + KMeans clustering |

---

#  How to Run

## 1️ Clone the repository

```bash
git clone https://github.com/your-username/OpenWeather-EDA.git
cd OpenWeather-EDA
```

---

## 2️ Install dependencies

```bash
pip install requests pandas numpy matplotlib seaborn scikit-learn
```

---

## 3️ Set your API key

Get a free API key from: [https://openweathermap.org/api](https://openweathermap.org/api)

Then replace in notebook:

```python
api = "REPLACE WITH YOUR API KEY"
```

---

## 4️ Run the notebook

```bash
jupyter notebook OpenWeather_EDA.ipynb
```

---

Note: Live API data means results may vary depending on when you run the notebook.

---

#  Analysis Phases

| Phase | What was done                                      |
| ----- | -------------------------------------------------- |
| 1     | Understood weather variables and relationships     |
| 2     | Tested API with a single city                      |
| 3     | Scaled data collection to 50 cities                |
| 4     | Parsed JSON → structured DataFrame                 |
| 5     | Data cleaning (nulls, duplicates, datatypes)       |
| 6     | EDA (statistics, correlation, distributions)       |
| 7     | Clustering (KMeans) + coastal vs inland comparison |

---

#  Cities Covered

50 Indian cities across metros, Tier-2 cities, coastal cities, and hill stations including:

Mumbai, Delhi, Chennai, Bengaluru, Kolkata, Hyderabad, Pune, Jaipur, Ahmedabad, Lucknow, Srinagar, Shimla, Kochi, Visakhapatnam, and more.

---

#  Key Findings

* Shimla and Srinagar are clear cold-weather outliers
* Rajasthan cities (Jodhpur, Jaipur) dominate the hot end
* Humidity and temperature show a weak negative correlation
* Coastal cities have ~10–15% higher humidity than inland cities
* KMeans identified 3 climate groups:

  * Hot & Dry
  * Humid Coastal
  * Cool Cities

---

#  Limitations

* Dataset is a single-time snapshot (no time series)
* Only 50 cities (good for patterns, not statistical generalization)
* Coastal/Inland classification is partly manual (e.g., Pune borderline case)
* Cluster labels are interpreted from centroids, not inherently “true classes”


