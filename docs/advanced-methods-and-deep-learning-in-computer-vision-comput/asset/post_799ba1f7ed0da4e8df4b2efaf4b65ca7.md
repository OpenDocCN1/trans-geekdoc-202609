
Kambhatla, N., Leen, T.K., 1997. Dimension reduction by local principal component analysis. Neural Computation 9, 1493–1516.

Kingma, D.P., Welling, M., 2014. Auto-encoding variational Bayes. In: Bengio, Y., LeCun, Y. (Eds.), International Conference on Learning Representations. http://dblp.uni-trier.de/db/conf/iclr/iclr2014.html#KingmaW13.

Kong, H., Wang, L., Teoh, E.K., Li, X., Wang, J.G., Venkateswarlu, R., 2005. Generalized 2d principal component analysis for face image representation and recognition. Neural Networks 18, 585–594.

Lee, A.B., Mumford, D., Huang, J., 2001. Occlusion models for natural images: a statistical study of a scale-invariant dead leaves model. International Journal of Computer Vision 41, 35–59.

Liu, D., Hua, G., Chen, T., 2010. A hierarchical visual model for video object summarization. IEEE Transactions on Pattern Analysis and Machine Intelligence 32, 2178–2190.

Locatello, F., Bauer, S., Lucic, M., Rätsch, G., Gelly, S., Schölkopf, B., Bachem, O., 2019. Challenging common assumptions in the unsupervised learning of disentangled representations. In: Proc. of the 36th International Conference on Machine Learning. Long Beach, CA.

Lu, X., Katz, A., Kanterakis, E., Li, Y., Zhang, Y., Caviris, N., 1992. Image analysis via optical wavelet transform. Optics Communications 92, 337–345.

Ma, L., Sun, Q., Georgoulis, S., Van Gool, L., Schiele, B., Fritz, M., 2018. Disentangled person image generation. In: Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition, pp. 99–108.

Mallat, S., Zhang, Z., 1993. Matching pursuit in a time-frequency dictionary. IEEE Transactions on Signal Processing 12, 3397–3451.

Metz, L., Poole, B., Pfau, D., Sohl-Dickstein, J., 2016. Unrolled generative adversarial networks. arXiv preprint. arXiv: 1611.02163.

Mirza, M., Osindero, S., 2014. Conditional generative adversarial nets. arXiv preprint. arXiv:1411.1784.

Mumford, D.B., Shah, J., 1989. Optimal approximations by piecewise smooth functions and associated variational problems. Communications on Pure and Applied Mathematics.

Ng, A., et al., 2011. Sparse Autoencoder. CS294A. Lecture Notes, vol. 72, pp. 1–19.

Poggi, T., Torre, V., Koch, C., 1985. Computational vision and regularization theory. Nature 317, 314–319.

Ren, S., He, K., Girshick, R., Sun, J., 2015. Faster r-cnn: towards real-time object detection with region proposal networks. In: Advances in Neural Information Processing Systems, pp. 91–99.

Roweis, S., Ghahramani, Z., 1999. A unifying review of linear Gaussian models. Neural Computation 11, 305–345.

Shackleton, M., 1994. Learned deformable templates for object recognition. In: IEE Colloquium on Genetic Algorithms in Image Processing and Vision, IET, p. 7.

Szegedy, C., Liu, W., Jia, Y., Sermanet, P., Reed, S., Anguelov, D., Erhan, D., Vanhoucke, V., Rabinovich, A., 2015. Going deeper with convolutions. In: Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition, pp. 1–9.

Tan, Z., Chai, M., Chen, D., Liao, J., Chu, Q., Yuan, L., Tulyakov, S., Yu, N., 2020a. Michigan: multi-input-conditioned hair image generation for portrait editing. ACM Transactions on Graphics (TOG) 39, 95.

Tan, Z., Chen, D., Chu, Q., Chai, M., Liao, J., He, M., Yuan, L., Hua, G., Yu, N., 2020b. Semantic image synthesis via efficient class-adaptive normalization. arXiv preprint. arXiv:2012.04644.

Terzopoulos, D., 1983. Multilevel computational processes for visual surface reconstruction. Computer Vision, Graphics, and Image Processing 24, 52–96.

Tran, L., Yin, X., Liu, X., 2017. Disentangled representation learning gan for pose-invariant face recognition. In: Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition, pp. 1415–1424.

Ulyanov, D., Lebedev, V., Vedaldi, A., Lempitsky, V.S., 2016. Texture networks: feed-forward synthesis of textures and stylized images. In: ICML, p. 4.

Van de Wouwer, G., Scheunders, P., Van Dyck, D., 1999. Statistical texture characterization from discrete wavelet representations. IEEE Transactions on Image Processing 8, 592–598.

Van den Oord, A., Kalchbrenner, N., Espeholt, L., Vinyals, O., Graves, A., et al., 2016. Conditional image generation with pixelcnn decoders. In: Advances in Neural Information Processing Systems, pp. 4790–4798.

Vincent, P., Larochelle, H., Bengio, Y., Manzagol, P.A., 2008. Extracting and composing robust features with denoising autoencoders. In: Proceedings of the 25th International Conference on Machine Learning, pp. 1096–1103.

Wan, Z., Zhang, B., Chen, D., Zhang, P., Chen, D., Liao, J., Wen, F., 2020a. Bringing old photos back to life. In: Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition, pp. 2747–2757.

Wan, Z., Zhang, B., Chen, D., Zhang, P., Chen, D., Liao, J., Wen, F., 2020b. Old photo restoration via deep latent space translation. arXiv preprint. arXiv:2009.07047.

This page intentionally left blank

## CHAPTER 6

## Deep face recognition using full and partial face images

Hassan Ugail

Centre for Visual Computing, University of Bradford, Bradford, United Kingdom

## CHAPTER POINTS

- Methods and practical techniques for deep learning based model definition, training, and testing.
- Examples of using deep learning based models for full and partial face recognition.
- Highlights of the present state of the art in face recognition as well as the challenges in deep learning assisted face recognition.

### 6.1 Introduction

Face recognition is one of the most exciting and prominent applications of deep learning applied in the domain of visual computing. Not only can it showcase the power of deep learning but also it can highlight some of the concerns of using a methodology whereby a black-box approach is utilized for solving problems whose solutions have real-life consequences.

Computer-based face recognition is still riddled with many challenges compared to the face recognition ability of humans. For a human, seeing someone for a brief moment is often enough to learn sufficient about the face of that individual (Young and Burton, 2018). This is because the brain memorizes important details relating to the person. In fact, it seems that when a familiar face is presented within various contexts, the brain compares the ‘before’ and ‘after’ images, without the use of any significant new information. Conversely, the variability of the appearance of a face has a greater effect on the ability of a machine to identify the person from the face.

There are many machine learning algorithms within computer vision specific to face-related functions. These algorithms are either unsupervised techniques, which are not explicitly programmed, or supervised, which are based on the idea that someone can select a portion of data with known labels (provided by the operator) or fed to an algorithm as a training set. For example, Principal Component Analysis (PCA), was introduced in 1905 and is an unsupervised machine learning model widely used for reducing dimensionality in complex data and image compression (Jolliffe, 2002). It has also been a common technique for coding faces in a dataset into the “face space”. In 1991, the Eigenface algorithm was applied to construct face recognition algorithms (Turk and Pentland, 1991). Eigenfaces extract the most important details in the data in the form of eigenvectors corresponding to the largest eigenvalues, representing the variations in the face space. Essentially, in the area of face recognition, the concept of an average face is interesting, and in some ways, it appears to be at the core of human face recognition. Attempts to use the average face as a tool for computer-based face recognition are not uncommon in the published literature, e.g., authors (Elmahmudi and Ugail, 2019a). Also, commonly used is the Local Binary Patterns (LBP) technique, which is a simple yet powerful approach to texture classification. This divides an image into different regions to extract features from each region separately. These features are subsequently used for aiding classification in face recognition tasks (Kas et al., 2020).

In conventional computing, a given algorithm is a group of explicitly programmed commands utilized by a machine to work out a problem. Machine learning approaches permit algorithms to be trained by using input data and to utilize statistical analysis to infer values that fall within a particular domain. For this reason, machine learning enables computers to build models from example data in order to automate a decision-making process, based on data input.

Deep learning (LeCun et al., 2015) is a mechanism by which a machine algorithm can learn by example. It aims to obtain an optimal configuration to a model so that the desired outputs can be obtained from a set of input data. It has been widely used for solving challenging problems in image processing and analysis. As a result, deep learning has probably become the standard de facto technique for use in modern face recognition systems.

Prior to deep learning, a high proportion of face recognition algorithms have utilized image processing techniques such as filtering, histograms and feature coding, containing only two or three layers of computation. There was a significant drawback in such methods, mainly because they can only solve one aspect of the face recognition problem at the expense of the others. For example, while a Gabor filtering method (Dora et al., 2017) can enhance face recognition under varying lighting conditions, that same method can perform poorly in the presence of facial expressions and pose variations. As a result, researchers struggled to come up with a coherent and integral method to solve the bulk of the issues that have plagued face recognition.

However, much of that changed in 2012, when it was decisively demonstrated that deep learning can take care of many of the problems faced by computer-assisted face recognition at the time. At that stage, the AlexNet deep learning model won the ImageNet competition, demonstrating that it was consistently ahead of the game on image recognition. Since then, deep learning has been on an upward trajectory and has stayed ahead of the curve in showing that it can match human performance in face recognition. For example, in 2014, DeepFace on the Labelled Faces in the Wild (LFW) dataset has shown, it can achieve human-level accuracy, the exact figures being 97.35% for DeepFace and 97.533% for humans (Taigman et al., 2014).
