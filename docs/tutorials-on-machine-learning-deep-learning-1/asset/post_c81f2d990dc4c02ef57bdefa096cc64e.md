
When we look for certain features, the network decides during its training which features are important for certain types/categories and it looks for us using different filters/feature-detectors. It'll apply these filters/feature-detectors so we get certain feature map.
That's why the term Feature Detector is better than the certain Filters.

We create many feature maps to obtain our first convolution layer.

## Feature Maps

| 0 | 0 | 0 | 0 | 0 |
| 0 | 1 | 0 | 0 | 1 |
| 0 | 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 0 | 0 |
| 0 | 1 | 1 | 1 | 0 |
| 0 | 0 | 0 | 0 | 0 |

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_274_0.png)

Input Image

Convolutional Layer

Let's see some example of filters for an image app. We are using Gimp.org. Here we have a picture of the Taj Mahal and you can choose which filter we want to apply. So if you download this program and upload a photo into it and then you can actually start a Convolution-matrix and apply filters. Following are commonly used filters.

Image Source: docs.gimp.org/en/plug-in-convmatrix.html

> Sharpen: if we apply this filter, we can see that it-sharpens the image. 5 in the middle as main pixel and four-1s. Kind of reduces the pixels around.

## Sharpen:

```
00000
00-100
01-510
01-100
00000
```

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_274_1.png)

Blur: All six 1's. Basically takes significant weight to all of the pixels and therefore it combines them together and you get a blur.

## Blur:

```
00000
01110
01110
01110
00000
```

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_274_2.png)

## Edge Enhance:

Edge Enhance: So here you can see that it's -1 and 1 and then you get all 0's (i.e. remove the main one). It gives you an edge.

```
|0 0 0|
|-1 1 0|
|0 0 0|
```

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_275_0.png)

## Edge Detect:

Edge Detect: So here we are detecting edge. You reduce the middle one as -4. And use 1s around it.

```
|0 1 0|
|3 -4 1|
|0 1 0|
```

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_275_1.png)

## Emboss:

Emboss: So the key point here is that this matrix is asymmetrical and you can see the image becomes asymmetrical.

```
|-2 -1 0|
|-1 1 1|
|0 1 2|
```

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_275_2.png)

But we can see these are great examples of the same image but we're getting different feature maps using different filters/feature-detectors.

But these terms: Edge-detect is quite important to us (we are not working with Gimp). We are not going to use those terms in CNN.

CNN will decide for itself what's important, what's not and it probably won't even be recognizable to the human eye. You won't be able to understand what those features mean.

That's the beauty of CNN. They can process so many different things and understand without even having that explanation why they understand which features are important to them when we have a term/name for those features or not.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_275_3.png)

*

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_275_4.png)

Here's a image of Geoffrey Hinton passed through one of these filters.

```
|1 0 -1|
|2 0 -2|
|1 0 -1|
```

The key-point is: the primary purpose of Convolution is to find features in your image using the feature detector, [to] put them into a Feature map [and] by preserving the spatial relationships between pixels (if they are completely jumbled then we've lost the pattern).

It's important to understand that most of the time the features a neural network will detect/recognize certain images and classes, it will mean nothing to humans.

## 9.2.2 Rectified Linear Unit (ReLU)

ReLU (Rectified Linear Unit) is an additional step on top of our Convolution. Here we have our Input image and we have Convolution Layer on top of that we're going to apply rectifier function. The reason why we're applying the rectifier is we want to increase Nonlinearity in our image or our CNN. ReLU acts as a filter function that breaks linearity.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_276_0.png)

- Why increase Nonlinearity: We want to increase nonlinearity in our network because images themselves are highly non-linear especially if you're recognizing different objects next to each other.
- Images are going to have lots of elements and transition between adjacent pixels often becomes nonlinear because of borders, different colors in your images.
- When we're applying a mathematical operation such as convolution, and running this feature detection to create our maps there is a possibility that we might create something linear therefore we need to break up the linearity. Example: Here is an original image. When we apply feature detector to this image we get: you can see that black is negative and white is positive. When you apply feature detector to a real-life image (not just 1 or 0 but lots of different values, including negative values) we get this kind of result.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_276_1.png)

Now a Rectified Linear Unit (ReLU) function removes all the black (anything below zero turns into zero).

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_277_0.png)

## Only non-negative values

It's pretty hard to see what exactly the benefit in terms of breaking linearity. This is a very mathematical concept and would have to go into a lot of math to really explain what is going on. Now try to figure out without math.

- What is LINEARITY here: For instance called the white building. In black-negative and white-positive version notice the light. You see that it is White (the reflection of light) and then it's Gray and then it gets Dark and then it gets Darker it looks like when you go from White to Gray the next step would be Black. So it's a Linear Progression from Bright to Dark therefore this is kind of Linear situation.
- When you take out the black you break up the Linearity. There won't be any gradual progression like White-Gray-Black.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_277_1.png)

Real image: Bk = -ve, W=+ve Non-Linear: only +ve

- Having like an abrupt change which helps to introduce non-linearity into your image.
- Additional reading: if you'd like to learn more there is a good paper. This one is by C.C. Jay Kuo from the University of California and it's called "Understanding Convolutional neural networks with a mathematical model".
- There he answers this question: Why a nonlinear activation function is essential filter of all intermediate layers. It explains it in a bit more detail both in terms of intuition and in terms of mathematics.

## Additional Reading: Neural Convolutional Neural Networks With A Mathematical Model

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_277_2.png)

By C.-C. Jay Kuo (2016)

Link:
https://arxiv.org/pdf/1609.0411.pdf

And if you really want to dig in and explore more, then there's another paper that you might be interested in. It's called "Delving Deep Into Rectifiers: Surpassing Human Level Performance on ImageNet classification" by Kaiming He from Microsoft Research.

They proposed a different type of ReLU function which you do see here on the right. Which is parametric ReLU function. And they argue that it delivers better results withoutrificing PERFORMANCE.

## Additional Reading: Delving Deep into Rectifiers: Surpassing Human-Level Performance on ImageNet Classification

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_278_0.png)

By Kaiming He et al. (2015)

Link:
https://arxiv.org/pdf/1502.01852.pdf

# Chapter 9 : Part 3.
Deep Learning
CNN: Pooling, flattening & Full Connection

## 9.3.1 Pooling

Here we'll talk about Max pooling. And what is pooling and why do we need it. Well to answer that question let's have a look at following.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_279_0.png)

- We've got a cheetah. Same cheetah but in 2nd image it's rotated and in 3rd image it's a bit squashed. We want the neural network to be able to recognize the cheetah in every single one of these images.
- However, this is just one cheetah. What happens if we have lots of different Images of different Cheetahs?

> We want the neural network to recognize all of these Cheetahs. So how can it do that if they're all looking at different directions, they're in different parts of the image, they're faces are positioned differently and many other differences like light and texture etc.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_279_1.png)

> There's lots of little differences and so if the neural network looks for a certain feature for instance: A distinctive feature of the Cheetah is the tear-mark that are on its face going from the eyes.
