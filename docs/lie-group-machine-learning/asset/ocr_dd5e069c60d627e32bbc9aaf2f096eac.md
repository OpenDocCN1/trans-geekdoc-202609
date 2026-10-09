![](bbox=[0.1, 0.08, 0.9, 0.35])

Here, we measure the describing ability of a tensor space by using $\varepsilon$, and we have

$$\varepsilon=\|T-A_{v}w_{v}\| \quad \quad \quad (10.38)$$

+   Finally, we summarise the tensor bundle learning model as follows: (Figure 10.13).
a) Construct the tensor based on the training sample;
b) Reconstruct the sub-tensor by tensor decomposition and build the tensor space;
c) Project the testing sample into the tensor space of each object cluster;
d) Determine the attributes of the testing sample with the projection results.

# **10.3.2 Tensor bundle learning algorithm**

In recent years, research has indicated that colour provides important information for human face recognition [19–22, 36, 37]. If we use the colour information in the classical PCA algorithm, the recognition effect can be better than that with only the grey information. A common method to represent a colour image is to divide the RGB space into three parts. However, this method, in theory, lacks support and experimental evidence. Another way to represent a colour image is the linear combination of every colour channel [23], e.g., $D = x_{1}R + x_{2}G + x_{3}B$. Here $x_{1}$ and $x_{3}$ are the combination factors. All these methods can manipulate the colour image vectorisation. In the tensor bundle learning algorithm, we can use the colour information as another view of the tensor, which would make it easier to understand the image.

First, we consider the construction method of the tensor model of a human face image. In RGB colour space, each image can be divided into three parts (Figure 10.14). Each part represents a different colour ingredient. For each person, we can construct a fourth-order tensor of their face as $T_{p}\in R^{I_{1}\times I_{2}\times I_{3}\times I_{4}}$ (Figure 10.14), where $I_{1}\times I_{2}\times I_{3}\times$