
consumption and time complexity. The algorithm could use 3D pixels belonging to neighbouring slices in considering memory occupancy.

The result of 2D segmentation SRM compared to extended 3D on merging the regions of neighbouring slices is shown in figure 7. These extensions are used in most cases and the dataset is robust. Whereas loading the entire dataset in main memory is not feasible for many real cases. For this, one can utilize multiple slices spanning to overcome the memory issues.

## CONCLUSION

Developing computational techniques like reconstruction analysis, segmentation, physiological signal processing, multimodal imaging, etc., are the major areas where research contributions required. However the chapter proposed helps on the basic study of image processing and its importance in processing image and helping medical descriptor on diagnose of a specific disease. Some fundamental concepts of medical image processing are discussed.

## REFERENCES

Alvarez, L., Guichard, F., Lions, P.L., & Morel, J.M. (1992). Axiomes et équations fundamentals du traitement d’images. Paris 315. C. R. Acad. Sci., 135–138.

Alvarez, L., Lions, P. L., & Morel, J. M. (1992). Image selective smoothing and edge detection by non-linear diffusion. SIAM Journal on Numerical Analysis, 29(3), 845–866. doi:10.1137/0729052

Ando, S. (2000). Consistent gradient operators. IEEE Transactions on Pattern Analysis and Machine Intelligence, 22(3), 252–265. doi:10.1109/34.841757

Angenent, S., Haker, S., & Tannenbaum, A. (2003). Minimizing flows for the Monge-Kantorovich problem. SIAM Journal on Mathematical Analysis, 35(1), 61–97. doi:10.1137/S0036141002410927

Bloch, F. (1946). Nuclear induction. Physical Review, 70, 460–474.

Bloembergen, N., Purcell, E. M., & Pound, R. V. (1948). Relaxation effects in nuclear magnetic resonance absorption. Physical Review, 73(7), 679–712. doi:10.1103/PhysRev.73.679

Canet, D. (1996). Nuclear Magnetic Resonance: Concepts and Methods. John Wiley & Sons.

Hashemi, R. H., & Bradley, W. G. (1997). MRI: The Basics. Baltimore, MD: Williams & Williams. www.cis.rit.edu/htbooks/mri/inside.htm

Liang, Z.P., & Lauterbur, P.C. (1999). Principles of Magnetic Resonance Imaging: a signal processing perspective. IEEE Press.

NessAiver, M. (1997). All You Really Need to Know about MRI Physics. Baltimore, MD: Simply Physics.

Nishimura, D.G. (1996). Principles of Magnetic Resonance Imaging. Academic Press.

Schempp, W. G. (1998). Magnetic Resonance Imaging: Mathematical Foundations and Applications. John Wiley and Sons.

## Chapter 9

### Deep Learning Techniques for Prediction, Detection, and Segmentation of Brain Tumors

Prisilla Jayanthi https://orcid.org/0000-0002-4961-9010 K. G. Reddy College of Engineering and Technology, India

Muralikrishna Iyyanki Defence Research and Development Organisation, India

### ABSTRACT

In deep learning, the main techniques of neural networks, namely artificial neural network, convolutional neural network, recurrent neural network, and deep neural networks, are found to be very effective for medical data analyses. In this chapter, application of the techniques, viz., ANN, CNN, DNN, for detection of tumors in numerical and image data of brain tumor is presented. First, the case of ANN application is discussed for the prediction of the brain tumor for which the disease symptoms data in numerical form is the input. ANN modelling was implemented for classification of human ethnicity. Next the detection of the tumors from images is discussed for which CNN and DNN techniques are implemented. Other techniques discussed in this study are HSV color space, watershed segmentation and morphological operation, fuzzy entropy level set, which are used for segmenting tumor in brain tumor images. The FCN-8 and FCN-16 models are used to produce a semantic segmentation on the various images. In general terms, the techniques of deep learning detected the tumors by training image dataset.

### INTRODUCTION

Deep Learning (DL) techniques include machine learning methods, where learning can be supervised, unsupervised, semi-supervised and reinforcement learning. DL performance is based on neural network (NN) modeling for huge data and requires faster processors for better outcomes. These techniques are very powerful in segmentation and detection of tumors in the healthcare. DL has the potential in transforming healthcare centers. DL in healthcare systems comes with improving accuracy and increasing efficiency. The excellent approaches of DL proved in classification, segmentation, recognition and detection with automated algorithms. DL systems develop and evolve by assisting humans with those tasks at which humans are not good. In this chapter, the approaches of ANN, CNN and DNN in healthcare are highlighted.

DOI: 10.4018/978-1-7998-3591-2.ch009

### DEEP LEARNING TECHNIQUES

This approach is used to build and train neural networks (NN), with high propitious decision-making nodes. An algorithm is said to be deep if the input data is passed through a series of layers before it gives output. The state-of-the-art of DL is focused on training NN models using the backpropagation algorithm. Deep Neural Networks (DNN) is one among the DL technique and all the networks that have more than a two or three layers are DNN. The most popular DL techniques are shown schematically in figure 1 (Brownlee, 2019):

Figure 1. Techniques of Deep Learning

![](img/a636f78302652a9c2ec5900d81fba475_134_0.png)

DL has been dominant in the medical imaging, in which different techniques are used for various analysis purposes. One of such technique of DL named ANN works on the numerical datasets of the patient in healthcare whereas CNN deals with the medical imaging that includes magnetic resonance imaging, digital images and so on.

The four tasks of DL are:

**Image Classification**, that includes two types of classification namely binary and multiclass. It allocates a label to an image.

- Labeling an x-ray comes under binary classification whereas
- Naming a face in the photo is multiclass.

*Image Classification with Localization (Object Localization)* includes class labelling and displaying the object location by a bounding box.

- Classifying different objects like birds and drawing a rectangular box known as bounding box around the birds.
- Labeling a digital image in MRI as cancer with a box around the region.

*Object detection* is the task of image classification with localization. Whenever an image has multiple objects and different objects are to be detected; it requires localization and classification.

- Labeling each element in the satellite image with a bounding box.
- A bounding box and labeling each vehicles, and pedestrians on a road.

*Image segmentation* is the technique of drawing a line around the object detected in the image. The process of dividing an image into segments is called as Image Segmentation. The segmentation identifies the specific pixels in the image that belong to the object image with a fine-grained localization (Brownlee, 2019).

In short, one can classify what are present in an image using classification. Image localization points to the single object position in an image whereas object detection detects the multiple objects in the image. Lastly, image segmentation produces pixel-wise masking on each object in the images. Thus, one can achieve the different shapes of objects in the image using image segmentation (Sharma, 2019). The need of bounding box reduces the range of search for the object features and thereby conserves computing resources: memory allocation and processing time (Zhao, 2017).

In DL, ANN model is a potent tool for ML, propitious to reform the future of AI. DL aims at models that computes and is collection of multiple processing layers to learn data representations with multi-levels abstraction. For solving complex problems, DL provides new sophisticated approaches to train DNN architectures.

### ARTIFICIAL NEURAL NETWORKS

It is known as computing system built with many interconnected processing elements, which processes the information by their dynamic state response to external inputs. ANN comprises of a group of algorithms used in ML and DL. ANNs are a type of models in ML, and called as Multilayer Perceptron (MLP) and its great potential lies in the high-speed processing provided for a massive parallel implementation (Abiodun, 2018).

ANN is one such model that is acquainted by innovations like AI and big data into the healthcare. Huge quantity of raw information is transformed into valuable information which is needed to take decisions for treatment and care. According to Ferguson (2019), many prognostics methods are turning to ANN to discover new insights into healthcare future.
