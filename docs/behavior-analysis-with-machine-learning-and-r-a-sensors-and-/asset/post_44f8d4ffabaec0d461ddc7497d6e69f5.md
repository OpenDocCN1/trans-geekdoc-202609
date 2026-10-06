
# CHAPTER 7. ENCODING BEHAVIORAL DATA

a CNN and perform inference. CNNs will be covered in chapter 8 and we'll also see how to build adaptive models using these activity images.

## Advantages:

- Spatial relationships can be captured.
- Can be multi-dimensional. For example 3D RGB images.
- Can be efficiently processed with CNNs.

## Limitations:

- Computational time can be higher than processing feature vectors. Still, modern hardware and methods allow us to perform operations very efficiently.
- It can take some extra processing to convert non-image data into images.

## 7.5 Recurrence Plots

Recurrence plots (RPs) are visual representations similar to images but typically they are one-dimensional. They are encoded as $n \times n$ matrices, where the same number of rows and columns (a square matrix). Even though these are like a special case of images, I thought it would be worth having them in their own subsection! Just as images, timeseries can be converted into RPs and then used to train a CNN.

A recurrence plot (RP) is a visual representation of patterns of dynamical systems (for example, timeseries). RPs were introduced by Eckmann et al. (1987) and they depict all the times when a trajectory is roughly in the same state. Biological systems possess behavioral patterns and activity dynamics that can be captured with RPs, for example, the dynamics of ant colonies (Neves et al., 2017).

At this point, you might be curious about how an RP looks. So let me begin by showing a picture$^4$ of 4 time series with their respective RP (Figure 7.8).

The first RP (leftmost) does not seem to have a clear pattern (white noise) whereas the other three show patterns like diagonals of different sizes, square and circular shapes, and so on. RPs can be characterized by small-scale and large-scale patterns. Examples of small-scale patterns are diagonals, horizontal/vertical lines, dots, etc. Large-scale patterns are called $typology$ and they depict the global characteristics of the dynamic system$^5$.

> $4$https://commons.wikimedia.org/wiki/File:Rp_examples740.gif

> $5$http://www.recurrence-plot.tk/glance.plip

![](img/91c149cc24c3e5af2971580c9dda9d8b_221_0.png)

Figure 7.8: Four timeseries (top) with their respective RPs (bottom). Source: wikipedia.

The visual interpretation of RPs requires some experience and is out of the scope of this book. However, they can be used as a visual pattern extraction tool to represent the data and then, in conjunction with machine learning methods like CNNs, used to solve classification problems.

> There exists an objective way to analyze RPs is called recurrence quantification analysis (RQA) (Zbilut and Webber, 1992). It introduces several measures like percentage of recurrence points (recurrence rate), percentage of points that form vertical lines (laminarity), average length of diagonal lines, length of the longest diagonal line, trees, etc. Those measures can then be used as features to train classifiers such as decision trees, k-nn, etc.

But how are RPs computed? Well, that is the topic of the next section.

## 7.5.1 Computing Recurrence Plots

It's time to delve into the details of how these mysterious plots are computed. Suppose there is a timeseries with $n$ elements (points). To compute its RP we need to compute the distance between each pair of points. We can store this information in an $n \times n$ matrix. Let's call this a distance matrix $D$. Then, we need to define a threshold $\epsilon$. For each entry in $D$ if the distance is less or equal than the threshold $\epsilon$ then it is set to 1 and 0 otherwise.

Formally, a recurrence of a state at time $i$ at a different time $j$ is marked within a two-dimensional square matrix with ones and zeros whose axes represent time:

```
$R_{i,j}(x) = \begin{cases} 1 & \text{if } ||\tilde{x}_i - \tilde{x}_j|| \le \epsilon \\ 0 & \text{otherwise}. \end{cases} \quad (7.1)$
```

where $\vec{x}$ are the states and $||\cdot||$ is a norm (for example Euclidean distance). $R_{i,j}$ is the square matrix and will be 1 if $\vec{x}_i \approx \vec{x}_j$ up to an error $\epsilon$. The $\epsilon$ is important since systems do not recur exactly to a previously visited state.

The threshold $\epsilon$ needs to be set manually which can be difficult in some situations. If not set properly, the RP can end up having excessive ones or zeros. If you plan to use RPs as part of an automated process and fed them to a classifier, you can use the distance matrix instead. The advantage is that you do not need to specify any parameter except for the distance function. The distance matrix can be defined as:

```
$D_{i,j}(x) = ||\vec{x}_i - \vec{x}_j||$
```

which is similar to Equation (7.1) but without the extra step of applying a threshold.

## Advantages:

- RPs capture dynamic patterns of a system.
- They can be used to extract small and large scale patterns.
- Timeseries can be easily encoded as RPs.
- Can be used as input for CNNs for supervised learning tasks.

## Limitations:

- Computationally intensive since all pairs of distances need to be calculated.
- Their visual interpretation requires experience.
- A threshold needs to be defined and it is not always easy to find the correct value. However, the distance matrix can be used instead.

## 7.5.2 Recurrence Plots of Hand Gestures

```
recurrence_plots.R
```

In this section, I am going to show you how to compute recurrence plots in R using as an example the HAND GESTURES dataset. The code can be found in the script recurrence_plots.R. First, we need a norm (distance function) for example the Euclidean distance:

```r
# Computes Euclidean distance between x and y.
norm2 <- function(x, y){
  return(sqrt((x - y)^2))
}
```

This function defines two square matrices M and D to store the recurrence plot and the distance matrix, respectively. Then, it iterates the matrices from bottom to top right and fills the corresponding values for M and D. The distance between elements i and j from the vector is computed. That distance is directly stored in D. To generate the RP we check if the distance is less or equal to the threshold. If that is the case the entry entry in M is set to 1. Finally, both matrices are returned by the function.

```r
rp <- function(x, e, f){
#x: vector
#e: threshold
#f: distance function
N <- length(x)
# This will store the recurrence plot.
M <- matrix(nrow=N, ncol=N)
# This will store the distance matrix.
D <- matrix(nrow=N, ncol=N)

for(i in 1:N){
  for(j in 1:N){
    # Compute the distance between a pair of points.
    d <- f(x[i], x[j])
    # Store result in D.
    # Start filling values from bottom.
    D[N - i+1, j] <- d
    if(d <= e){
      M[N - i+1, j] <- 1
    }else{
      M[N - i+1, j] <- 0
    }
  }
}
return(list(D=D, RP=M))
}
```

Now, we can try rp() function on the HAND GURES dataset to convert one of the timeseries into a RP. We first read one of the gesture files. For example, the first gesture '1' from user 1. We only extract the acceleration from the x axis and store it in x.

```r
df <- read.csv("../data/hand_gestures/1/1_20130703-1200056.txt", header = F)

x <- df$V1
```

If we plot vector x we get something like in Figure 7.9.

```r
# Plot vector x.
plot(x, type="l", main="Hand gesture 1", xlab="time", ylab="")
```

Now the rp() function that we just defined is to calculate the RP and distance matrix of vector x. We set a threshold of 0.5 and store the result in res.

```r
# Compute RP and distance matrix.
res <- rp(x, 0.5, norm2)
```

Let's first plot the distance matrix stored in resD. The heatmap() function can be used to generate the plot.
