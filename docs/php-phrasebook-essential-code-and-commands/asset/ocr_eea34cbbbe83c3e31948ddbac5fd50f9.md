# Automatically Localizing Dates

![](bbox=[0.184, 0.11, 0.903, 0.332])

Figure 3.1  The current date in different locales.

![](bbox=[0.181, 0.416, 0.916, 0.639])

Figure 3.2  This particular system does not seem to support locales.

# Manually Localizing Dates

If you cannot rely on setlocale(), yet want to use localized date and time values, you have to do the translations by yourself and store the results in an array. Then, you can use date() to retrieve information about a date. This serves as an index for your array.