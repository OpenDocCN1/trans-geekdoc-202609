
feature-design step. DBNESR first learns hierarchical representations of feature by greedy layer-wise unsupervised learning in a feed-forward (bottom-up) and back-forward (top-down) manner and then makes more efficient recognition with Softmax regress by supervised learning. As a comparison with the algorithms only based on supervised learning, we again propose and design many kinds of classifiers: BP, HBPNNs, RBF, HRBFNNs, SVM and multiple classification decision fusion classifier

`~?|Ç# ¯+¯?+¶~ <`

experiments validate: Firstly, the proposed DBNESR is optimal for face recognition with the highest and most stable recognition rates; second, the algorithm combining unsupervised and supervised learning has better effect than all supervised learning algorithms; third, hybrid neural networks have better effect than single model neural network; fourth, the average recognition rate and variance of these algorithms in order of the largest to the smallest are respectively shown as DBNESR, MCDFC, SVM, HRBFNNs, RBF, HBPNNs, BP and BP, RBF, HBPNNs, HRBFNNs, SVM, MCDFC, DBNESR; at last, it reflects hierarchical representations of feature by DBNESR in terms of its capability of modeling hard artificial intelligent tasks.

`Keywords:-`

Face Recognition, Unsupervised, Hierarchical

Representations, Hybrid

**INTRODUCTION**

Face recognition (FR) is one of the main areas of investigation in biometrics and computer vision. It has a wide range of applications, including access control, information security, law enforcement and surveillance systems. FR

has caught the great attention from large numbers of research groups and has also achieved a great development in the past few decades \[1\] \[2\] \[3\].

However, FR suffers from some difficulties because of varying illumination conditions, different poses, disguise and facial expressions and so on \[4\]

\[5\] \[6\]. A plenty of FR algorithms have been designed to alleviate these difficulties \[7\] \[8\] \[9\]. FR includes three key steps: image preprocessing, feature extraction and classification. Image preprocessing is essential process before feature extraction and also is the important step in the process of FR. Feature extraction is mainly to give an effective representation of each image, which can reduce the computational complexity of the classification algorithm and enhance the separability of the images to get a higher recognition rate. While classification is to distinguish those extracted 本书版权归Arcler所有

![Image 1417](index-327_1.png)

![Image 1418](index-327_2.png)

![Image 1419](index-327_3.png)

Hierarchical Representations Feature Deep Learning for Face Recognition 301

features with a good classifier. Therefore, an effective face recognition system greatly depends on the appropriate representation of human face features and the good design of classifier \[10\].

<

feature selection methods have been presented, such as: spectral feature selection (SPEC) \[11\], multi-cluster feature selection (MCFS) \[12\], minimum redundancy spectral feature selection (MRSF) \[13\], and joint embedding learning and sparse regression (JELSR) \[14\]. In addition, wavelet transform is popular and widely applied in face recognition system for its multi-resolution character, such as 2-dimensional discrete wavelet transform \[15\], discrete wavelet transform \[16\], fast beta wavelet networks

\[17\], and wavelet based feature selection \[18\] \[19\] \[20\].

After extracting the features, the following work is to design an effective

\#

< ¯~~

{~~+¶~

addition, random weight network (RWN) is proposed in some articles \[26\]

for FR \[28\] \[29\].

interference of noise and redundant information, reduce the effects of environmental factors on images and highlight the important information of features, it is well known that the original face images often need to be

\# #

of the huge computational cost. So PCA and 2D-PCA are used to extract geometric features from preprocessed images, reduce their dimensionality for computation and attain a higher level of separability. At last, we propose a novel deep learning algorithm combining unsupervised and supervised learning named deep belief network embedded with Softmax regress (DBNESR) to learn hierarchical representations for FR; as a comparison with the algorithms only based on supervised learning, again design many

'

of the algorithm.

The proposed DBNESR has several important properties, which are summarized as follows: 1) Through special learning, DBNESR can provide effective hierarchical representations \[30\]. For example, it can capture the intuition that if a certain image feature (or pattern) is useful in some 本书版权归Arcler所有

![Image 1420](index-328_1.png)

![Image 1421](index-328_2.png)

![Image 1422](index-328_3.png)

Deep Learning Algorithms

302

locations of the image, then the same image feature can also be useful in other locations or it can capture higher-order statistics such as corners and

\# #" #

considered (e.g., faces). 2) DBNESR is similar to the multiple nonlinear functions mapping, which can extract complex statistical dependencies

\+ \` |

deep hierarchical representations by re-using and combining intermediate concepts, allowing it to generalize well across a wide variety of computer vision (CV) tasks

others. 3) Further, an end system making use of deep learning hierarchical representations features can be more readily adapted to new domains.

The analysis and experiments are performed on the precise rate of face recognition. The conducted experiments validate: Firstly, the proposed DBNESR is optimal for face recognition with the highest and most stable recognition rates; Second, the deep learning algorithm combining unsupervised and supervised learning has better effect than all supervised learning algorithms; Third, hybrid neural networks has better effect than single model neural network; Fourth, the average recognition rate and variance of these algorithms in order of largest to smallest are respectively shown as DBNESR, MCDFC, SVM, HRBFNNs, RBF, HBPNNs, BP and BP, RBF, HBPNNs, HRBFNNs, SVM, MCDFC, DBNESR; At last, it $ #^

\#

The remainder of this paper is organized as follows. Section 2 reviews the images preprocessing. Section 3 introduces the feature extraction

\#

learning proposed by us. Experimental results are presented and discussed in Section 6. Section 7 gives the concluding remarks.

**IMAGES PREPROCESSING**

Images often appear the phenomenon such as low contrast, being not clear and so on in the process of generation, acquisition, input, etc. of images due to the influence of environmental factors such as the imaging system, noise and light conditions so on. Therefore it needs to make images preprocessing.

The purpose of the preprocessing is to eliminate the interference of noise and redundant information, reduce the effects of environmental factors on images and highlight the important information of images \[31\].

本书版权归Arcler所有

![Image 1423](index-329_1.jpg)

![Image 1424](index-329_2.jpg)

![Image 1425](index-329_3.jpg)

![Image 1426](index-329_4.jpg)

![Image 1427](index-329_5.jpg)

![Image 1428](index-329_6.png)

![Image 1429](index-329_7.png)

![Image 1430](index-329_8.png)

Hierarchical Representations Feature Deep Learning for Face Recognition 303

Images preprocessing usually includes gray of images, images filtering, gray equalization of images, standardization of images, compression of images (or dimensionality-reduced) and so on \[32\]. The process of images preprocessing is as following.

 ¨

smoothing denoising for images. This method not only can effectively restrain the noise but also can very well protect the

\#~

pixel point and all others pixel points within its neighborhood as the size of grey value, sets the median of the sequence as the gray value of the pixel point, as shown in Equation (1).

(1)

»

' #

***2***
