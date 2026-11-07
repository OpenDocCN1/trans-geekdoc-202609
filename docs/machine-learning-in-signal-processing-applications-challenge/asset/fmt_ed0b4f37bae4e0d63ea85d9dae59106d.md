
### 1.3.2 Nearest Neighbor
To explain the concept of nearest neighbor, let us take an example of a classification problem in machine learning, where the dataset includes a training set and test set. `kNN` algorithm is used to identify similarities and dissimilarities in the data set. It follows a simple approach as in [[18](#ch01.xhtml#r1_18)] where a query point `t` is classified depending on the category of its nearest neighbors in the training set. It is labelled as belonging to that class which is most frequently represented among its `k`-nearest neighbors.

![FIGURE 1.6 K-NN example.](images/Fig01_06.jpg)

[**FIGURE 1.6**](#ch01.xhtml#f1_6b) K-NN example.

Referring to the example in [Figure 1.6](#ch01.xhtml#f1_6), the algorithm or classifier will find the nearest example to the test point using a distance function or metric and will assign the same class as that example. The distance metric commonly used in this classification to measure the similarity is the Euclidean distance. However, there are other distance metrics such as the Manhattan distance and the Minkowski distance that are also used.

### 1.3.3 Hilbert Space
The notion of a Hilbert space emerged from the efforts of a German mathematician David Hilbert to generalize the concept of Euclidean space to an infinite dimensional space. It expands the vector space from the two- and three-dimensional domains to domains with multidimensions or infinite dimensions. Hilbert space includes few additional properties to normal vector spaces such as an inner product operation that allows length and angle measurements. They are complete metric spaces that satisfy the following three properties [[17](#ch01.xhtml#r1_17)]. Here, `F` is considered as a linear vector space.

1. **Positive**: `x`, `x` ≥ 0 , for `x` ∈ `F`; ⟨`x`, `x`⟩ = 0 only if `x` = 0

2. **Symmetry**: $\\left\\langle {x,~y} \\right\\rangle = ~\\left\\langle {y,~x} \\right\\rangle~\\quad\\text{for~}F \\in {\\mathbb{R}}\\quad\\text{;}\\,\\left\\langle {x,~y} \\right\\rangle = ~\\left\\langle \\overline{y,~x} \\right\\rangle\\quad\\text{for}~F \\in {\\mathbb{C}}$

3. **Distributive**: ⟨`x`, `y`[1]+ `y`[2]⟩ = ⟨`x`, `y`[1]⟩ + ⟨`x`, `y`[2]⟩, `x`, `y`[1], `y`[2] ∈ `F`

4. **Multiplicative**: ⟨`λ x`, `y`⟩ = ⟨`λ x`, `y`⟩, for `x`, `y` ∈ `F` and `λ` ∈ ℂ

The advantage of Hilbert space is that there is no restriction on the vector dimensions—they can be finite, infinite, or even functions. Kernel methods in machine learning use Hilbert space to perform dot product computations.

## 1.4 Fusion of Machine Learning in Signal Processing
DSP has laid a foundation for various technologies in the information age including televisions, mobile phones, and MP3 players, to name a few. On the other hand, ML, which is a newcomer in this era, has led to the existence of sensational technologies such as face recognition, voice recognition, image classification, driverless cars, and stock market prediction. While DSP systems extract information through a sequence of processes that include data acquisition, signal conversion, and filtering, the ML technique depends on algorithms to extract information.

Signal processing and machine learning have undergone rapid transformations and seen significant improvements with the advancement in technology and the change in economic demands. Over the recent years, there has been an overwhelming demand for smart devices and gadgets that can interact with the environment which are referred to as human-machine interface (HMI) devices, for example, wearable tech gadgets that can track human activity. While such applications depend on machine learning techniques to mimic human intelligence to learn from the data and offer solutions to real-world problems, it is important to note that they also depend on statistical signal processing and feature extraction techniques. It is evident that modern applications require the fusion of SPML systems to maintain high performance while dealing with big data, high-tech digital sensors, and hardware.

## 1.5 Benefits of Adopting Machine Learning in Signal Processing
Machine learning algorithms learn from the data and continuously improve performance through experience. However, the data generated and stored by smart gadgets or systems are available in enormous volumes, and the term “big data” is used to describe this large-scale data set. Moreover, the data are available in diverse formats such as 2D signals, videos, and images, and traditional signal processing techniques will not come in handy to extract the information hidden in the data. Considering the enormous data sets and diverse formats, it is vital for ML algorithms to perform with high speed and efficiency. The great need to cope with big data and dissimilar formats has led to the adoption of ML algorithms that use intelligent learning methods to extract information and process data with high speed and accuracy.

Artificial intelligence techniques and ML algorithms are widely used in a number of vast and complex applications that require statistical signal processing including bioinformatics, astronomy, environment, and communications, just to name a few. For example, under bioinformatics, several academic researchers have adopted SPML techniques such as short-time Fourier transform (`STFT`) to detect epileptic seizures through EEG data as in [[19](#ch01.xhtml#r1_19)] and [[20](#ch01.xhtml#r1_20)]. As the data keep growing bigger and bigger, some applications in the modern world would even require advanced ML techniques. The performance of traditional ML algorithms may be slow as they require data to be fully loaded into memory for data mining and processing. The inability of such algorithms to learn all the data within a reasonable allotted time may pose a challenge.

Advanced ML techniques such as deep learning have gained a lot of importance in the recent years due to their state-of-the-art performance in terms of speed and deep architecture. Deep learning architecture can capture complex input data patterns outperforming traditional ML techniques in making informed predictions. Especially, the deep learning technique called convolutional neural networks (`CNN`) has been showing some promising results for future work. The continuous evolution of technology and research efforts will definitely give rise to modern applications in various domains with a requirement to learn from multifarious environments, and this is where ML algorithms will play a vital role.

## 1.6 Conclusion
In this chapter, we have given you a crash course on the fundamentals behind signal processing and machine learning including key concepts and terminologies required to proceed with the rest of the chapters in this book. This quick overview would have provided sufficient introductory background information that is enough to get you started with the upcoming chapters in signal processing and machine learning. Specifically, we hope you have developed a mindset and thought process for utilizing the statistical signal processing and machine learning tools for solving real-world problems.
