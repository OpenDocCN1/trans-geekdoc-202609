
Int. J. Electr. Comput. Eng. (IJECE), 14, 3, 3168, 2024, Institute of Advanced Engineering and Science.

- 56. Pertot, I., Kufilk, T., Gordon, I., Freeman, S., Elad, Y., Identifier: a web-based tool for visual plant disease identification, a proof of concept with a case study on strawberry. Comput. Electron. Agric., 84, 144–154, 2012.

- 57. Yang, N., Qian, Y., EL-Mesery, H.S., Zhang, R., Wang, A., Tang, J., Rapid detection of rice disease using microscopy image identification based on the synergistic judgment of texture and shape features and decision tree-confusion matrix method. J. Sci. Food Agric., 99, 14, 6589–6600, 2019.

- 58. Chad, D., Tyr, W.H., Chen, S., et al., Automated identification of northern leaf blight-infected maize plants from field imagery using deep learning. Phytopathology, 107, 1426–1432, 2017.

- 59. Ni, C., Wang, D., Vinson, R., Holmes, M., Tao, Y., Automatic inspection machine for maize kernels based on deep convolutional neural networks. Biosyst. Eng., 178, 131–144, 2019.

- 60. Lu, Y., Yi, S., Zeng, N., Liu, Y., Zhang, Y., Identification of rice diseases using deep convolutional neural networks. Neurocomputing, 267, 378–384, 2017.

- 61. Zhang, Z., Liu, H., Meng, Z., Chen, J., Deep learning-based automatic recognition network of agricultural machinery images. Comput. Electron. Agric., 166, 104978, 2019.

- 62. Zhang, X., Qiao, Y., Meng, F., Fan, C., Zhang, M., Identification of maize leaf diseases using improved deep convolutional neural networks. IEEE Access, 6, 30370–30377, 2018.

- 63. Krishnaswamy, R.A., Raja, P., Anirudh, R., Tomato crop disease classification using pre-trained deep learning algorithm. Procedia Comput. Sci., 133, 1040–1047, 2018.

- 64. Coulibaly, S., Kamsu-Foguem, B., Kamissoko, D., Traore, D., Deep neural networks with transfer learning in millet crop images. Comput. Ind., 108, 115–120, 2019.

- 65. PlantVillage homepage: https://plantvillage.org/ Access: April 2018.

- 66. Hughes, D.P. and Salathe, M., An open access repository of images on plant health to enable the development of mobile disease diagnostics, arXiv preprint arXiv:1511.08060, 2015.

- 67. Gangadevi, E., Rani, R.S., Dhanaraj, R.K., Nayyar, A., Spot-out fruit fly algorithm with simulated annealing optimized SVM for detecting tomato plant diseases. Neural Comput. Appl., 36, 8, 4349–4375, 2023, Springer Science and Business Media LLC.

- 68. LeCun, Y., Boser, B., Denker, J.S., Henderson, D., Howard, R.E., Hubbard, W., Jackel, L.D., Backpropagation Applied to Handwritten Zip Code Recognition. Neural Comput., 1, 541–551, 1989, https://doi.org/10.1162/neco.1989.1.4.541.

- 69. Simonyan, K. and Zisserman, A., Very deep convolutional networks for large-scale image recognition, 2014, arXiv Prepr. arXiv1409.1556.

- 70. He, K., Zhang, X., Ren, S., Sun, J., Deep residual learning for image recognition, 2016, arXiv Prepr. arXiv1512.03385.

- 71. Szegedy, C., Vanhoucke, V., Ioffe, S., Shlens, J., Wojna, Z., Rethinking the inception architecture for computer vision, in: Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition, pp. 2818–2826, 2016.

- 72. Tan, M. and Le, Q.V., EfficientNet: Rethinking model scaling for convolutional neural networks. 36th Int. Conf. Mach. Learn. ICML 2019, 2019-June, pp. 10691–10700, 2019.

## AutoML-Driven Deep Learning for Fake Currency Recognition

T. Bhaskar1* and E. Gangadevi2

1Computer Engineering, Sanjivani College of Engineering, Kopargaon, India
2Loyola College, Chennai, India

### Abstract

False copies of genuine items are referred to as counterfeits. The financial industry is still quite vulnerable to counterfeit money. There are numerous detection techniques, but since there are now free picture manipulation programmers, it has become a significant problem in the banking industry. Finding those key regions for evaluation is the first task because there are many important regions that are represented by currencies. Classifiers can determine if the extracted features are real or not. Without classifiers, we may compare the segmented currency image to the region of the original note. Yet, that is insufficient to determine the authenticity of the specific paper currency image. If we segment the crucial areas, the alignment and edges might not match; therefore, paper money note images might be mistaken for the real thing. To obtain better results, the classifiers will process the extracted features.

The method for currency recognition using image processing is suggested in this chapter. Three elements, color, size, and texture, are utilized in the recognition process with this technique. This technology makes it simpler to check the value of paper currency at anytime and anyplace, and it uses the CNN (Convolutional Neural Network). The integration of AutoML not only accelerates the expansion process but also optimizes the performance of the deep learning models making the system flexible to various currencies and counterfeit systems. This chapter experimented with this approach on all Indian religious groups. The characteristics of paper money are crucial in this recognition.

Keywords: Image processing, AutoML, convolutional neural network (CNN), feature extraction, denomination

*Corresponding author: senthilkumar.n@vit.ac.in

### 11.1 Introduction

Due to fraudulent bills being sold in the market and widespread illiteracy, every nation today struggles to recognize its own currency. For this reason, automatic currency recognition systems are essential. In such a system, accuracy and speed are the two most crucial elements. Moreover, accuracy is more crucial than speed. By examining the salient characteristics, a currency recognizer recognizes the currency and determines the denomination. Researchers suggested a wide range of strategies. A handful of them use internal properties, while others use physical properties (width, length, texture and color). Every issue in the software industry has an answer. Such software solutions allow us to save time and energy. One technique that used image processing to identify cash notes existed in the early 1990s. Unfortunately, this technique does not consider the authentication of the notes. An image input was required for such a system before it begins to do various duties on its behalf.

The banking industry has seen significant technological improvement, which has led to the advent of self-servicing to make transactions easy and customer friendly. Some banks also bring brand-new recognition procedures, such as cash deposit by the user themselves through devices without going to the specific bank. In this situation, a currency recognizer is needed to inspect the money and handle it in accordance with the denominations.

A system based on CNN (Convolution Neural Network) technology is suggested in this work. Different modules are used to identify the currency depending on the structural perspective of the currency notes. The VGG16 model was created to train the specified system and provide improved accuracy.

### 11.2 Literature Review

Principal Features for Indian Currency Recognition [1] was taken as the motivation for this study. In this work, a method for recognizing cash using properties, such as the center numeral, latent image, RBI stamp, form, and micro letter, is proposed. A training data set is provided to prepare training models. For the recognition of paper currency, PCA analysis is explained.

Currency Recognition using Machine Learning [2] technique helps to identify the images accurately. The method for cash recognition using image processing is suggested in this paper. This method is based on the following three unique characteristics: color, size and texture. The method presented in this paper can be used to determine many different national currencies. Only fiat currencies from India will be considered for implementation purposes. This technology makes it easy to check the value of money anytime and anywhere, and it uses CNN (Convolution Neural Network). Every denomination of Indian currency was used in our testing, and the algorithm was able to identify with 95% accuracy. To improve the technique's accuracy, a classification model was created incorporating all of the previously listed parameters. Features of paper money are crucial to this recognition.

Currency recognition using image processing [3] deals with identifying images with respect to size, color, and texture. In this research, a machine learning system that can detect foreign currencies with a high degree of accuracy was provided. The suggested procedure may be used to figure out where a banknote came from, what denomination it is, and how much it is worth. The method relies on the fact that different banknotes from the same country vary in size, color, and text placement to determine the denomination value. This study considered the denominations of 20 as the most popular currencies. Our system can rapidly and precisely locate test notes.

Fake currency detection using an image processing algorithm and machine learning algorithm [4] helps detect currency using suitable algorithms. The question of identifying whether the provided sample currency is fake is covered in this research. Traditional techniques and strategies exist for identifying counterfeit currency based on features including color, width, and serial numbers. In this era of cutting-edge technology and sophisticated computational approaches, which offer 99.9% accuracy for false identification of currency, a number of machine learning strategies are proposed. Beyond algorithms, there are other techniques for detection and identification, including note-specific photo filtering and properties like color, shape, and paper width [5]. According to this research, image processing should come first, then K-Nearest Neighbors to detect fake currency. Due to its excellent accuracy for small data sets, KNN is a promising option for use in computer vision jobs. Utilizing sophisticated computational and mathematical methodologies, for the purpose of authenticating banknotes, this collection contains detailed information about the entities and traits often associated with cash. Machine learning [9, 10] and image processing are used in the processing and extraction of data to achieve the desired results and levels of accuracy.

As previously mentioned, many different systems have been put out in various articles [6–8], although one may infer from their findings that none of the solutions suggested are entirely effective and that it is useless to
