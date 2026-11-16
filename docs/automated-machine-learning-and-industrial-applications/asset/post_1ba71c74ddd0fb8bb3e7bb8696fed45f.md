

![](img/5510bd7390ed7002b5774fe8c2be9eff_231_0.png)

Figure 10.2 Schematic representation of AlexNet.

## 10.3.2 Existing CNN Models

The effectiveness of the E-EfficientNet approach was demonstrated by comparing it with cutting-edge CNN architectures such as Inception V3, AlexNet, ResNet50, and VGG16.

### 10.3.2.1 AlexNet

A CNN architecture consisting of eight layers and roughly 61 million parameters, the AlexNet model [67] was first presented. This framework adheres to LeNet-5’s model [68]. The AlexNet method, as depicted in Figure 10.2, utilizes 227 × 227 input image. The Softmax layer makes a distribution using the FC-8 layer’s inputs giving each class a probability rate and guaranteeing that all classes have a total probability of 1.

### 10.3.2.2 VGG16

The VGG16 [69], which clinched the top spot in the ILSVRC-2014 competition, features approximately 138 million parameters. Notably, this architecture consistently employs 3 × 3 filters with stride 1 in its convolution layers and 2 × 2 filters with stride 2 in its maximum pooling layers maintaining the same padding. The maximum pooling and convolution layers are arranged consistently in the VGG16 architecture (see Figure 10.3). The

![](img/5510bd7390ed7002b5774fe8c2be9eff_232_0.png)

Figure 10.3 The architecture of VGG16.

architecture concludes with three fully connected (FC) layers, with the final one employing a Softmax activation function with the first two using ReLU. This 16-layer architecture allows pictures with a resolution of 224 × 224 pixels to be input.

### 10.3.2.3 ResNet50

Several non-linear layers find it difficult to learn identity maps, and the vanishing gradient problem is addressed by the ResNet50 architecture [70], which won first place in the ILSVRC-2015 competition. ResNet50 is built with multiple stacked residual units and has a network-in-network architecture (see Figure 10.4). Residual units serve as the building blocks composed of pooling and convolution layers. This architecture takes 224 × 224 pixel images as input and utilizes 3 × 3 filters similar to VGG16.

![](img/5510bd7390ed7002b5774fe8c2be9eff_232_1.png)

Figure 10.4 The architecture of ResNet50.

### 10.3.2.4 Inception V3

![](img/5510bd7390ed7002b5774fe8c2be9eff_233_0.png)

Figure 10.5 Schematic representation of inception V3.

The third repetition in Google's DL Evolutionary Systems series is known as Inception V3 [71]. Following Szegedy's creation of the Inception V1 design, in Inception V2, batch normalization was introduced. Subsequently, Inception V3 implemented factorization. The primary objective of factorization is to minimize the number of parameters and connections without compromising the network's efficiency. The algorithm incorporates fully connected layers, convolutions, max pooling, average pooling, dropouts, concatenations, as well as symmetrical and asymmetrical building blocks (refer to Figure 10.5). The 42-layer Inception V3 architecture includes an input layer that can handle images up to 299 × 299 pixels in resolution. The Softmax function is incorporated into the last layer of the architecture.

## 10.4 Methodology—E-ENet

The entire framework of the DL-based plant disease identification model E-ENet is illustrated in Figure 10.6 encompassing the following three main steps: localizing plant leaves, segmenting images, and extracting and identifying plant diseases.

The model utilized in this study is primarily composed of the following three steps:

Localization of Diseased Leaves: The RPN—version 2 (RPNv2) algorithm is used to train the leaf dataset in a composite environment to identify diseased leaves. Both the classification neural network and frame regression neural network are used in the same complex environment to find and retrieve diseased leaves.

![](img/5510bd7390ed7002b5774fe8c2be9eff_234_0.png)

Identification of Leaf Disease Species: The third and final step involves identification of leaf disease species. The recognition of plant diseases is accomplished in a simple background using the E-ENet model.

These steps collectively form the comprehensive framework for the deep learning-based plant disease identification model presented in the study.

### 10.4.1 Localization of the Leaf

The RPNv2 method is trained for precise localization and retrieval of diseased plant leaves within a challenging dataset featuring complex backgrounds. This method effectively blends boundary regression and classification neural networks to improve the precision of recognizing and defining diseased areas on plant leaves. To determine whether the content inside the designated boundary box corresponds to an object or background, the classification neural network is essential. Intersection over Union (IoU) is utilized as a critical criterion in training to guarantee efficient learning and precise classification of images according to their relevance to the targeted objects. Boundaries with IoU values greater than 0.5 are annotated as objects, while those with IoU values less than 0.1 are labeled as backgrounds. The relevance between an artificially marked boundary box and a predicted boundary box is computed using the idea of unity. The IoU formula is displayed as follows:

```
IoU = u1/u2 (10.1)
```

where u2 is the total area, and u1 is the overlap area between the artificially marked boundary box and the predicted boundary box. The sigmoid function is chosen as the appropriate loss function for binary classification tasks within the neural network. Represented by four-dimensional variables (x, y, w, h), a single boundary box is characterized by (P_x, P_y, P_w, P_h) as the given boundary box, (G_x, G_y, G_w, G_h) as the target boundary box, and (G'_x1, G'_y1, G'_w1, G'_h1) as the predicted boundary box. The primary objective is to establish a mapping relationship denoted as f for the boundary regression neural network ensuring accurate and precise predictions.

f(P_x, P_y, P_w, P_h) = (G_x^1, G_y^1, G_w^1, G_h^1) and (G_x^1, G_y^1, G_w^1, G_h^1) ≈ (G_x, G_y, G_w, G_h) are defined. The boundary measurement includes pan and zoom. The constraint of pan is (Δx, Δy) given that Δx = P_w d_x(P_1) and Δy = P_h d_y(P_1). The formula is shown as follows:

```
G_x^1 = P_w d_w(P_1) + P_x (10.2)
```

```
G_y^1 = P_h d_h(P_1) + P_y (10.3)
```

The parameter for zoom is denoted as (S_w, S_h), where S_w = exp(d_w(P_1)) and S_h = exp(d_h(P_1)). The formula is expressed as follows:

```
G_w^1 = P_w exp(d_w(P_1)) (10.4)
```

```
G_h^1 = P_h exp(d_h(P_1)) (10.5)
```

In accordance with the provided formula, the actual learning objectives of the boundary regression neural network are denoted as d(P_1) = (d_x(P_1), d_y(P_1), d_w(P_1), d_h(P_1)), and the true transformation parameters between the predicted boundary box and previously annotated boundary box are expressed as t = (t_x, t_y, t_w, t_h).

```
t_x = \frac{G_x - P_x}{P_x} (10.6)
```

```
t_y = \frac{G_y - P_y}{P_y} (10.7)
```

```
t_w = log \frac{G_w}{P_w} (10.8)
```

```
t_h = log \frac{G_h}{P_h} (10.9)
```

The objective function of the boundary regression neural network is represented as d(P1) = w^TP1, where w signifies the learning parameter of the boundary regression neural network. The corresponding loss function is expressed as follows:

```
loss = \sum_{i=1}^N (t_i - d_i(P_1))  (10.10)
```

### 10.4.2 Segmentation of Leaf Image

The model applies an advanced method that builds upon previous steps, the Chan–Vese Level II algorithm, to image segmentation in complex environments. By initializing the zero level set, minimizing the energy function, and iteratively computing leaf profiles, this algorithm skillfully segments images of diseased plant leaves. Unlike surface evolution, which uses an explicit control speed (F), the Chan–Vese Level II algorithm makes use of the level set to create an energy function that fully captures the region.

The contour length is raised to aid in the energy function's merging. The energy function is defined as the minimum sum of variances between the gray values within and outside the contour in the image. To account for a closed curve in the image, the energy function formulation is as follows:

```
E = \mu Length(C_1) + \lambda_1 \int\int_{c1} |u(x, y) - u_1|^2 dxdy + \lambda_2 \int\int_{c2} |u(x, y) - u_2|^2 dxdy  (10.11)
```

The image's gray values are represented by u(x, y), the average gray values in the contour are represented by u1, the average gray values outside the contour are represented by u2, and the image's gray values are represented by c1 and c2. Next, the following are the provided formulas:

```
F1 = \lambda_1 \int\int_{c1} |u(x, y) - u_1|^2 dxdy  (10.12)
```

```
F2 = \lambda_2 \int\int_{c2} |u(x, y) - u_2|^2 dxdy  (10.13)
```

When F1 ≈ 0 and F2 ≈ 0, the computing ends. Level set technique is applied to rectify Equation 10.11 and zero level set is employed to display contour lines. Dirac's function and Heaviside's function are introduced as follows:

