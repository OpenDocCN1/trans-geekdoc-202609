# Biological Pattern Discovery with R

The density function has a number of outputs. Two major ones include two coordinates. Suppose the output of the density function is saved in a variable named as model. The code below shows how to use these outputs. Two outputs (model$x and model$y) were used to call the lines to generate a density curve. The result of running the following code is shown in Figure 2.11.

```
x=c(-0.24,-1.24,0.74,0.38,1.49,0.19,0.30,
-0.99,0.58,-0.46,1.17,-2.89,-2.04,
-0.82,0.92,0.91,-0.88,1.06,0.95,0.44,
-1.16,1.12,10.75,4.05,3.23,7.85,
-1.56,4.21,9.34,8.05)
model=density(x)
hist(x,nclass=20,prob=TRUE)
lines(model$x,model$y)
```

![](bbox=[0.277, 0.413, 0.722, 0.558])

Fig. 2.11. An illustration of using the output of the density function.

# 2.2.3.2 The K-nearest neighbour approach

The K-nearest neighbour approach estimates a density function for a data point based on the density of a ball (or a spherical volume) centred at the data point with K nearest neighbours [Bailey and Jain, 1978]. Suppose a data point is denoted by x and the number of the nearest neighbours is denoted by K. The K-nearest neighbour approach estimates the density for a data point using the following equation, where $N$ is the total number of data points, $d$ stands for the data dimension and $V_d$ is the volume of a ball with the radius denoted as $R_K(x)$,

> $f_K(x) = rac{K}{N V_d R_K(x)}} \quad (2.7)$