
## 14 Neural networks for images

### 14.1 Introduction

In an MLP, the core operation at each hidden layer is computing $\mathbf{z} = \varphi(\mathbf{W}\mathbf{x})_j$. However, this does not work well if the input is a variable-sized image, $\mathbf{x} \in \mathbb{R}^{WHC}$, where $W$ is the width, $H$ is the height, and $C$ is the number of input **channels** (e.g., $C = 3$ for RGB color). The problem is that we would need to learn a different-sized weight matrix for every input size. In addition, even if the input was fixed size, the number of parameters needed would be prohibitive for reasonably sized images.

In this chapter, we discuss **convolutional neural networks (CNN)**, in which we replace matrix multiplication with a convolution operation. We explain this in detail in Sec. $14.2$, but the basic idea is to divide the input into overlapping 2d image patches, and to compare each patch with a set of small weight matrices, or filters, which represent parts of an object; this is illustrated in Fig. $14.1$. We can think of this as a form of **template matching**. The key is that we learn the templates from data, and can also do the matching in feature space, not just pixel space.

The templates can occur anywhere in the input, which reduces the number of parameters, and also ensures that the model is **invariant** to translations of the input. This is useful for tasks such as image classification, where the goal is to classify if an object is present at any location. CNNs have many other applications besides image classification, as we will discuss later in this chapter. They can also be applied to 1d inputs (see Sec. $15.3$) and 3d inputs; however, we mostly focus on the 2d case in this chapter.

### 14.2 Basics

In this section, we discuss the basics of CNNs.

### 14.2.1 Convolution in 1d

The **convolution** between two functions, say $f, g : \mathbb{R}^{D} \to \mathbb{R}$, is defined as

$$[f \star g](\mathbf{z}) = \int_{\mathbb{R}^{D}} f(\mathbf{u})g(\mathbf{z} - \mathbf{u})\,d\mathbf{u} \tag{14.1}$$

Now suppose we replace the functions with finite-length vectors, which we can think of as functions defined on a finite set of points. For example, suppose $f$ is evaluated at the points $\{-L, -L + 1, \ldots, 0, 1, \ldots, L\}$ to yield the weight vector (also called a filter or kernel) $w_{-L} = f(-L)$ up to $w_L = f(L)$. Now let $g$ be evaluated at points $\{-N, \ldots, N\}$ to yield the feature vector $\mathbf{x}_{-N} = g(-N)$ up to $\mathbf{x}_N = g(N)$. Then the above equation becomes

$$[\mathbf{w} \star \mathbf{x}](i) = w_{-L}x_{i+L} + \cdots + w_{-1}x_{i+1} + w_0x_i + w_1x_{i-1} + \cdots + w_Lx_{i-L} \tag{14.2}$$

(We discuss boundary conditions (edge effects) later on.) We see that we “flip” the weight vector **w** (since indices of **w** are reversed), and then “drag” it over the **x** vector, summing up the local windows at each point, as illustrated in Fig. 14.2.

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_464_0.png)

Figure 14.1: We can classify a digit by looking for certain discriminative features (image templates) occurring in the correct (relative) locations. From Figure 5.1 of [Cho]. Used with kind permission of Francois Chollet.

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_464_1.png)

Figure 14.2: Discrete convolution of **x** = [1, 2, 3, 4] with **w** = [5, 6, 7] to yield **z** = [5, 16, 34, 52, 45, 28]. We see that this operation consists of “flipping” **w** and then “dragging” it over **x**, multiplying elementwise, and adding up the results.

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_464_2.png)

Figure 14.3: 1d cross correlation. Adapted from Figure 13.10.1 of [Zha+19a].

There is a very closely related operation, in which we do not flip **w** first:

$$[\mathbf{w} \star \mathbf{x}](i) = w_{-L}x_{i-L} + \cdots + w_{-1}x_{i-1} + w_0x_i + w_1x_{i+1} + \cdots + w_Lx_{i+L} \tag{14.3}$$

This is called **cross correlation**; If the weight vector is symmetric, as is often the case, then cross correlation and convolution are the same. In the deep learning literature, the term “convolution” is usually used to mean cross correlation; we will follow this convention.

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_465_0.png)

Figure 14.4: Illustration of 2d cross correlation. Adapted from Figure 6.2.1 of [Zha+19a].

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_465_1.png)

Figure 14.5: Convolving a 2d image (left) with a 3 × 3 filter (middle) produces a 2d response map (right). The bright spots of the response map correspond to locations in the image which contain diagonal lines sloping down and to the right. From Figure 5.3 of [Cho]. Used with kind permission of Francois Chollet.

We can also evaluate the weights **w** on domain {0,1,…,L−1} and the features **x** on domain {0,1,…,N−1}, to eliminate negative indices. Then the above equation becomes

[**w** ⊗ **x**](t) = Σ_{u=0}^{L−1} w_u x_{i+u}  (14.4)

See Fig. 14.3 for an example.

### 14.2.2 Convolution in 2d

In 2d, Eq. (14.4) becomes

[**W** ⊗ **X**](i,j) = Σ_{u=0}^{H−1} Σ_{v=0}^{W−1} w_{u,v} x_{i+u,j+v}  (14.5)

where the 2d filter **W** has size H × W. For example, consider convolving a 3 × 3 input **X** with a 2 × 2 kernel **W** to compute a 2 × 2 output **Z**:

**Z** = (w1 w2; w3 w4) ⊗ (x1 x2 x3; x4 x5 x6; x7 x8 x9)  (14.6)

= ((w1 x1 + w2 x2 + w3 x4 + w4 x5) (w1 x2 + w2 x3 + w3 x5 + w4 x6); (w1 x4 + w2 x5 + w3 x7 + w4 x8) (w1 x5 + w2 x6 + w3 x8 + w4 x9))  (14.7)

See Fig. 14.4 for a visualization of this process.

Do not distribute without permission from Kevin P. Murphy and MIT Press.

We can think of 2d convolution as **template matching**, since the output at a point (i, j) will be large if the corresponding image patch centered on (i, j) is similar to W. If the template W corresponds to an oriented edge, then convolving with it will cause the output **heat map** to “light up” in regions that contain edges that match that orientation, as shown in Fig. 14.5. More generally, we can think of convolution as a form of **feature detection**. The resulting output Z = W ⊛ X is therefore called a **feature map**.

### 14.2.3 Convolution as matrix-vector multiplication

Since convolution is a linear operator, we can represent it by matrix multiplication. For example, consider Eq. (14.7). We can rewrite this as matrix-vector multiplication by flattening the 2d matrix X into a 1d vector x, and multiplying by a Toeplitz-like matrix C derived from W, as follows:

z = C x = ( w1 w2 0 | w3 w4 0 | 0 0 0 ; 0 w1 w2 | 0 w3 w4 | 0 0 0 ; 0 0 0 | w1 w2 0 | w3 w4 0 ; 0 0 0 | 0 w1 w2 | 0 w3 w4 ) ( x1 x2 x3 x4 x5 x6 x7 x8 x9 )ᵀ  (14.8)

= ( w1 x1 + w2 x2 + w3 x4 + w4 x5 ; w1 x2 + w2 x3 + w3 x5 + w4 x6 ; w1 x4 + w2 x5 + w3 x7 + w4 x8 ; w1 x5 + w2 x6 + w3 x8 + w4 x9 )  (14.9)

We can recover the 2 × 2 output by reshaping the 4 × 1 vector z back to Z in the obvious way.¹ Thus we see that CNNs are like MLPs where the weight matrices have a special sparse structure, and the elements are tied across spatial locations. This implements the idea of translation invariance, and massively reduces the number of parameters compared to a weight matrix in a standard fully connected or dense layer, as used in MLPs.

### 14.2.4 Boundary conditions and strides

In Eq. (14.7), we saw that convolving a 3 × 3 image with a 2 × 2 filter resulted in a 2 × 2 output. In general, convolving a f_h × f_w filter over an image of size x_h × x_w produces an output of size (x_h − f_h + 1) × (x_w − f_w + 1); this is called **valid convolution**, since we only apply the filter to “valid” parts of the input, i.e., we don’t let it “slide off the ends”. If we want the output to have the same size as the input, we can use **zero-padding**, which means we add a border of 0s to the image, as illustrated in Fig. 14.6a. This is called **same convolution**.

Since each output pixel is generated by a weighted combination of inputs in its **receptive field** (based on the size of the filter), neighoring outputs will be very similar in value, since their inputs are overlapping. We can reduce this redundancy (and speed up computation) by skipping every s-th
