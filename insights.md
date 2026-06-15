# Insights — Indian Cities Weather EDA

Key findings from live weather data collected across 50 Indian cities via the OpenWeatherMap API.

---

## 1. Temperature Distribution

Hottest cities — Rajasthan cities (Jodhpur, Jaipur, Ajmer) consistently appear at the top end. High daytime temperatures are driven by low humidity and minimal cloud cover.

Coldest cities — Shimla and Srinagar are clear outliers. The hill station effect is dominant here, where altitude has a stronger influence than latitude.

The average temperature across all 50 cities typically falls in the 28–35°C range depending on the time of data collection, reflecting India’s predominantly tropical climate.

The spread between the hottest and coldest cities is significant (20°C+), which supports the need for clustering rather than relying only on summary statistics.

---

## 2. Humidity vs Temperature

A weak negative correlation is observed — as temperature increases, humidity tends to decrease.

This aligns with intuition: hot and dry regions (such as Rajasthan) reduce humidity levels, while coastal cities maintain higher humidity with moderate temperatures.

However, the relationship is not strong enough for prediction purposes. The scatter is widely distributed, indicating high variability.

Regression analysis confirms the negative trend, but with a broad confidence interval.

Takeaway: This is a trend, not a deterministic relationship.

---

## 3. Wind Speed vs Humidity

No clear relationship is observed between wind speed and humidity across Indian cities.

While wind can influence local moisture distribution, city-level single-point measurements dilute this effect due to geographic and environmental variability.

Coastal cities do not consistently show higher wind speeds, suggesting that measurement location (city center vs coastal edge) impacts results significantly.

---

## 4. Wind Speed vs Pressure

A slight negative trend is observed — higher wind speeds are loosely associated with lower pressure.

This is consistent with atmospheric physics, where pressure gradients drive wind movement.

However, the correlation remains weak due to the limited dataset and lack of time-series data.

---

## 5. Correlation Heatmap (Numeric Features)

Columns analyzed: Temperature, Feels Like, Humidity, Pressure, Wind Speed

Notable correlations:

- Temperature and Feels Like: near perfect positive correlation, as expected since both are derived from similar atmospheric conditions
- Temperature and Humidity: weak negative correlation
- Pressure and Temperature: slight negative relationship, often influenced by altitude differences
- Other relationships: weak or negligible correlations

Visibility was excluded from the correlation matrix as it behaves more like an outcome variable influenced by external conditions such as fog, pollution, and dust rather than a driver of weather patterns.

---

## 6. Weather Descriptions

Most common observed conditions:

- Haze and mist dominate in several cities, especially across northern plains
- Clear sky and few clouds are more frequent in drier or southern regions
- Overcast conditions are more common in coastal and northeastern cities

When grouped by weather description, hazy conditions tend to appear in cities with moderate to low temperatures, aligning with typical morning fog patterns in northern India.

---

## 7. Climate Clustering (KMeans, k=3)

Three clusters were identified using Temperature, Humidity, Wind Speed, and Pressure after standardization.

Cluster 0: Hot and Dry
High temperature, low humidity, moderate wind conditions

Cluster 1: Humid Coastal
Moderate to high temperature with high humidity and relatively stable wind patterns

Cluster 2: Cool Cities
Lower temperatures, moderate humidity, typically representing hill stations and cooler northern regions

A key observation is that clustering was derived purely from weather variables without geographic labels. The emergence of coastal cities in one cluster and hill stations in another suggests that meteorological variables inherently capture geographic structure.

The choice of k=3 was based on domain intuition representing broad climate zones in India. A formal elbow method analysis was not performed, which is a limitation.

---

## 8. Coastal vs Inland Comparison

Coastal cities included: Mumbai, Chennai, Kochi, Visakhapatnam, Mangalore, Kolkata, Surat, Pune

Metric comparison:

Coastal cities
- Higher humidity (approximately 10–15 percent higher on average)
- More stable temperature ranges
- Slightly higher wind variability

Inland cities
- Lower humidity
- Higher temperature variability with more extreme highs and lows
- More continental climate characteristics

A note of caution: Pune was included in the coastal category due to perceived climatic influence, but geographically it is inland. This classification is debatable and should be reconsidered in future iterations.

---

## Limitations

- The dataset represents a single snapshot in time, so seasonal and temporal variations are not captured
- 50 cities provide a good sample for pattern recognition but are insufficient for statistically robust conclusions
- No UV index or dew point data included due to API limitations in the free tier
- Cluster labels are interpretive and assigned post-analysis based on centroid characteristics
- Correlation does not imply causation; all relationships are observational
