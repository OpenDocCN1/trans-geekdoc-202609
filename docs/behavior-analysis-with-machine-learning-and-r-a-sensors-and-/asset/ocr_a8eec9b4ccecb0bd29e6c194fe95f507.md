![](bbox=[0.318, 0.085, 0.681, 0.345])

Figure 5.1: The device was placed on the neck at a random position.

```
# Can take some seconds to load since the file is big.
df <- read.csv(datapath, stringsAsFactors = TRUE)
```

```
# Plot missing values.
gg_miss_var(df)
```

Figure 5.2 shows the resulting output. This plot shows that there are missing values in four variables: pressure, cz, cy and cx. The last three correspond to the compass (magnetometer). For pressure, the number of missing values is more than 2 million! For the rest, it is a bit less (more than 1 million).

To explore this issue, we can plot each observation in a row with the function vis_miss().

```
# Select first 1000 rows.
# It can take some time to plot bigger data frames.
vis_miss(df[1:1000])
```

Figure 5.3 shows every observation per row and missing values are black colored (if any). From this image, it can be seen that missing values seem to be systematic. It looks like a clear stripes pattern, especially for the compass variables. Based on these observations, we could guess that this doesn't look like random sensor failures or random noise.