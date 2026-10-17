# 8.1 Intro to ggplot

We'll begin by demonstrating how to create a scatter plot in ggplot2 to introduce the three key elements of a ggplot2 object. Specifically, we create a scatter plot of a patient's depression vs. anxiety score. To start a graph, we can use the ggplot() function to create a ggplot object as shown in the following code. Note that this brings up a gray box; this is the base that we build up from.

```
ggplot()
```

![](bbox=[0.13, 0.363, 0.87, 0.642])

Next, we can begin adding layers to our ggplot object. One type of layer is a geom, which creates a geometric object. In the next code chunk, we use the geom_point() function to add a scatter plot layer. For this function, we first need to specify which data we want to use, and then we need to tell R how to use that data to create the scatter plot using the aes() function, which creates an aesthetic. For a scatter plot, we need to at least specify the x-axis and y-axis in the aesthetic. Both the data and the aesthetic can either be specified in our initial ggplot() function, which passes this information to all future layers, or in the geom_point() function itself. In the following code, we specify the aesthetic in the geom function but also include two alternative ways to code the same image in the subsequent code chunk. The resulting plot shows a fairly linear relationship between anxiety and depression.