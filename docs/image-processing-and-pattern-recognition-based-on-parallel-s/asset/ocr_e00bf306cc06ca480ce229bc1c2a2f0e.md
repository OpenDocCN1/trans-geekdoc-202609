![](bbox=[0.265, 0.16, 0.375, 0.255])

![](bbox=[0.445, 0.1, 0.735, 0.39])

# Fig. 3.8: Example of causing correction in FAI graphs

In this example, the image of square 100 × 100 have the main image and square 10 × 10 is the noise, which is not removed in the process of removal of noise. If the noise is in the direction of the shift copy of the original image, then the formation of function of the area of intersection may cause errors. In a graph FAI (x) of Fig. 3.8b there is a horizontal component, which does not allow determination of the maximum shift correctly. In this case, it becomes necessary to correct the graph.

We introduce the concept of the value of noise effects threshold (dN). DN value specifies a certain percentage of the elements of the input image area (S0), which will be considered as noise. Thus, the correct formula of the basic parameters of the function of the area of intersection, as maximum shifts, takes the following form:

```
Xmax = x - 1, if FAI(x - 1) = FAI(x) and FAI(x) ≤ dN · S0 (3.3)
```

```
Ymax = y - 1, if FAI(y - 1) = FAI(y) and FAI(y) ≤ dN · S0 (3.4)
```

The values obtained from these formulas are fully consistent with options for obtaining the value of the maximum shifts using zero-crossing property.

Note that the functions of the small horizontal sections crossing areas can be only a consequence of the form of the input object. In this case, those elements of the original image will be perceived as noise. Using a threshold value of noise components, we cut the excess information in FAI graphs in the process of construction.