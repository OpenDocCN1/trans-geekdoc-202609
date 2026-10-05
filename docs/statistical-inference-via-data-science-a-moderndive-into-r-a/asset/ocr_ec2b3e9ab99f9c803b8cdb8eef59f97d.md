# 2.4 LNG#2: Lineigraphs

The most common examples of lineigraphs have some notion of time on the x-axis hours, days, weeks, etc. Since time is sequential, we connect consecutive observations of the variable on the y-axis with a line. Lineigraphs have some notion of time on the x-axis are also time series plots. Let's illustrate lineigraphs using another dataset in the nycflights23 package: the weather data frame.

Let's explore the weather data frame from the nycflights23 package by running view(weather) and glimpse(weather). Furthermore, we'll read the associated help file by running weather to bring up the help file.

Observe that there is a variable wind_speed of hourly speed records in miles per hour near three major airports in New York City: Newark (origin EWR), John F. Kennedy International (JFK), and LaGuardia (LGA).

However, instead of considering hourly wind speeds for all days in 2023 for all airports, for simplicity we consider hourly wind speeds at Newark airport for the first 15 days in January. This data is accessible in the early_january_2023_weather data frame included in the modernive package. In other words, early_january_2023_weather contains hourly weather observations for origin equal to EWR (Newark's airport code), month equal to 1, and less than or equal to 15.

# Learning check

(LC2.9) Take a look at both the weather data frame from the nycflights23 package and the early_january_2023_weather data frame from the modernive package by running View(weather) and View(early_january_2023_weather). In what respect do these data frames differ?

(LC2.10) View() the flights data frame again. Why does the time_hour variable uniquely identify the hour of the measurement, whereas the hour variable does not?

# 2.4.1 Lineigraphs via geom_line

Let's create a time series plot of the hourly wind speeds saved in the early_january_2023_weather data frame using geom_line() to create a lineigraph, instead of geom_point() like we used previously to create scatterplots:

```
ggplot(data = early_january_2023_weather,
      mapping = aes(x = time_hour, y = wind_speed)) +
  geom_line()
```