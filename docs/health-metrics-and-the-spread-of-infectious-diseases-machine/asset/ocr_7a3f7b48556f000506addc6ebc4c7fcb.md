# Example: Simulation of Infections in Central African Rep.

The as.data.frame() function converts the matrix to a data frame, and the dplyr::select() function selects the longitude and latitude columns. The summary() provides a summary of the data frame, including the mean, median, and quartiles of the longitude and latitude values.

```
ctr_africa_coords <- ctr_africa %%
s::st_coordinates() %%
as.data.frame() %%
dplyr::select(X, Y)
```

```
ctr_africa_coords %%
summary()
# Min. : 14.46  Min. : 2.268
# 1st Qu.: 16.58  1st Qu. : 4.648
# Median : 20.96 Median : 5.3564
# Mean : 20.70   Mean : 6.294
# 3rd Qu.: 24.26 3rd Qu. : 8.145
# Max. : 27.37   Max. : 11.142
```

Synthetic data are created as an image of the spread of infections observed in Central Africa on a specific point in time. Data are generated using random numbers for the number of infected individuals, location and temperature levels. The temperature levels consider a mean of 20.3 degrees Celsius (69 degrees Fahrenheit), a maximum of 29.2 C (85 °F), and a daily average of 24.7 °C (76 °F).

The synthetic data are generated using the rbinom(), rnorm(), and rpois() functions from the (stats) package. Data are generated for 100 locations in Central Africa, with 70% of the locations infected and 30% non-infected. The latitude and longitude are generated using the rnorm() function with mean values of 6.294 and 20.70, respectively. The number of infected individuals is generated using the rpois() function with a mean value of 10, and the temperature levels are generated using the rnorm() function with a mean value of 25.

Set the number of points:

```
num_points <- 100
```

# 12.4.3 Data Simulation

```
set.seed(21082024) # set seed for reproducibility
# simulate the presence of infection
# 1 = "infected" and 0 = "non_infected"
longitude <- rnorm(n = num_points, mean = 20.70, sd = 1)
latitude <- rnorm(n = num_points, mean = 6.294, sd = 1)
presence <- rbinom(100, 1, prob = 0.3)
cases <- ifelse(presence == 1,
rpois(n = num_points*0.7, lambda = 10), 0)
temperature <- rnorm(n = num_points,
mean = 24.7,
sd = (29.2 - 20.3) / 4)
```

```
# build a dataframe *
```