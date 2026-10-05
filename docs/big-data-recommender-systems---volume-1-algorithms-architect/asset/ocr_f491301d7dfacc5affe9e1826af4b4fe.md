# 154 Big data recommender systems, volume 1

the gradient of error. $\eta \le 1$ is the factor by which the extent of correcting is determined and it is known as step size of the learning rate. Based on (7.11), the associated prediction error of rating $r_{ui}$ can be computed as:

```
$e_{ui} = r_{ui} - \mu - b_u - b_i - x_u^T y_i \quad (7.13)$
```

The operating operations are as follows:

+   $b_u \to b_u + \eta(e_{ui} - \lambda b_u) \quad (7.14)\n$b_i \to b_i + \eta(e_{ui} - \lambda b_i) \quad (7.15)\n$x_u \to x_u + \eta(e_{ui}x_u - \lambda x_u) \quad (7.16)\n$y_i \to y_i + \eta(e_{ui}y_i - \lambda y_i) \quad (7.17)$

The confident levels of various implicit feedback data instances are considered by the online strategy. The learning rate of the training process is adjustable to each data instance.

# Real-time video recommendation generation

The procedure of real-time recommendation generation is discussed in this section. In order to make accurate video recommendations in real-time, a similar video table should be built to pick high-quality candidate videos for recommendation; for each, it will record the most related videos. The factors are leveraged from three aspects to compute the similarity of videos. These three aspects are the MF similarity, the time similarity and the time factor [39].

The definition of CF similarity goes as

```
$S_{ij} = y_i^T y_j \quad (7.18)$
```

For video $i$ and $j$, the similarity is defined as follows:

```
$S_{ij} = \begin{cases} 1 & \text{type}(i) = type(j) \ 0 & \text{type}(i) \neq type(j) \end{cases} \quad (7.19)$
```

Specifically, the similarity of video pairs will decrease when their update time go up from the current time. The update time refers to the time of the latest user action that touches the similarity computation (similarity of video $i$ and $j$ will be updated when new user action relating to $i$ or $j$ happens), a damping factor which is used to measure this time factor as follows:

```
$d_{ij} = 2^{-\Delta t/	au} \quad (7.20)$
```

where $\Delta t$ is the time difference between $sim_{ij}$'s update time and current time, and $\xi$ is a parameter which controls the rate of decay. By giving two videos, $i$ and $j$, the overall relevance between them [39] is defined as

```
$sim_{ij} = d_{ij}((1 - \beta) * S_{1ij} + \beta * S_{2ij}) \quad (7.21)$
```

where $eta$ is a parameter adjusting the weight of different similarity factors in the final relevance function. The exact values of $\xi$ and $eta$ are determined by the experiments. The model is scalable implemented on Storm, a distributed real-time