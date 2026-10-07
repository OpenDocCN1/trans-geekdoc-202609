# Chapter 9 : Part 2

# Deep Learning
CNN: Convolution Operations
& ReLU layer

# 9.2.1 Convolution

Convolution: Following is the convolution function. A convolution is basically a combined integration of the two functions and it shows how one Function modifies the other or (modifies the shape of the other). If you've done any Signal Processing or Electrical Engineering you are already familiar with it.

```
$$(f * g)(t) \stackrel{	ext{def}}{=} \int_{-\infty}^{\infty} f(	au)g(t-	au)d	au$$
```

Additional Reading: If you know the mathematics of convolution function and CNN read the article below, is called "Introduction to convolutional neural networks" by Jianxin Wu who is a professor at Nanjing University in China. It is oriented specifically at people who are beginners to know CNN so the mathematics there should be accessible.

# Additional Reading:
Introduction to Convolutional Neural Networks

By Jianxin Wu (2017)

```
$$\begin{aligned} \frac{\partial z}{\partial(	ext{vec}(Y)^T)} (F \otimes I) &= (F \otimes I) \frac{\partial z}{\partial \text{vec}(Y)} \ &= (F \otimes I) 	ext{vec}\left(\frac{\partial z}{\partial Y}\right) \ &= \text{vec}\left(\frac{\partial z}{\partial Y} F^T\right) \ &= \text{vec}\left(\frac{\partial z}{\partial Y} F^T\right), \end{aligned}$$$
```

Link:

http://cs.nju.edu.cn/wujx/paper/CNN.pdf

cs.nju.edu.cn/wujx/index.htm

Convolution in intuitive terms: Here we got an input image, just ones and zeros to simplify things. You can see the smiley face here.

Feature Detector: We've also got a detector. This feature detects a 3x3 Matrix. It could be any size. The feature detected is being called filter you might be going to be using either filter or a feature detector interchangeably. And a Convolution operation is signified by ⊗ "x in a circle."

| 0 | 0 | 0 | 0 | 0 | 0 |
|---|---|---|---|---|---|n| 0 | 1 | 0 | 0 | 0 | 1 |
| 0 | 0 | 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 0 | 0 | 0 |
| 0 | 0 | 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 1 | 0 | 0 |
| 0 | 0 | 0 | 0 | 0 | 0 |

Input Image

| 0 | 0 | 1 |
|---|---|---|n| 1 | 0 | 0 |
| 0 | 1 | 1 |

Feature Detector