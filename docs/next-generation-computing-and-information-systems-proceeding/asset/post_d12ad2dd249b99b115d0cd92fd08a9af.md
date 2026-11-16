
## 4.1 Preprocessing

A median filter is used to smoothen the images in our proposed study. It can handle pulse noise in higher density when combined with a median filter. The details of the images can be preserved while using this filter.

## 4.2 Feature extraction

The median filter approach is used to accomplish preprocessing, after which the preprocessed pictures are sent to the feature extraction step (Soni et al. 2021). The MRI brain image is used to extract three separate parameters, including Grey Matter Volume and cortical thickness.

## 4.3 Combination kernel for support vector machine

The maximum margin classifier works fine when there is a linear boundary (i.e.) a hyperplane separating both the classes. It does not work when there are no solutions when M>0, for the optimization problem. To address non-linear data, the primary feature space is changed into a higher-dimensional feature space. The original feature space of the kernel is illustrated employing the following Equation (1).

```
K(U, V) = \varphi(U)^T \varphi(V)
```

Given below are the relations for the several kernels.

### Linear Kernel

```
linear_k(U, V) = u^T v + c
```

Where u, v characterize the dot product of linear kernel and constant c.

### Quadratic Kernel

```
quad_k(U, V) = 1 - \frac{\|u - v\|^2}{\|u - v\|^2 + c}
```

Here u, v signify the vectors in the original input space

### Polynomial Kernel

```
poly_k(U, V) = (\lambda u^T v + c)^\theta, \lambda > 0
```

### Sigmoid Kernel

```
sig_k(U, V) = tanh (\lambda u^T v + c), \lambda > 0
```

## 4.4 Whale optimization

Whale Optimization (WO) Algorithm is adopted for the weight optimization. The final score gained by using the WO is dependent on optimization score value (Gupta and Awasthi 2008).

The whale optimization technique encompasses three distinct stages like the act of encircling prey, bubble-net attacking procedure, and hunt for the victim/prey.

### 4.4.1 Encircling the prey/victim

The Humpback whales are competent for discriminating the position of the victim and surrounds them. For the vague location of the most favored is its search area, the current finest contender elucidation is the objective victim or is in its vicinity of the most favored in the WO technique (Sharma et al. 2022).

### 4.4.2 Bubble-net attacking method (exploitation phase)

Following the arithmetical illustration of the bubble-net activities of the humpback whales, two improved techniques are envisaged which are furnished below.

### 4.4.3 Shrinking encircling mechanism

Eq. (3) takes care of reducing the value of an effectively. Specifically, the variation array of V is also reduced through a. By means of stipulating the arbitrary values for A that lies between −1 and 1. The updated location of a search criteria shall be distinctly located by identifying the best among locations with that of the currently updated location

## 5 RESULT AND DISCUSSION

The proposed system is implemented in Apache Spark (Ullah et al. 2019) that has a system configuration as an i5 core processor, 8GB RAM, Windows 10 OS.

### 5.1 Performance evaluation

### 5.1.1 Memory usage

Java Programming with Cloud Sim program elegantly executes the efficient organization of the memory for utilization. Latest objects are produced and arranged in the stack. Memory utilization of the new-fangled technique is effectively estimated in Binary digits (bits) (Figure 1).

### 5.1.2 Running time

Based on the memory attributes, the runtime in the Java Programming with Cloud Sim program is firmly derived. The running time taken is illustrated to the absolute exclusion of the coefficients. The time interval is effectively estimated in milliseconds. Table 1 shows research memory measures were taken based on testing. The optimization time is calculated based on a testing % is 60, 70, 80, and 90. The optimization time for a testing % 60 obtains 6348ms to complete a process (Shah et al. 2023).

Table 1. Proposed research memory measures were taken based on testing %.

| Training % | Memory |
|---|---|
| 60 | 1877527 |
| 70 | 1966548 |
| 80 | 2236584 |
| 90 | 2684484 |

![](img/9eefc6d2972274efeb1680c6a31895e5_46_0.png)

Figure 1. Graphical representation of our proposed memory measures.

We can attain a memory measures value for our proposed prediction of dyslexia it will vary from the training % 60, 70, 80, and 90. In our proposed technique has utilized a small amount of memory is required to complete a process in the testing % 60 has taken a 1877527 ms is required to complete a process.

Figure 2 shows Graphical representation of proposed Accuracy measures

![](img/9eefc6d2972274efeb1680c6a31895e5_47_0.png)

Figure 2. Graphical representation of our proposed accuracy measures.

The efficiency of our proposed research here we have explained the accuracy measures of this study it will be varying from the testing % 60, 70, 80, and 90. Figure 3 shows the Graphical representation of proposed precision measures.

![](img/9eefc6d2972274efeb1680c6a31895e5_47_1.png)

Figure 3. Graphical representation of our proposed precision measures.

We can attain a precision measures value for our proposed prediction of dyslexia it will vary from the training % 60, 70, 80, and 90. In our proposed technique has utilized a least amount of memory is needed to end a process in the testing 60% has taken an 83.24% is required to complete a procedure. Figure 4 shows Graphical representation of proposed study recall measures. Table 2. shows Recall measures of proposed study taken based on training %.

Table 2. Recall measures of our proposed study taken based on training %.

| Training % | Recall |
|---|---|
| 60 | 73.28 |
| 70 | 72.61 |
| 80 | 74.16 |
| 90 | 75.22 |

The proposed combinational kernel-based dyslexia detection approach is evaluated using dyslexia detectors based on SVM Kernel and its variants. The proposed model outperforms the ML and DL-based dyslexia detection models. The proposed model had a high accuracy of 90.36 percent.

![](img/9eefc6d2972274efeb1680c6a31895e5_48_0.png)

Figure 4. Graphical representation of our proposed study recall measures.

### 5.2 Comparative analysis

In the related work section, some of the existing methods are reviewed for the research of our work by considering the limitations of such state-of-art works and to tackle the problems. Figure 5 shows the Accuracy comparison of the proposed models.

![](img/9eefc6d2972274efeb1680c6a31895e5_48_1.png)

Figure 5. Accuracy comparison.

The proposed combinational kernel SVM performs better when compared to existing SVM and Fuzzy models. By using this comparison result, we can evaluate the performance of our proposed work whether it has very good classification efficiency or not (Khan et al. 2022). Table 3 shows the comparative study of the proposed model with the existing models for classification of dyslexia from different types of data such as fMRI images, MRI images, psychological assessments, Handwriting, Eye Movements, and Electroencephalogram signals (Hosseinzadeh et al. 2022).

Table 3. Comparative study of the proposed model with other existing models for detection of dyslexia (Aski et al. 2023; Bhatt and Sharma 2023; Rahkra et al. 2021; Rida et al. 2016; Tharewal et al. 2022; Vyas et al. 2022; Yao et al. 2021).

| Type of Data | Features | Model Proposed | Accuracy % |
|---|---|---|---|
| Electroencephalogram Signals | Maximum peak amplitude, Spectral Flatness and positive region | Ensemble of Support Vector Classifiers | 86.3% |
| Reading and writing assessments | Assessment score of URAWSS test | Decision tree and Random Forest | Decision tree and Random forest performed better than traditional rule based approaches |
| Eye Movements while reading 12 different texts | Age, Font-type, Mean fixations, number of fixations, sum of fixations, no of visits, mean of visits, sum of visits | SVM-classifier for binary class | 80.18 % |
| Reading or writing assessments conducted by teacher and Parent | Assessment score of reading and writing tests | Fuzzy Unordered Rules Induction Algorithm | Fuzzy model was reported to perform better than traditional rule–based approaches |
| Reading and writing performance | Three different range of scores were obtained | Artificial neural networks | 75% |
| EEG signals | Features (Beta band power) extracted by discrete wavelet transform with Daubechies of order 2 | Enhanced K-Nearest Neighbor classifier | Optimal electrode positions in the evaluation of dyslexia is suggested as 8 |
| Handwritten texts, pictures, pictures, and audio | Features extracted from pictures and audio files. | Random Forest | 90% |

## 6 CONCLUSION

In this research, a combinational kernel SVM of linear and quadratic kernel uses brain images for the prediction of dyslexia in distributed environment. Apache Spark MLlib is implemented which is a distributed approach that provides support for big data and overcomes big data processing and execution concerns. As a future advancement, the proposed model can be further improved to predict dyslexia better by considering a greater number of input parameters. In the future, multimodal quantitative MRI techniques can be used for better characterization of brain tissue and fine structure of the developmental curves of developmental dyslexia. The ability and the performance of the existing system shall be improved.

## REFERENCES

- Appadurai, J.P. and Bhargavi, R., 2021. Eye movement feature set and predictive model for dyslexia: Feature set and predictive model for dyslexia. *International Journal of Cognitive Informatics and Natural Intelligence (IJCINI)*, 15(4): 1–22.
- Aski, V.J., Dhaka, V.S., Parashar, A. and Rida, I., 2023. Internet of Things in healthcare: A survey on protocol standards, enabling technologies, WBAN architectures and open issues. *Physical Communication*: 102103.
- Belle, A., Thiagarajan, R., Soroushmehr, S.M., Navidi, F., Beard, D.A. and Najarian, K., 2015. Big data analytics in healthcare. *BioMed research international*, 2015.
- Bhatt, M.W. and Sharma, S., 2023. An object recognition-based neuroscience engineering: A study for future implementations. *Electrica*, 23(2).
- Dhiman, G., Soni, M., Pandey, H.M., Slowik, A. and Kaur, H., 2021. A novel hybrid hypervolume indicator and reference vector adaptation strategies based evolutionary algorithm for many-objective optimization. *Engineering with Computers*, 37: 3017–3035.
