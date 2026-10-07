weather-data.py that illustrates how to combine two Pandas DataFrames.

# LISTING 3.6: weather-data.py

```
import pandas as pd

can_weather = pd.DataFrame({
    "city": ["Vancouver","Toronto","Montreal"],
    "temperature": [72,65,50],
    "humidity": [40, 20, 25]
})

us_weather = pd.DataFrame({
    "city": ["SF","Chicago","LA"],
    "temperature": [60,40,85],
    "humidity": [30, 15, 55]
})

df = pd.concat([can_weather, us_weather])
print(df)
```

The first line in Listing 3.6 is an import statement, followed by the definition of the Pandas dataframes can_weather and us_weather that contain weather-related information for cities in Canada and the USA, respectively. The Pandas dataframe df is the concatenation of can_weather and us_weather. The output from Listing 3.6 is here:

| Vancouver | 40 | 72 |
| Toronto | 20 | 65 |
| Montreal | 25 | 60 |
| Chicago | 15 | 40 |
| LA | 55 | 85 |