
5. [Arun Senthil, S. and Sundaramoorthy, S.](#ch30.xhtml#R_ref30_5) (2018). Optimal control policy for tracking optimal progression of temperature in a batch reactor - Some insights into the choice of objective function. IFAC Papers Online, 51(1), 112-117.

6. [Billings, S. A.](#ch30.xhtml#R_ref30_6) (2013). Nonlinear system identification: NARMAX methods in the time, frequency, and spatio-temporal domains. John Wiley & Sons. pp. 576. ISBN: 978-1-119-94359-4.

7. [Yadav, E. S., Shettigar J.P., Poojary, S., Chokkadi, S., Jeppu, G., and Indiran, T.](#ch30.xhtml#R_ref30_7) (2021). Data-driven modeling of a pilot plant batch reactor and validation of a nonlinear model predictive controller for dynamic temperature profile tracking. ACS Omega, 6, 16714–16721.

8. [Narwekar, K. and Shah V. A.](#ch30.xhtml#R_ref30_8) (2020). Temperature Control Using Sliding Mode Control: An Experimental Approach. In: Tuba, M., Akashe, S., and Joshi, A. (eds) Information and Communication Technology for Sustainable Development. Advances in Intelligent Systems and Computing. Springer: Singapore, 933.

9. [Narwekar, K. and Shah, V. A.](#ch30.xhtml#R_ref30_9) (2018). Temperature control of reactor using variable structure control. Int. J. Res. Anal. Rev., 5(3), 318-322.

10. [Narwekar, K. and Shah, V. A.](#ch30.xhtml#R_ref30_10) (2018). Level control of coupled tank using sliding mode control. Int. J. Res., 7(IX), 1025-1031.

11. [Narwekar, K. and Shah, V. A.](#ch30.xhtml#R_ref30_11) (2017). Robust temperature control of chemical batch reactor using sliding mode control. Int. J. Sci. Res. Manag. (IJSRM), 07, 6561-6568.

12. [Mishra, S. R., Yadav, E. S., and Indiran, T.](#ch30.xhtml#R_ref30_12) (2023, May). Validation of split range control algorithm on a laboratory scale batch reactor heating system. In AIP Conference Proceedings., 2752(1) 1-5. AIP Publishing.

13. [Shettigar, J. P., Pai, A., Joshi, Y., Indiran, T., and Chokkadi, S.](#ch30.xhtml#R_ref30_13) (2023). Validation of nonlinear PID controllers on a lab-scale batch reactor. Comm. Comp. Inform. Sci., 1797, 47-59.

14. [Bala Abhirami, M. and Thirunavukkarasu, I.](#ch30.xhtml#R_ref30_14) (2023). Maximum sensitivity-based PID controller for a lab-scale batch reactor. Lec. Notes Elec. Engg., 957, 183-194.

# 31 3D Image Modeling Using Data Science

Nishita Sharma, Divyanshi Mishra^([^(31)](#fn31))

Department of CSE, Dronacharya Group of Institution, Greater Noida, U. P., India

## Abstract

People today are embracing numerous modernization tactics and eschewing time-consuming procedures. The goal of this work is to design a system that can convert a diagram or figure that is on paper into digital image that can be reproduced or changed in a digital environment. Time is a crucial factor that plays a significant part in any operation, whether it involves a human or a machine. The concept of artificial intelligence (AI), machine learning (M), deep learning, vision API, etc., all can be used to help a system design the image of any figure or diagram directly so that it can print the image of any scanned image into 3D modeled image. We have used deep neural networks that can be trained and used for a variety of tasks with the aid of tensor flow. Other technologies that are used are in this model RPN/OCR/GAN/VECTOR imaging and convolutional neural networks (CNN), these works together for detection, visualization, generation, fetching and extracting the processed data in a digital format. These dependencies may be required to provide certain functionality or to use specific program features. The recycler view a user interface element called recycler view enables us to make scrolling lists. The software’s integrated 3D viewer will then be used to preview our final output 3D matched image. In the future, this model will be able to pick up new techniques, approaches, and patterns on its own, which will be a significant advancement in the field of 3D image modeling.

**Keywords:** Data science, artificial intelligence, machine learning and 3D modeling

## 1. Introduction

One of the most in-demand activities is designing or using a handwritten piece in digital format. The idea of turning a physical image into a three-dimensional (3D) model makes it simple to use and comprehend through virtual models, depending on the user’s demands. While it is possible to transfer text and images into digital formats, there is still work to be done in the area of digitally turning drawn figures into 3D models. In this field, research is conducted on image processing to extract useful information from images, automate processes linked to images, and use convolutional neural networks (CNNs) to make predictions based on image data. Data science contributes significantly to the modeling of digital 3D images by offering methods and resources for data analysis and image manipulation using statistical modeling, machine learning algorithms, and pattern recognition, among other techniques. It enables feature extraction, signal and dimensional enhancements, image restoration and object identification.

In the previous researches on text to image using deep learning, the generative adversarial network (GAN) technique was employed for picture generation and discrimination. Using GAN in conjunction with the natural language toolkit (NLTK), a digital 2D image of the text was produced in order to comprehend the pattern of text in photographs. Using the supplied data, the graphical user interface (GUI) was utilized to create visually appealing windows for the user interface and display the photographs more suitably \[[1](#ch31.xhtml#ref31_1)\]. However, while this technology cannot translate words into 3D models, it can only provide a 2D representation of the language that the user submits.

Another study on the conversion of 2D–3D images describes how different algorithms are used to analyze the 2D image’s depth dimensions before using techniques to turn it into a 3D model. To create an image that resembles the given 2D, KNN search is used to distinguish between relevant and irrelevant images. The dimensions, edges, and closest neighbor points have been guided by depth fusion combined with cross-bias filtering in depth to create an accurate image of the 2D photograph \[[2](#ch31.xhtml#ref31_2)\]. This paper’s goal is to synthesis research studies and data science algorithms that will facilitate the direct conversion of text into a digital 3D model and the conversion of physically drawn images into 3D models for easier comprehension and a more user-friendly human-computer interface. In this paper, model training and tracking are implemented using the tensor flow platform for training deep neural networks. In addition to vector imaging, another algorithm used to generate realistic data is GAN. This process turns handwritten inputs into vector-based representations, which makes it simpler to manipulate and transform the inputs using deep learning to create 3D models digitally. Important parts of text detection systems use algorithms like region proposal network (RPN) and optical character recognition (OCR). OCR can be used to accurately recognize and disguise handwritten characters into digital representation. These two algorithms can be used to process each part independently and produce a highly accurate and precise 3D model. Through the use of these algorithms and techniques, 3D images created by the software from original handwrite inputs is displayed using 3D viewer and scanner to facilitating an effective human-computer interface.

## 2. Literature Review
