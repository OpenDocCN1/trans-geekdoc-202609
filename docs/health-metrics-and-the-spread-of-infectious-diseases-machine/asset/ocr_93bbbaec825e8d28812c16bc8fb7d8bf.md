164

Introduction to Data Visualisation

languages like Fortran and BASIC were used to create simple plots, then the development
of specialised software like SAS and SPSS provided more robust tools for data analysis and
visualisation.

The emergence of the internet and web technologies in the 1990s led to the introduction of
more sophisticated statistical software and programming environments. Tools like R, Python,
and JavaScript, with libraries like ggplot2, matplotlib, and D3, revolutionised
t field of data visualisation, making it more accessible and powerful.

In summary, data visualisation plays a crucial role in fields like data science, business
analytics, scientific research, journalism, and public policy. It serves as a potential tool for
communicating data whileising patterns, trends, and relationships that might not be
aparent from raw data alone. For instance, in public health, tracking disease outbreaks in
time, as with COVID19, tools like dashboards and interactive maps are used extensively
to monitor the spread of the disease and communicate the effectiveness of interventions.

# 10.2 The Grammar of Graphics

One of the fundamental concepts in modern data visualisation layers is the Grammar of Graphics,
which provides a structured approach to creating visualisations by layer. This concept
is clearly interpreted in tools like the {ggplot2} R package, part of the {tidyverse}
ecosystem, developed by Hadleyham in 2005.

The Grammar of Graphics allows for the creation of complex visualisations by combining
simple building blocks as data, aesthetics, and geoms (geometric objects) in a
structured manner. It provides a flexible framework for customising visualisations and
supports the creation of a wide range of plots, from basic scatter plots to intricate multi-
layered visualisations.

It starts with the ggplot() function, which initialises the plot. The function takes a data
frame as its first argument and then additional arguments to specify the aesthetics of the
plot, as the x and y variables, colour, shape, and size.

```
ggplot()
```

The aesthetics are defined using the aes() function, which maps variables in the data frame
of visual properties of the plot, such as x and y coordinates, colour, shape, and size. The
aes() function is the mapping part of the plot, and it can be called with the mapping
argument in the layers of the plot.

```
ggplot(data = ,
mapping = aes(x = x, y = y, color = z))
```

Data can also be called outside of the ggplot() function.

```
data %>%
gggplot(aes(x = x, y = y, color = z))
```

And then additional layers are added using functions like geom_point() for a scatterplot, and
geom_line() for a line plot, and so on. Then, with the labs() function, we can add titles,
labels, and captions to the plot.