
# Binary Ethnicity Classification

This is a binary ethnicity classification $E$, that aims to differentiate between a given ethnicity $E[p]$ and another person not belonging to that ethnicity $E[NP]$ as accurately as possible. Suppose $x$ represents multiple data points or features belonging to a face image. However, within a real-world scenario, input data for ethnicity classification can be based on either full-face or partial face images. In this case, we can explore both full-face $x^F$ and partial-face $x^{(PF)}$ features for ethnicity classification. Both hand-crafted and deep learning features are incorporated into training. This ethnicity classification problem can be defined as:

$$H(x) = \theta[0] + \theta[1]x, \quad x = x^{(F)} \cup x^{(PF)}, \tag{6.2}$$

where $H(x)$ is the predictor function, $\theta[0]$ and $\theta[1]$ are constant values. The goal should be to find the perfect values of $\theta[0]$ and $\theta[1]$ to make the predictor perform as well as possible. Optimising the predictor $H(x)$ is carried out using the training examples. For each of the training examples, we have an input value $x_{train}$, for which a corresponding output $y$ is known in advance. We find the difference between the known and correct value $y$, and our predicted value $h(x_{train})$.

With enough training examples, these differences provide a useful way to measure the "inaccuracy" of $H(x)$. We can then tweak $H(x)$ by tuning the values of $\theta[0]$ and $\theta[1]$ to make it "less wrong". This process is repeated until the system has converged on the best values for $\theta[0]$ and $\theta[1]$.

## The Dataset

The Pakistani Face Database has been developed by researchers within the University of Bradford, United Kingdom. 100 Pakistani and 100 Non-Pakistani images were selected from the Pakistani face database. The ethnicity of each image was determined by asking the participants to self-identify their ethnicity. For participants of Pakistani origin, eligibility was dependent on whether both the maternal and paternal parents were of Pakistani ethnicity.

All the facial images were cropped around the region of the nose using Photoshop CS6 to generate a sub-dataset of the varied nose regions, as shown in [Figure 6.1](#13_ch6.xhtml#f6_1). To keep all the relevant information, it was ensured that the entire nose was cropped, clearly showing the nasal bridge, the pronasale (nasal tip) as well as the nasal alars (nostrils).

![Figure 6.1: An example of nose images that have been processed using Adobe Photoshop CS6. (The images used have been reproduced in line with the approved ethics from the University of Bradford, UK, and participant consent.)](images/fig6_1_B.jpg)

[Figure 6.1:](#13_ch6.xhtml#f6_1b) An example of nose images that have been processed using Adobe Photoshop CS6. (The images used have been reproduced in line with the approved ethics from the University of Bradford, UK, and participant consent.)

## Methodology

Our approach was to extract nose features using six pre-trained machine learning models: three VGG-based and three deep-learning-based. The models used include `VGG-Face`, `VGG-16`, `VGG-19`, `ResNet-50`, `ResNet-101`, and `ResNet-152`, followed by a discriminative binary classification using a Linear Support Vector Machine. A total of eight experiments were conducted on the following datasets:
1. 2,200 isolated nose crops
2. 1,200 isolated eyes and nose crops
3. 1,200 isolated nose and mouth crops
4. 1,200 isolated mouth and eyes crops

### Data Pre-Processing

All images used in our experiments were resized to 224 × 224 pixels to ensure they conform to the input criteria of the pre-trained models. Furthermore, data augmentation was carried out for the training data using rotations at the degree of 10 right, 10 left, 90°, 180°, and 270° as well as random crops. This led to a minimum of a twelvefold increase in the original data size.

### Feature Extraction

The activation of the last pooling layer of each of the ResNet models was used for feature representation.

In total, three sets of features were retrieved using `ResNet-50`, `ResNet-101`, and `ResNet-152` Neural Networks, per experiment. We decided to exclude the last output layer of the Fully Connected layer (`FC`), since it was trained on a set of different data (i.e., objects) compared to the facial features which are presently used. Additionally, research proves that the lower layers of the Deep Neural Network are adequate in learning generic features.

Comparably, for the VGG feature representation using the `VGG-Face`, `VGG-16`, and `VGG-19` models, we used the middle Fully Connected layer (`FC7`) and discounted `FC6` and `FC8`.

### Classification

Having used machine learning-based feature extraction with `VGG-Face`, `VGG-16`, `VGG-19`, `ResNet-50`, `ResNet-101`, and `ResNet-152` models independently, a linear classifier was employed for the two-category ethnicity classification.

Support Vector Machines (SVMs) are supervised machine learning models that function to identify a hyperplane which best classifies data points within a given data space. Published literature has determined that SVMs is a powerful binary classifier that operates by defining an optimum separating hyperplane between two classes of data.

The SVM algorithm classifies data by defining an optimum separating hyperplane between two data classes, which typically involves solving an optimisation problem. Given a training set:

$$\{(x_i, y_i)\}_{1 \le i \le n}, \quad x_i \in \mathbb{R}^d, \quad y_i \in \{+1, -1\}, \tag{6.3}$$

SVM finds the optimal hyperplanes by solving:

$$
\begin{cases}
\min_{w,b} \frac{1}{2}\| w \|^2 \\
\text{subject to } y_i(w \cdot x + b) \ge 1
\end{cases} \tag{6.4}
$$

for $i = 1, \dots, n$ are the observations, where the weights $w$ and $b$ (the bias) are learned during training. The classifier is learned such that $y_i \in \{+1, -1\}$, where $+1$ denotes images labelled as Pakistani, and $-1$ denotes non-Pakistani images. A k-fold cross-validation technique was employed to evaluate the performance of the pre-trained models.

## Experimental Results

By extracting features from images using three pre-trained deep-learning models: `ResNet-50`, `ResNet-101`, and `ResNet-152`, we achieved results above 90% for the binary classification of a Pakistani nose on a dataset of 2,200 nose images (experiment 1), as shown in [Table 6.1](#13_ch6.xhtml#t6_1).

In contrast, the experiments conducted using the three VGG-based models, namely `VGG-Face`, `VGG-16`, and `VGG-19`, vary between each other and are essentially lower when compared to the ResNet models. The performance accuracies are directly comparable to the ResNet models and demonstrate the finding that the accuracy is poorer with VGG than ResNet. This may be attributable to the finding that the ResNet models are classed as very deep learning models, which are architecturally different and are reported to yield higher accuracies.

**Table 6.1:** Performance accuracy for the binary classification of Pakistani nasal images using residual neural networks.

| Feature Extraction Model | Classifier |
| :--- | :--- |
| | Linear Support Vector Machine (SVM) |
| **ResNet-50** | 94.1% |
| **ResNet-101** | 93.4% |
| **ResNet-152** | 93.6% |

**Table 6.2:** Performance accuracy for the binary classification of Pakistani nasal images using the VGG model.

| Feature Extraction Model | Classifier |
| :--- | :--- |
| | Linear Support Vector Machine (SVM) |
| **VGG-16** | 90.8% |
| **VGG-19** | 87.5% |
| **VGG-Face** | 79.9% |

However, `VGG-16` does outperform `VGG-Face` and `VGG-19` in the binary classification task, as shown in [Table 6.2](#13_ch6.xhtml#t6_2).
