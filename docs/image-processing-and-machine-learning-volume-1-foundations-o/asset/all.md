![](images/9781003829157.jpg)

![Cover: Image Processing and Machine Learning, Volume 1: Foundations of Image Processing, edited by Erik Cuevas, Alma Nayeli Rodríguez, published by Routledge, Taylor and Francis Group.](images/9781003829157.jpg)

MATLAB^® is a trademark of The MathWorks, Inc. and is used with permission. The MathWorks does not warrant the accuracy of the text or exercises in this book. This book’s use or discussion of MATLAB^® software or related products does not constitute endorsement or sponsorship by The MathWorks of a particular pedagogical approach or particular use of the MATLAB^® software.

First edition published 2024

by CRC Press

2385 NW Executive Center Drive, Suite 320, Boca Raton FL 33431

and by CRC Press

4 Park Square, Milton Park, Abingdon, Oxon, OX14 4RN

*CRC Press is an imprint of Taylor & Francis Group, LLC*

© 2024 Erik Cuevas and Alma Rodríguez

Reasonable efforts have been made to publish reliable data and information, but the author and publisher cannot assume responsibility for the validity of all materials or the consequences of their use. The authors and publishers have attempted to trace the copyright holders of all material reproduced in this publication and apologize to copyright holders if permission to publish in this form has not been obtained. If any copyright material has not been acknowledged please write and let us know so we may rectify in any future reprint.

Except as permitted under U.S. Copyright Law, no part of this book may be reprinted, reproduced, transmitted, or utilized in any form by any electronic, mechanical, or other means, now known or hereafter invented, including photocopying, microfilming, and recording, or in any information storage or retrieval system, without written permission from the publishers.

For permission to photocopy or use material electronically from this work, access [www.copyright.com](http://www.copyright.com) or contact the Copyright Clearance Center, Inc. (CCC), 222 Rosewood Drive, Danvers, MA 01923, 978-750-8400. For works that are not available on CCC please contact [mpkbookspermissions@tandf.co.uk](mailto:mpkbookspermissions@tandf.co.uk)

*Trademark notice*: Product or corporate names may be trademarks or registered trademarks and are used only for identification and explanation without intent to infringe.

ISBN: 978-1-032-23458-8 (hbk)

ISBN: 978-1-032-26260-4 (pbk)

ISBN: 978-1-003-28741-4 (ebk)

DOI: [10.1201/9781003287414](https://doi.org/10.1201/9781003287414)

Typeset in Palatino

by codeMantra

# Preface Volume 1

Image processing is an important area of research because it enables the improvement and manipulation of images for various applications, such as medical imaging, wherein it plays a crucial role in the analysis and diagnosis of X-rays, CT scans, and MRI images. Image processing algorithms can be used in surveillance systems to detect and track objects, enhance image quality, and perform facial recognition. In remote sensing, image processing techniques are used to analyze satellite and aerial images for various purposes such as environmental monitoring and resource management. In multimedia, it is used in applications to enhance and manipulate images for display, such as in photo editing software and video games. Overall, image processing has a wide range of applications and has become a critical tool in many industries, making it an important area of study and research.

Machine learning (ML) is a research field part of artificial intelligence that allows to learn from data and make predictions or decisions without being explicitly programmed. Some of the main applications of ML include automation, where ML algorithms can automate tasks that would otherwise require human intervention, reducing errors and increasing efficiency. In predictive analytics, ML models can analyze large amounts of data to identify patterns and make predictions, which can be used in various applications such as stock market analysis, fraud detection, and customer behavior analysis. In decision-making, ML algorithms can help organizations make better and more informed decisions by providing insights and recommendations based on data.

The combination of image processing and ML involves the use of techniques from both fields to analyze and understand images. Image processing techniques are used to pre-process the images, such as filtering, segmentation, and feature extraction, while ML algorithms are used to analyze and interpret the processed data such as classification, clustering, and object detection. The goal is to use the strengths of each field to build computer vision systems that can automatically understand and analyze images without human intervention. With this combination, image processing techniques can enhance the quality of the images, which improves the performance of ML algorithms. On the other hand, ML algorithms can automatically analyze and interpret images, which reduces the need for manual intervention.

Our primary objective was to create a comprehensive textbook that serves as an invaluable resource for an image processing class. With this goal in mind, we carefully crafted a book that encompasses both the theoretical foundations and practical applications of the most prevalent image processing methods. From pixel operations to geometric transformations, spatial filtering to image segmentation, and edge detection to color image processing, we have meticulously covered a wide range of topics essential to understanding and working with images. Moreover, recognizing the increasing relevance of ML in image processing, we have incorporated fundamental ML concepts and their applications in this field. By introducing readers to these concepts, we aim to equip them with the necessary knowledge to leverage ML techniques for various image processing tasks. Our ultimate aspiration is for this book to be a valuable companion for students and practitioners alike, providing them with a solid understanding of image processing fundamentals and empowering them to apply these techniques in real-world scenarios.

To cover all the important information, the inclusion of numerous chapters and programs is necessary. Consequently, the resulting book contained a substantial amount of content and programming examples. However, recognizing that a single-volume book with a multitude of chapters and programs can be overwhelming for readers, the decision to divide the book into two volumes was made. This division was undertaken with the primary objective of ensuring that the book was appropriately handled and comprehended by readers. The book becomes more approachable and manageable by splitting the material into two volumes, preventing readers from feeling overwhelmed by the sheer volume of the information. This thoughtful division facilitates a smoother learning experience, allowing readers to navigate through the content more effectively, delve deeper into the material, and absorb concepts and techniques at their own pace. Ultimately, the decision to divide the book into two volumes serves the purpose of optimizing readers’ understanding and engagement with the extensive materials and programs presented within its pages.

With the objective of ensuring that the book can be effectively navigated and comprehended by readers, we have made the decision to divide it into two volumes. Volume 1: “Foundations of Image Processing” and Volume 2: “Advanced Topics in Image Analysis and Machine Learning”.

Volume 1 covers the fundamental concepts and techniques in image processing, starting with pixel operations and their properties and exploring spatial filtering, edge detection, image segmentation, corner detection, and geometric transformations. It provides a solid foundation for readers interested in understanding the core principles and practical applications of image processing. By focusing on these initial six chapters, the volume establishes the essential groundwork necessary for further exploration in the field. Building upon the knowledge gained from Volume 1, Volume 2 considers more advanced topics in image analysis. It covers a range of subjects, including morphological filters, color image processing, image matching, feature-based segmentation using the mean-shift algorithm, and finally, the application of singular value decomposition (SVD) for image compression. In addition to covering the advanced concepts and techniques of image processing, Volume 2 provides several important ML techniques as applied to the field. Recognizing the increasing significance of ML in image analysis and understanding its potential for enhancing image processing tasks, we have incorporated relevant ML approaches throughout Volume 2.

The division into two volumes was aimed at ensuring that each volume could stand alone as a self-contained resource. This means that readers have the flexibility to review and study each volume independently, without necessarily relying on the other volume for context or understanding. By maintaining a self-contained structure, readers can approach the material in a modular manner, focusing on specific aspects or revisiting specific chapters as needed.

Welcome to Volume 1 of our book. This volume serves as an introduction to the fundamental concepts and techniques in image processing. It lays the groundwork for understanding the core principles and practical applications of image processing. By focusing on these fundamental topics, Volume 1 aims to provide readers with a solid understanding of the core concepts and techniques in image processing. It forms the basis upon which you can further explore advanced topics and ML applications in Volume 2. Whether you are a student or a practitioner in the field, this volume will equip you with the necessary knowledge to approach image processing tasks with confidence and understanding.

Many books on image processing techniques are geared toward readers with a strong mathematical background. Upon reviewing various related books, the authors noticed the need for a more general and less technical approach to these topics to attract a wider audience of readers and students. This book includes all the topics found in other similar books, but with a greater emphasis on explaining, putting into practice, and utilizing the methods, and less emphasis on the mathematical details.

This book not only covers the key concepts and techniques of image processing but also provides a substantial amount of code and implementations. The authors view this as an important aspect of the book. Even those readers with strong mathematical abilities can struggle to fully grasp a particular approach until they see it in code. By implementing algorithms and methods in code, any confusion or uncertainty is removed, making the material easier to understand and transmit. With this approach, as the reader progresses through the book from simpler to more advanced methods, the focus on computation (the implemented code) allows them to see the various models and reinforce their mathematical understanding.

Many comparable books only focus on the theoretical aspect, while those that cover practical implementations usually present a general approach to developing algorithms from scratch. Our teaching experience has shown that students understand the material faster when they have access to code that they can modify and experiment with. This book uses MATLAB^® as the programming language to implement the systems, due to its popularity among engineers and its extensive library collection for various disciplines. Other programming languages such as Java, R, C++, and Python are also used in engineering, but MATLAB stands out for its distinctive features.

For beginner readers, the numerous computational methods used in image processing can be overwhelming due to the vast number of mathematical concepts and techniques involved. Some practical books attempt to address this issue by offering chapters on how to use pre-existing recipes. However, what if the assumptions of the problem are not met? In such cases, it becomes necessary to modify or adapt the algorithm. To accomplish this, it’s crucial that the book provides the conceptual understanding needed to appreciate and comprehend the underlying mathematics. The aim of this book is to strike a balance by offering a comprehensive yet accessible view of the most commonly used computational algorithms and popular image processing approaches, with a focus on rigor.

Despite the heavy mathematical concepts involved in image processing methods, it is possible to utilize these models without a deep understanding of their mathematical foundations. For many readers, learning image processing through programming instead of a complex mathematical model is a more feasible goal. This book aims to fulfill this objective.

The teaching of image processing can be effective by blending theoretical knowledge with hands-on computer exercises, allowing students to write their own code for processing image data. As image processing principles are widely used in various fields, such as ML and data analysis, there is a growing demand for engineers who are proficient in these concepts. Many universities respond to this need by offering comprehensive courses in image processing that cover the most widely used techniques. Image processing is perceived as a highly practical subject, inspiring students to see how image transformations can be transformed into code to produce visually appealing effects.

The material has been compiled from a teaching perspective. For this reason, the book is primarily intended as a textbook for undergraduate and postgraduate students of Science, Electrical Engineering, or Computational Mathematics. It is appropriate for courses such as image processing, computer vision, artificial vision, advanced methods, and image understanding. The book was conceived as a complete course that can be covered in a semester.

Volume 1 is organized in a way that allows readers to easily understand the goal of each chapter and reinforce their understanding through practical exercises using MATLAB programs. It consists of six chapters; the details of each chapter are described below.

**[Chapter 1](#C_004_c1.xhtml)** explores pixel operations, their properties, and how they are applied in image processing. It also explains the relationship between image histograms and pixel operations and includes numerical examples using MATLAB to help illustrate the concepts.

**[Chapter 2](#C_005_c2.xhtml)** focuses on the analysis of spatial filtering, which involves modifying each pixel of an image by considering not only its original value but also the values of its neighboring elements.

In **[Chapter 3](#C_006_c3.xhtml)**, the concepts of the edges or contours of an image are described, which corresponds to an important component for image analysis. The main existing methods for locating edges, their properties, and particularities, which are implemented in MATLAB for the reader’s understanding, are also addressed.

**[Chapter 4](#C_007_c4.xhtml)** covers the topic of image segmentation and the treatment of binary images. Segmentation involves isolating each individual binary object in an image. After isolating these objects, various properties such as the number of objects, their position, and the number of pixels that make up the object can be evaluated.

**[Chapter 5](#C_008_c5.xhtml)** outlines the main methods for identifying corners, their key properties, defining equations, and implementation in MATLAB.

In **[Chapter 6](#C_009_c6.xhtml)**, the primary methods for detecting geometric shapes, such as lines or circles, are covered.

Over a span of more than 5 years, we conducted extensive testing and experimentation to effectively present this material to diverse audiences. Furthermore, we are deeply grateful for the unwavering support and tolerance we received from our students, particularly those from the CUCEI at the University of Guadalajara, Mexico. The invaluable collaborations, assistance, and discussions with our colleagues throughout this journey could fill an additional chapter. We extend our sincerest gratitude to all those who have contributed to this endeavor.

**Erik Cuevas**

**Alma Nayeli Rodriguez**

*Guadalajara, Jalisco, Mexico*

# 1 Pixel Operations

DOI: [10.1201/9781003287414-1](https://doi.org/10.1201/9781003287414-1)

## 1.1 Introduction

Pixel operations refer to those operations performed on images where only the pixel value of interest *p* = *I*(*x*,*y*) from the image is considered \[[1](#C_004_c1.xhtml#r1_1)\]. Each new pixel value calculated *p*^′ = *I*^′(*x*,*y*) is dependent on the value of the original pixel *p* = *I*(*x*,*y*) at the same position. Thus, it is independent of the values of other pixels, such as its closest neighbors. The new pixel value is determined through a function *f*\[*I*(*x*,*y*)\], so that:

*f*\[*I*(*x*,*y*)\]→*I*^′(*x*,*y*) (1.1)

[Figure 1.1](#C_004_c1.xhtml#f1_1) shows a representation of this type of operation. If, as in the previous case, the function *f*(⋅) is independent of the image coordinates, its values do not depend on the pixel position, so the function is called homogeneous. Examples of typical homogeneous operations are:

![FIGURE 1.1 Representation of pixel operations, in which the resulting pixel depends only on the value of the function operating on the original pixel.](images/Fig01_01.jpg)

[**FIGURE 1.1**](#C_004_c1.xhtml#f1_1b) Representation of pixel operations, in which the resulting pixel depends only on the value of the function operating on the original pixel.

*   Contrast and illumination changes in the image
*   Application of certain illumination curves
*   Inverting or complementing an image
*   Threshold segmentation of an image
*   Gamma correction of an image
*   The color transformation of an image

On the other hand, non-homogeneous pixel operations consider not only the value of the pixel in question but also its relative position in the image, that is *I*^′(*x*,*y*).

*g*\[*I*(*x*,*y*),*x*,*y*\]→*I*^′(*x*,*y*) (1.2)

A frequent operation performed on images using non-homogeneous operations is the changing of contrast or illumination of an image depending on the position of the pixel in the image. Under such conditions, some image pixels will be strongly altered, while other elements will present only small effects.

## 1.2 Changing the Pixel Intensity Value

### 1.2.1 Contrast and Illumination or Brightness

The contrast of an image can be defined as the relationship between the different intensity values present in the whole image \[[2](#C_004_c1.xhtml#r1_2)\]. The contrast is related to how the intensity values are distributed \[[3](#C_004_c1.xhtml#r1_3)\]. Suppose they are concentrated toward lower intensity values. In that case, the image will appear darker. In contrast, if the intensity values are concentrated toward higher intensity values, the image will appear bright or illuminated. To exemplify these conditions, we can present examples of increasing the contrast of an image by 50%, which would be equivalent to applying a homogeneous function that multiplies the pixel by 1.5. Another example can be to increase the illumination or brightness by 100 levels, which would be equivalent to employing a function that adds 100 units to the pixel in question. Thus, the homogeneous function can be defined as follows:

*f*[*c*](*I*(*x*,*y*)) = *I*(*x*,*y*) ⋅ 1.5 (1.3)

*f*[*h*](*I*(*x*,*y*)) = *I*(*x*,*y*) + 100 (1.4)

The generic operator *f*(⋅), which is used to modify the contrast or illumination in an image, can be formulated as follows:

*I*(*x*,*y*) = *f*(*x*,*y*) = *c* ⋅ *I*(*x*,*y*) + *b*; (1.5)

where *c* modifies the contrast value and *b* changes the brightness or illumination value, [Figure 1.2](#C_004_c1.xhtml#f1_2) shows graphically the different effects produced by distinct values of *c* and *b*.

![FIGURE 1.2 Graphical representation of the mapping generated for the resulting pixel I′(x, y): (a) when changing the value of c in Equation 1.5 with b = 0, and (b) when changing the value of b in Equation 1.5 with c = 1.](images/Fig01_02.jpg)

[**FIGURE 1.2**](#C_004_c1.xhtml#f1_2b) Graphical representation of the mapping generated for the resulting pixel *I*′(*x*, *y*): (a) when changing the value of *c* in Equation 1.5 with *b* = 0, and (b) when changing the value of *b* in Equation 1.5 with *c* = 1.

[Figure 1.3](#C_004_c1.xhtml#f1_3) shows the result of applying the above homogeneous operations on an image.

![FIGURE 1.3 Examples of applying homogeneous pixel operations. (a) Original image, (b) image with 50% contrast increment, and (c) image with illumination decreased by 100 levels.](images/Fig01_03.jpg)

[**FIGURE 1.3**](#C_004_c1.xhtml#f1_3b) Examples of applying homogeneous pixel operations. (a) Original image, (b) image with 50% contrast increment, and (c) image with illumination decreased by 100 levels.

### 1.2.2 Delimitation of Results by Pixel Operations

When homogeneous operations are used, the calculated pixel value may exceed the limited value defined by the 8-bit grayscale images. Therefore, new pixel values could fall outside the range of 0–255. If this situation happens, the image data type automatically changes from integer (uint8) to float (double). If you write programs in a language such as C, you need to avoid this problem by using appropriate instructions. One example to protect the program when the pixel value exceeds the upper limit is considered as follows:

```
If (Ixy > 255)
Ixy = 255;
```

The previous operation will have the effect of eliminating any excess produced by the application of the homogeneous operation on the image. This effect is often referred to in the literature as “clamping.” Another problem in the use of homogeneous operations performed on pixels occurs when the calculated value of the new pixel is less than the lower limit defined for an 8-bit grayscale image. This can happen when the value of the illumination is reduced to some levels, producing negative values. This problem, as well as the previous one, is avoided if the program is protected with the following instructions:

```
If (Ixy < 0)
Ixy = 0;
```

### 1.2.3 Image Complement

Image complement or inversion is considered a pixel operation in which the pixel value is altered in the opposite direction (by multiplying the pixel value by −1), while on the other hand, a constant intensity value is added. Under this operation, the result falls within the allowed range of values. For one pixel *p* = *I*(*x*,*y*) on range of values \[0,*p*[max]\] the complement or inversion operation is defined as:

*f*[inv](*p*) = *p*[max] − *p* (1.6)

To implement the complement operation of an image in MATLAB^®, it is necessary to perform the code shown below:

```
I=imread(‘extension’);
 Ig=rgb2gray(I);
IC=255-Ig;
```

Where `IC` is the result of the complement corresponding to the image stored in `I`. [Figure 1.4](#C_004_c1.xhtml#f1_4) shows the effect of having applied the complement on an image using the previous code in MATLAB.

![FIGURE 1.4 Result of applying the complement pixel operation to an image. (a) Original grayscale image and (b) complement.](images/Fig01_04.jpg)

[**FIGURE 1.4**](#C_004_c1.xhtml#f1_4b) Result of applying the complement pixel operation to an image. (a) Original grayscale image and (b) complement.

### 1.2.4 Segmentation by Threshold

Segmentation by thresholding can be considered a special form of quantification in which the image pixels are divided into two classes depending on their relationship with a predefined threshold value *p*[th]. All pixels in the image assume two different values *p*[0] or *p*[1] depending on their relationship to the threshold, formally defined as:

$f\_{\\text{th}}\\left( p \\right) = \\left\\{ \\begin{matrix} {p\_{0}\\text{~\\ \\ si~}p < p\_{\\text{th}}} \\\\ {p\_{1}\\text{~\\ \\ si~}p \\geq p\_{\\text{th}}} \\\\ \\end{matrix} \\right.$ (1.7)

where 0 < *p*[th] < *p*[max]. A frequent application of this operation is the binarization of a grayscale image by considering a *p*[0] = 0 y *p*[1] = 1. An example of applying segmentation by using thresholding on an image is shown in [Figure 1.5](#C_004_c1.xhtml#f1_5). The effect of binarization can be clearly seen in the resulting histogram of the image, where the whole distribution is divided into only two parts *p*[0] y *p*[1] as shown in [Figure 1.6](#C_004_c1.xhtml#f1_6).

![FIGURE 1.5 Example showing the application of segmentation by using thresholding on an image, considering p0 = 0, p1 = 1 y pth = 80. In addition, (c) and (d) show the respective histograms of (a) and (b).](images/Fig01_05.jpg)

[**FIGURE 1.5**](#C_004_c1.xhtml#f1_5b) Example showing the application of segmentation by using thresholding on an image, considering *p*[0] = 0, *p*[1] = 1 y *p*[th] = 80. In addition, (c) and (d) show the respective histograms of (a) and (b).

![FIGURE 1.6 The effect of the binarization operation on the histogram. The threshold value is pth. (left) Original histogram and (right) histogram resulting from the operation, concentrating their values at two different points. p0 y p1.](images/Fig01_06.jpg)

[**FIGURE 1.6**](#C_004_c1.xhtml#f1_6b) The effect of the binarization operation on the histogram. The threshold value is *p*[th]. (left) Original histogram and (right) histogram resulting from the operation, concentrating their values at two different points. *p*[0] y *p*[1].

## 1.3 Histogram and Pixel Operations

In some cases, the effects of pixel operations can be easily detected through the histogram. Histograms can be considered as a statistical index of the image. It is usually used as an element to assist in the evaluation of important properties of an image \[[4](#C_004_c1.xhtml#r1_4)\]. Especially, errors produced in image acquisition are easily recognized through the use of histograms. In addition to the ability to deal with the problems mentioned above, it is also possible to pre-process the image based on the histogram to improve it or to highlight features of the image that will be extracted or analyzed in later processing steps (e.g., by considering a pattern recognition system in the image).

### 1.3.1 Histogram

Histograms are elements that describe the frequency at which the intensity values (pixels) of the image are distributed. In the simplest case, histograms are best understood when they describe the distribution of grayscale images. An example is shown in [Figure 1.7](#C_004_c1.xhtml#f1_7). For a grayscale image *I*(*u*,*v*) with intensities in the range \[0,*K*−1\] generate a histogram *H* with exactly *K* different values. Therefore, for a typical 8-bit grayscale image, a histogram will use *H* = 2⁸ = 256. Each element of the histogram is defined as *h*(*i*),  corresponding to the number of pixels in the image with an intensity value *i*, for all values of 0 ≤ *i* < *K*. This can be expressed as follows:

![FIGURE 1.7 (a) 8-bit intensity (grayscale) image and (b) its histogram.](images/Fig01_07.jpg)

[**FIGURE 1.7**](#C_004_c1.xhtml#f1_7b) (a) 8-bit intensity (grayscale) image and (b) its histogram.

*h*(*i*) = card¹{(*u*,*v*)|*I*(*u*,*v*)=*i*} (1.8)

*h*(0) is then the number of pixels with the value 0, *h*(1) the number of pixels that have the value of 1, and so on, while finally *h*(255) represents the number of white pixels (with the maximum intensity value) in the image. As a result of the histogram calculation, a one-dimensional vector *h* with a length *K* is obtained, as shown in [Figure 1.8](#C_004_c1.xhtml#f1_8) where *K* = 16.

![FIGURE 1.8 The vector of a histogram with 16 possible intensity values. The index of the elements of the vector i = 0…15 represents the intensity value. The value of 9 of intensity 2 means that in the corresponding image, the intensity value 2 appears 9 times.](images/Fig01_08.jpg)

[**FIGURE 1.8**](#C_004_c1.xhtml#f1_8b) The vector of a histogram with 16 possible intensity values. The index of the elements of the vector *i* = 0…15 represents the intensity value. The value of 9 of intensity 2 means that in the corresponding image, the intensity value 2 appears 9 times.

The histogram shows important characteristics of an image, such as its contrast and dynamic range, which are attributed to the image acquisition and need to be evaluated for correcting levels so that image properties can be analyzed more clearly in the post-processing stages.

Evidently, the histogram does not provide information about the spatial distribution of the pixels. Therefore, the information provided by the histogram presents a loss of information about the spatial relationship that the pixels had in the image. Under such conditions, it is impossible to reconstruct an image using only the information from its histogram. To exemplify this fact, [Figure 1.9](#C_004_c1.xhtml#f1_9) shows three different images that produce the same histogram.

![FIGURE 1.9 Three different images that produce the same histogram.](images/Fig01_09.jpg)

[**FIGURE 1.9**](#C_004_c1.xhtml#f1_9b) Three different images that produce the same histogram.

### 1.3.2 Image Acquisition Characteristics

Histograms show important characteristics of an image, such as contrast and dynamics, which are problems that occur during image acquisition and have consequences for the subsequent processing steps. In the following, important concepts to consider regarding the acquisition of an image and its histogram are explained.

#### 1.3.2.1 Lighting

Illumination errors are recognized in the histogram because there are no pixels in the final or initial region of the intensity scale, while the middle regions of the histogram present a concentration of pixels with different intensity values. [Figure 1.10](#C_004_c1.xhtml#f1_10) shows an example of images with different types of illumination. It is possible to observe that the pixels in image (a) cover the entire dynamic (0–255) width of the histogram (b). On the other hand, images (c) and (e) have histograms with intensity values concentrated in whiter colors (values close to 255) and in the darker colors (values close to 0), histograms (d) and (f), respectively.

![FIGURE 1.10 The figures show how lighting errors are easily detected by the histogram. (a) Image with correct illumination, (c) with high illumination, and (e) with poor illumination. (b), (d), and (f) are the histograms of (a), (c), and (e), respectively.](images/Fig01_10.jpg)

[**FIGURE 1.10**](#C_004_c1.xhtml#f1_10b) The figures show how lighting errors are easily detected by the histogram. (a) Image with correct illumination, (c) with high illumination, and (e) with poor illumination. (b), (d), and (f) are the histograms of (a), (c), and (e), respectively.

#### 1.3.2.2 Contrast

The definition of contrast is understood as the range of intensity values that are used in a given image, or, in short, the difference between the maximum and minimum intensity values of the pixels present in the image. A full contrast image uses the full range of intensity levels defined for the image from 0 to *K* − 1 (black to white). It is, therefore, easy to observe the contrast of an image using a histogram. [Figure 1.11](#C_004_c1.xhtml#f1_11) shows different contrast settings in images from the histograms produced.

![FIGURE 1.11 The figures show different contrasts in images and their respective effects on the histogram. (a) Normal contrast and its histogram (c); and (b) low contrast and its histogram (d).](images/Fig01_11.jpg)

[**FIGURE 1.11**](#C_004_c1.xhtml#f1_11b) The figures show different contrasts in images and their respective effects on the histogram. (a) Normal contrast and its histogram (c); and (b) low contrast and its histogram (d).

#### 1.3.2.3 Dynamics

Under the term dynamics, we understand the number of different pixels that are used in the image. The ideal case in an image is presented when the full range of available intensity values *K* is used for the image in question. In this case, the whole region of intensity values is covered completely. An image that covers a region of intensity values smaller than the full one (*a*[min]\=0,*a*[max]\=*K*−1) so that:

*a*[min] > 0 or *a*[max] < *K* − 1 (1.9)

It produces an image with poor dynamic. It is considered poor since an appropriated dynamic reaches its maximum when all intensity values in that range are present in the image ([Figure 1.12](#C_004_c1.xhtml#f1_12)).

![FIGURE 1.12 Different dynamics in an image and their effects on the histogram. (a) High dynamics, (b) low dynamics with 20 intensity levels, (c) very low dynamics with only 8 intensity levels, (d) histogram of (a), (e) histogram of (b), and (f) histogram of (c).](images/Fig01_12.jpg)

[**FIGURE 1.12**](#C_004_c1.xhtml#f1_12b) Different dynamics in an image and their effects on the histogram. (a) High dynamics, (b) low dynamics with 20 intensity levels, (c) very low dynamics with only 8 intensity levels, (d) histogram of (a), (e) histogram of (b), and (f) histogram of (c).

While the contrast of an image can be high as long as the maximum value of the pixel intensity range is not exceeded, the dynamics of an image cannot be high (except by interpolation of the pixel intensity values). High dynamics represent an advantage for an image because the risk of losing image quality through the following processing steps is reduced. For this reason, digital cameras and professional scanners have a resolution higher than 8 bits, usually 12–14 bits, even if the image display elements have a normal resolution of 256.

### 1.3.3 Calculating the Histogram of an Image with MATLAB

This section explains MATLAB functions that can be used to calculate and display the histogram of an image contained in the Image Processing Toolbox \[[5](#C_004_c1.xhtml#r1_5)\].

#### 1.3.3.1 MATLAB Command Line Function

The function of the image processing toolbox for calculating the histogram of an image has the following format:

```
[counts,x]=imhist(I, n)
```

This function calculates and displays the histogram of the `I` image. The number of histogram values if `n` is not specified depends on the type of image involved. If `I` corresponds to a grayscale image, the function will use 256 values for the calculation and display. If `I` represents a binary image, the function will calculate the histogram with only two values.

If `n` is specified, the histogram is calculated and displayed using n intensity values instead of those specified by the image type. The variable `counts` symbolizes a vector that contains the number of pixels.

### 1.3.4 Color Image Histograms

Histograms of color images refer to brightness histograms. They are obtained over the planes from the color image, considering each plane as if it were an independent grayscale image.

#### 1.3.4.1 Brightness Histograms

The brightness histogram of an image is nothing more than the histogram of the corresponding grayscale version of the color image. Since the grayscale images are extracted from the color image, they represent the histograms of the different planes that compose it. [Figure 1.13](#C_004_c1.xhtml#f1_13) shows the luminosity histogram of a color image.

![FIGURE 1.13 Brightness histogram of a single plane from a color image. (a) Color image, (b) its grayscale version (luminance image), and (c) the corresponding histogram of (b).](images/Fig01_13.jpg)

[**FIGURE 1.13**](#C_004_c1.xhtml#f1_13b) Brightness histogram of a single plane from a color image. (a) Color image, (b) its grayscale version (luminance image), and (c) the corresponding histogram of (b).

#### 1.3.4.2 Color Component Histograms

Although the luminance histogram considers all color components, it is possible that errors may not be detected in the image. The luminance histogram may appear adequate, even though some color planes are inconsistent.

The histograms of each channel also give additional information on the color distribution in the image. For example, the blue channel (B) usually has a small contribution to the total luminance of the color image. To calculate the color component histograms, each color channel is considered an independent grayscale image from which each histogram is generated. [Figure 1.14](#C_004_c1.xhtml#f1_14) shows the luminance histogram *h*[LUM] and the histograms of each of the different color planes *h*[R], *h*[G] y *h*[B] for a typical RGB image.

![FIGURE 1.14 Histograms of the components from a color image. (a) Original RGB image, (b) histogram of Luminosity (hLUM), (c) histogram of the red channel (hR), (d) histogram of the green channel (hG), and (e) histogram of the blue channel (hB),](images/Fig01_14.jpg)

[**FIGURE 1.14**](#C_004_c1.xhtml#f1_14b) Histograms of the components from a color image. (a) Original RGB image, (b) histogram of Luminosity (*h*[LUM]), (c) histogram of the red channel (*h[R]*), (d) histogram of the green channel (*h[G]*), and (e) histogram of the blue channel (*h[B]*),

### 1.3.5 Effects of Pixel Operations on Histograms

An increase in the illumination (to add a positive constant to all pixel values) of an image causes its histogram to be shifted to the right side so that the values will tend to approach the upper limit of the allowed dynamic range (to intensity values of 255). On the other hand, an increase in the contrast of some images causes the respective histogram to extend its values within the interval of intensities (0–255). The complement operation on an image or inversion provokes the histogram to reflect itself, but in the opposite direction from its original position. Although the above cases seem straightforward (even trivial), it might be useful to discuss in detail the relationships between pixel operations and the histograms resulting from such operations.

[Figure 1.15](#C_004_c1.xhtml#f1_15) illustrates the way in which each region of the image with a homogeneous intensity *i* belongs to element *i* in the histogram. This element *i* corresponds to all pixels having an intensity value of *i*.

![FIGURE 1.15 Histogram values corresponding to a different set of pixels in the image. If a histogram element is shifted as a consequence of an operation, then all pixels of the corresponding set will also be modified in the same way. When two histogram elements h(p1) y h(p2) are joined together, their corresponding sets of pixels are also added together and are now non-separable.](images/Fig01_15.jpg)

[**FIGURE 1.15**](#C_004_c1.xhtml#f1_15b) Histogram values corresponding to a different set of pixels in the image. If a histogram element is shifted as a consequence of an operation, then all pixels of the corresponding set will also be modified in the same way. When two histogram elements *h*(*p*[1]) y *h*(*p*[2]) are joined together, their corresponding sets of pixels are also added together and are now non-separable.

As a result of an operation such as those mentioned above, the histogram value can shift, with the effect that all pixels belonging to this intensity value change. However, what happens when two different intensity values coincide as a result of an operation? In that case, both sets of pixels are merged, and the full amount of both is added together to generate a single intensity value for the histogram. Once different intensity levels have been merged into one, it is not possible to differentiate the subsets of pixels. Consequently, it is not possible to divide them. From the above, it is possible to conclude that this process or operation is associated with a loss in the dynamics and information of the image.

### 1.3.6 Automatic Contrast Adjustment

The objective of the automatic adaptation of the contrast is that the pixel values of an image are automatically modified in order to completely cover the allowed range of intensity values. To achieve this, a procedure is performed in which it is considered that the darkest pixel in the image is forced to take the smallest allowable value in the range of intensity values and the brightest pixel to the highest allowable value, while the rest of the pixels between these two values are linearly interpolated within this range \[[6](#C_004_c1.xhtml#r1_6)\].

Considering that *p*[low] y *p*[high] are the current intensity values corresponding to the smallest and highest pixels of an image *I*, which has a set of intensity values defined by the Interval \[*p*[min],*p*[max]\]. To cover the full scale of intensity values of the image, the pixel with the lowest intensity contained in the image is considered as the smallest of the allowable range (zero for an 8-bit grayscale image), and then the contrast (see [Figure 1.16](#C_004_c1.xhtml#f1_16)) is modified by the factor:

![FIGURE 1.16 The auto-contrast operation, in which from Equation 1.10, the pixel value p is linearly interpolated from the interval \[plow, phigh\] to the interval \[pmin, pmax\].](images/Fig01_16.jpg)

[**FIGURE 1.16**](#C_004_c1.xhtml#f1_16b) The auto-contrast operation, in which from Equation 1.10, the pixel value *p* is linearly interpolated from the interval \[*p*[low], *p*[high]\] to the interval \[*p*[min], *p*[max]\].

$\\frac{p\_{\\text{max}} - p\_{\\text{min}}}{p\_{\\text{high}} - p\_{\\text{low}}}$ (1.10)

Therefore, the simplest function of contrast adaptation *f*[ac] is defined as follows:

$f\_{ac} = \\left( {p - p\_{low}} \\right)\\left( \\frac{p\_{max} - p\_{min}}{p\_{high} - p\_{low}} \\right) + p\_{min}$ (1.11)

For an 8-bit grayscale image, the function can be simplified to:

$f\_{\\text{ac}} = \\left( {p - p\_{\\text{low}}} \\right) \\cdot \\left( \\frac{255}{p\_{\\text{high}} - p\_{\\text{low}}} \\right) + p\_{\\text{min}}$ (1.12)

The value of the interval \[*p*[min],*p*[max]\] does not always mean that it is the maximum permissible range of image representation, but it can also represent any range of interest for an image representation. Under such conditions, this method originally planned to increase the contrast can also be used to represent the image within a particular permissible range *p*[low] and *p*[high]. [Figure 1.17](#C_004_c1.xhtml#f1_17) shows the effect of the auto-contrast operation *p′*.

![FIGURE 1.17 The effect of the auto contrast operation. (a) Original image with low contrast, (b) enhanced image, (c) histogram of the original image, and (d) histogram of the enhanced image.](images/Fig01_17.jpg)

[**FIGURE 1.17**](#C_004_c1.xhtml#f1_17b) The effect of the auto contrast operation. (a) Original image with low contrast, (b) enhanced image, (c) histogram of the original image, and (d) histogram of the enhanced image.

As can be seen from [Figure 1.17](#C_004_c1.xhtml#f1_17), the self-adjustment of contrast performed by using Equation. 1.11 can produce that the extreme pixel values contained in the image change radically or very little the complete distribution of the resulting histogram. This is because the values of *p*[low] and *p*[high] from the original histogram involve a very small number of pixels that do not significantly represent the complete distribution. To avoid this problem, some fixed percentages (*s*[low],*s*[high]) are defined from which the distribution is considered significant for both the starting point (dark pixels) and the end element (light pixels) of the distribution. With these percentages, we calculate the new boundaries of the distribution. For this purpose, the lower boundary *a*[low] is considered the intensity value at which the number of pixels of lower intensities added together is greater than or equal to *s*[low]. Likewise, *a*[high] is the upper boundary intensity value at which the number of pixels of higher intensities added together is less than or equal to *s*[high]. See [Figure 1.18](#C_004_c1.xhtml#f1_18) for an illustration of the process. The values *a*[low] y *a*[high] depend on the image content and can be easily calculated from the cumulative histogram. *H*(*i*) of image *I*, such that:

![FIGURE 1.18 Auto-contrast operation considers percentage values to generate new boundaries. They now represent the significant values of the distribution. All values between 0 y alow as well as ahigh and 255 are ignored in the adjustment so that the resulting image reflects an improvement in contrast.](images/Fig01_18.jpg)

[**FIGURE 1.18**](#C_004_c1.xhtml#f1_18b) Auto-contrast operation considers percentage values to generate new boundaries. They now represent the significant values of the distribution. All values between 0 y *a*[low] as well as *a*[high] and 255 are ignored in the adjustment so that the resulting image reflects an improvement in contrast.

*a*[low] = min {*i*|*H*(*i*)≥*M*⋅*N*⋅*s*[low]} (1.13)

*a*[high] = max {*i*|*H*(*i*)≤*M*⋅*N*⋅(1−*s*[high])} (1.14)

where *M* ⋅ *N* is the number of pixels in the image *I*. All values outside the interval *a*[low] y *a*[high] are not considered for contrast enhancement, while values within this range are linearly scaled to occupy the permissible range \[*p*[min],*p*[max]\]. The pixel operation used to perform the auto-contrast operation can be formulated as follows:

$f\_{\\text{mac}} = \\left\\{ \\begin{matrix} p & \\text{si}\_{\\text{low}} & {}\_{\\text{min}} \\\\ \\left( {p - a\_{\\text{low}}} \\right) & {\\text{si}a\_{\\text{low}} < p} & {< a\_{\\text{high}}} \\\\ p & \\text{si}\_{\\text{high}} & {}\_{\\text{max}} \\\\ \\end{matrix} \\right.$ (1.15)

In practice, *s*[low] y *s*[high] are assigned the same value. They typically assume values within the interval \[0.5, 1.5\]. An example of this operation is provided by the popular image-processing program Photoshop, where the value of s is set to *s*[low] = 0.5 in order to perform auto-adjustment of the contrast in images.

### 1.3.7 Cumulative Histogram

The cumulative histogram is a variant of the normal histogram. It provides important information for performing pixel-by-pixel operations on images (point operations), for example, to balance a histogram. The cumulative histogram *H*(*i*) is defined as:

$H\\left( i \\right) = {\\sum\\limits\_{j = 0}^{i}{h\\left( j \\right)}}\\quad\\text{para}0 \\leq i < K$ (1.16)

The value of *H*(*i*) is then the sum of all the elements below the specified value *i* of the “classical” histogram *h*(*j*) with the values *j* = 0…*i*. or the value obtained considering the immediately preceding value

$H\\left( i \\right) = \\left\\{ \\begin{matrix} {h\\left( 0 \\right)} & {\\operatorname{}\\text{para}\\operatorname{}i = 0} \\\\ {H\\left( {i - 1} \\right) + h\\left( i \\right)} & {\\text{para}\\operatorname{}0 \\leq i < K} \\\\ \\end{matrix} \\right.$ (1.17)

The cumulative histogram is, according to its definition, a monotonically increasing function with a maximum value of

$H\\left( {K - 1} \\right) = \\underset{j = 0}{\\overset{K - 1}{\\Sigma}}h\\left( j \\right) = MN$ (1.18)

[Figure 1.19](#C_004_c1.xhtml#f1_19) shows an example of the cumulative histogram.

![FIGURE 1.19 (a) Original image, (b) histogram of (a), and (c) the cumulative histogram of (a).](images/Fig01_19.jpg)

[**FIGURE 1.19**](#C_004_c1.xhtml#f1_19b) (a) Original image, (b) histogram of (a), and (c) the cumulative histogram of (a).

### 1.3.8 Histogram Linear Equalization

A frequent problem is the adaptation of different images to the same distribution *h*[eq] of intensity levels, either to improve their print quality or to be able to compare them properly. Balancing a histogram means, by using a pixel operation, changing the image in such a way that it shows a histogram, as far as possible, distributed over all intensity levels (see [Figure 1.20](#C_004_c1.xhtml#f1_20)). Since we are dealing with discrete distributions, this is only possible at the approximation level because, as already discussed above, the homogeneous operations can only shift or merge groups of pixels belonging to a certain intensity level. However, once they are together, it is not possible to separate them. Therefore, it is not possible to remove the histogram peaks from the distribution. Under such conditions, it is not possible to produce, from the original histogram, an ideal histogram *h*[eq], where all gray levels are equally distributed. Instead of this, it is possible only to transform the image so that the histogram shows an approximation to the balanced distribution of gray levels. Such an approximation can be achieved by the cumulative histogram *H*(*i*). An important feature of this transformation is that a version of the cumulative histogram *H*[eq] represents a balanced (target) distribution. Obviously, as presented in the previous statement, this is only an approximation. However, it is possible in this way to use a pixel operation that shifts the histogram elements in such a way that the cumulative histogram of the image shows at least approximately an increasing linear function, as exemplified in [Figure 1.20](#C_004_c1.xhtml#f1_20).

![FIGURE 1.20 Representation of the equalization process of a histogram. Using a pixel operation on an image with the original histogram h(i), the idea is to obtain the histogram heq(i), the cumulative histogram H(i) and the balanced version represented by Heq(i) as the effect of the operation.](images/Fig01_20.jpg)

[**FIGURE 1.20**](#C_004_c1.xhtml#f1_20b) Representation of the equalization process of a histogram. Using a pixel operation on an image with the original histogram *h*(*i*), the idea is to obtain the histogram *h*[eq](*i*), the cumulative histogram *H*(*i*) and the balanced version represented by *H*[eq](*i*) as the effect of the operation.

The pixel operation *f*[eq](*p*) required to balance the histogram of an image is calculated from its cumulative histogram. For an image with a resolution *M* × *N* pixels in the range of \[0...*K*−1\] the operation can be defined as follows:

$f\_{\\text{eq}}\\left( p \\right) = \\left\\lbrack {H\\left( p \\right) \\cdot \\frac{K - 1}{MN}} \\right\\rbrack$ (1.19)

The function defined in Equation 1.13 presents a monotonical behavior because this function corresponds to the cumulative histogram experiments, a behavior in which it is constantly incremented. *H*(*p*) and the other parameters *K*, *M*,  and *N* are only constants. An image whose histogram is already well distributed over all its intensity levels would not represent any change when applying the pixel operation that balances the histogram. [Figure 1.21](#C_004_c1.xhtml#f1_21) shows the result on an image after having equalized its histogram linearly. It can be noted that for inactive pixels (those intensity values that do not exist in the original image), when they are considered in the cumulative histogram, the graph presents the same value as its previous neighbor value. For example, consider that there are no pixels in the original image of intensity level 10. Their value in the histogram will be *h*(10) = 0, but their value in the cumulative histogram will be *H*(10) = *H*(9). This, although it would seem to be a negative consequence of the pixel operation used to balance the histogram (Equation 1.11). As a consequence, intensity values that do not exist in the original image will not finally appear in the balanced image.

![FIGURE 1.21 Through the use of the correct pixel operation feq the intensity value p is shifted to p′ in such a way that it best approximates the cumulative target histogram Heq(i).](images/Fig01_21.jpg)

[**FIGURE 1.21**](#C_004_c1.xhtml#f1_21b) Through the use of the correct pixel operation *f*[eq] the intensity value *p* is shifted to *p*′ in such a way that it best approximates the cumulative target histogram *H*[eq](*i*).

$fdD\\left( i \\right) = \\frac{H\\left( i \\right)}{H\\left( {K - 1} \\right)} = \\frac{H\\left( i \\right)}{\\text{Sum}\\left( h \\right)} = \\underset{j = 0}{\\overset{i}{\\Sigma}}\\frac{h\\left( j \\right)}{\\text{Sum}\\left( h \\right)} = \\underset{j = 0}{\\overset{i}{\\Sigma}}\\text{hN}\\left( i \\right)$

0 ≤ *i* < *K* (1.20)

The function *f**d**D*(*i*) is, like the cumulative histogram, monotonically increasing, so it follows that:

*f**d**D*(0) = hN(0) (1.21)

$fdD\\left( {K - 1} \\right) = {\\underset{i = 0}{\\overset{K - 1}{\\Sigma}}{\\text{hN}\\left( i \\right) = 1}}$ (1.22)

Through this statistical formulation, it is possible to model the image as a random process. The process is usually considered to be homogeneous (i.e., independent of the position in the image). Thus, each pixel in the image *I*(*x*,*y*) is the result of a random experiment with a random variable *i*.

## 1.4 Gamma Correction

So far, in this book, the word “intensity” has been used several times, with the understanding that the pixel values of an image are somehow related to these concepts. However, how does the value of a pixel actually relate to the amount of light on a monitor or to the number of toner particles that the laser printer needs to form a certain intensity value on the paper? In general, the relationship between the intensity value of a pixel and its respective physical measurements is complex and, in all cases, non-linear. Therefore, it is important to know at least approximately the nature of these relationships and thus to be able to predict the appearance of images on different media.

Gamma correction is a pixel operation that compensates for the different image acquisition conditions and allows the display of different characteristics by using a general space of intensities \[[7](#C_004_c1.xhtml#r1_7)\]. The expression gamma originally comes from classical photography, where there is an approximately logarithmic relationship between the amount of illumination and the resulting density of the photographic film. The so-called illumination function represents this relationship and is distributed over a relatively large region in the form of an ascending line (see [Figure 1.22](#C_004_c1.xhtml#f1_22)). The slope of the illumination function within its dispersion region is traditionally defined as the gamma of the photographic film. Later in the television industry, the problem of image distortion due to the nonlinearity of the cathode ray tube was confronted, and the concept of gamma was adopted to describe it. Therefore, the television signal is corrected by the television station before sending it to the receiver, which is called gamma correction, so this correction compensates for the distortion made by the TV.

![FIGURE 1.22 Illumination function for photography. The function relates the logarithmic magnitude of the illumination to the resulting photographic film density over a relatively large region. The slope of the function is defined as gamma (γ) of the photographic film \\gamma = \\frac{\\Delta D}{\\Delta B}.](images/Fig01_22.jpg)

[**FIGURE 1.22**](#C_004_c1.xhtml#f1_22b) Illumination function for photography. The function relates the logarithmic magnitude of the illumination to the resulting photographic film density over a relatively large region. The slope of the function is defined as gamma (*γ*) of the photographic film $\\gamma = \\frac{\\Delta D}{\\Delta B}$.

### 1.4.1 The Gamma Function

The basis for the gamma correction is the gamma function, which can be defined as follows:

$\\begin{array}{ccl} b & = & {f\_{\\gamma}\\left( a \\right) = a^{\\gamma}} \\\\ b & = & {f\_{\\gamma}\\left( a \\right) = a^{\\gamma}} \\\\ a & \\in & {{\\mathbb{R}},\\operatorname{}\\gamma > 0} \\\\ \\end{array}$(1.23)

where the parameter γ is the so-called gamma factor. The gamma function is used only within the interval \[0,1\], and the function produces a value from (0,0) to (1,1). As shown in [Figure 1.23](#C_004_c1.xhtml#f1_23), when *γ* = 1, we have *f*[*γ*](*a*) = *a* (identity), generating a line from (0,0) to (1,1). For values of *γ* < 1, the function is displayed above the line. For the case *γ* = 1, if *γ* > 1, the function is below the line, where the curvature of the function increases in both directions (above and below the line) as long as *γ* is different from 1.

![FIGURE 1.23 Gamma function b = aγ for different values of γ.](images/Fig01_23.jpg)

[**FIGURE 1.23**](#C_004_c1.xhtml#f1_23b) Gamma function *b* = *a*^γ for different values of *γ*.

The gamma function is controlled only by the parameter *γ* and behaves with monotonical increments in the interval \[0,1\], so it is invertible, such that:

$a = f\_{\\gamma}^{- 1}\\left( b \\right) = b^{1/\\gamma} = f\_{\\overline{\\gamma}}\\left( b \\right)$ (1.24)

The same is applicable to the case of the gamma value with $\\overline{\\gamma} = \\frac{1}{\\gamma}$.

The specific values of *γ* for different devices are usually specified by the manufacturer and obtained from measurements. For example, the nominal values for *γ* of a standard cathode ray tube are between 1.8 and 2.8, with a typical value of 2.4 for a standard LCD monitor.

### 1.4.2 Use of Gamma Correction

To illustrate the use of gamma correction, it is assumed that a camera distorts the image with a value *γ*[*c*]. It produces an output signal *s* because of the occurrence of the illumination value under the following relationship:

*s* = *B*^(*γ*[*c*]) (1.25)

To compensate for this distortion, we apply an inverse gamma correction to the camera output signal. ${\\overline{\\gamma}}\_{c}$ will allow us to recover the original signal. This operation can be formulated as follows:

$b = f\_{{\\overline{\\gamma}}\_{c}}\\left( s \\right) = s^{1/\\gamma\_{c}}$ (1.26)

From this formulation, it can be observed that:

$b = s^{1/\\gamma\_{c}} = \\left( B^{\\gamma\_{c}} \\right)^{1/\\gamma\_{c}} = B^{\\frac{\\gamma\_{c}}{\\gamma\_{c}}} = B^{1} = B$ (1.27)

The corrected signal *b* is identical to the light intensity. Under this operation, the distortion produced by the camera is eliminated. [Figure 1.24](#C_004_c1.xhtml#f1_24) shows an illustration of this process. The rule of thumb is to find the distortion *γ*[*D*] for the device in question and compensate for it through gamma correction ${\\overline{\\gamma}}\_{D}$.

![FIGURE 1.24 Principle of gamma correction. To correct the distortion \\gamma\_{c} presented by a camera, it is necessary to apply the gamma correction \\overline{\\gamma\_{c}} in such a way that the combination of both generates the elimination of the distortion.](images/Fig01_24.jpg)

[**FIGURE 1.24**](#C_004_c1.xhtml#f1_24b) Principle of gamma correction. To correct the distortion *γ*[*c*] presented by a camera, it is necessary to apply the gamma correction $\\overline{\\gamma\_{c}}$ in such a way that the combination of both generates the elimination of the distortion.

Everything discussed above assumes that all values are in the interval \[0,1\]. Obviously, this is not always the case, particularly when dealing with digital images in the range \[0,255\]. Considering this, for applying the gamma correction, the only thing to do is to scale the image interval to values between 0 and 1 and then apply the gamma correction as discussed in this section.

## 1.5 MATLAB Pixel Operations

Once we have covered the theoretical foundations in previous sections, we will present how to use MATLAB tools to perform pixel operations on images. These tools involve using MATLAB as a programming language (.m file extension) and functions belonging to the image processing and computer vision toolboxes.

### 1.5.1 Changing Contrast and Illumination in MATLAB

To increase the contrast using MATLAB, it is necessary to multiply the image by a positive constant so that the histogram of the resulting image becomes wider. The following command assumes that *A* is an image, and the contrast is raised by 50% so that the image is multiplied by 1.5, leaving its result in *B*.

```
>>B=A*1.5;
```

To increase the illumination of an image in MATLAB, add to the image the number of levels to which you want to increase the illumination. With this operation, we will make the histogram move in any direction according to the added number of levels. The following command assumes that we want to increase the illumination of image *A* by 10 levels, so we add 10 to this matrix, producing the result in *B*.

```
>>B=A+10;
```

### 1.5.2 Segmenting an Image by Thresholding Using MATLAB

Although segmentation and binary image processing will be covered in depth in another chapter, this section briefly introduces thresholding, but only as a pixel operation, and how to perform it using MATLAB commands.

Using the functions of the MATLAB image processing toolbox, it is possible to segment an image depending on the intensity level of the objects presented in the scene.

To perform the segmentation process by thresholding, it is only necessary to define the intensity level (threshold) from which the elements of the image can be classified into two classes. Those above this value will be considered as a particular class, while those below this value will be considered another class.

#### 1.5.2.1 Command Line Segmentation

The simplest binarization process that can be conducted by MATLAB is logical operations. The way to do this is by using the overloaded property of the logical operations. These operations, in the case of matrices (images), imply the evaluation of the logical condition for each element. The result of this operation produces ones and zeros for those elements that have fulfilled the logical condition. On the other hand, the elements with a value of zero represent those pixels whose evaluation of the condition is false. For example, we would have in the command line:

```
>>B=A>128;
```

The resulting matrix *B* will be composed of ones and zeros. Ones at those positions of *A* where the pixel values are greater than the threshold 128, while zeros at those points of A where the pixels did not meet the condition.

### 1.5.3 Contrast Adjustment with MATLAB

MATLAB contains the function `imadjust`, which allows us to adapt the contrast of images to increase, decrease or adjust it. The function prototype presents the following structure:

```
J=imadjust (I)
J=imadjust(I,[low_in; high_in],[low_out; high_out])
```

`J` =` imadjust(I)` maps the intensity values of the image `I` to new intensity values in image `J` such that from 1% of the data (*s*[low]\=*s*[high]\=1%) are considered to define the lower and upper limits of intensities of the image `I`. From these limits, it will be adjusted the contrast of the resulting image `J`. As already discussed above, the fact of not considering the limits of image `I`, but only a percentage, allows us to improve the contrast considering the complete amount of the data. Under such conditions, it is possible to improve the contrast of the image even in those cases where the contrast covers the entire image range but not significantly.

`J` =` imadjust(I,[``low_in``;` `high_in],[low_out; high_out``])` maps the values of the image `I` to new values of `J`, such that the values of image `low_in` and `high_in` are mapped to the new values `low_out` and `high_out` of image `J`. The values below `low_in` and `high_in` of the image `I` are not considered. It is possible to delimit the boundaries with the empty matrix [], which means defining the boundaries with the permissible values for each type of image [0,1].

There are some additional variants of this function that, apart from considering the contrast enhancement, allow us to further scale the contrast by means of a parameter (SP). Through this parameter, it is possible to represent the way in which the images `I` and `J` are related when scaled. The structure of the function is as follows:

```
J = imadjust(I,[low_in; high_in],[low_out; high_out], SP)
```

This function transforms the values of `I` to obtain the values of `J`, as explained above. However, if `SP` is less than 1, the mapping is scaled up (brighter) for the `J` image values, while if SP is greater than 1, the scaling is done down (darker). For the case where `SP` is one, the adjustment is simply linear. [Figure 1.25](#C_004_c1.xhtml#f1_25) shows the effect of applying the `imadjust` function to an image.

![FIGURE 1.25 Result of applying the imadjust function. (a) Original image, (b) image resulting from applying the imadjust function, (c) histogram of the original image, and (d) histogram of the contrast-corrected image.](images/Fig01_25.jpg)

[**FIGURE 1.25**](#C_004_c1.xhtml#f1_25b) Result of applying the imadjust function. (a) Original image, (b) image resulting from applying the imadjust function, (c) histogram of the original image, and (d) histogram of the contrast-corrected image`.`

### 1.5.4 Histogram Equalization Using MATLAB

The problem of adapting different images to the same distribution of intensity levels, either to improve their print quality or to compare them properly, can be implemented using MATLAB. Equalizing a histogram, as already discussed in previous sections, means modifying it by using a pixel operation of the image in such a way that it shows a histogram with a desired distribution. To solve the equalization problem, the cumulative histogram is used, and among its properties is that it represents an equalized distribution. Obviously, the above statement is only an approximation. However, it is possible to use a pixel operation that shifts the histogram elements so that the cumulative histogram of the image shows at least approximately an increasing linear function.

The required pixel operation *f*[eq](*p*) to equalize the histogram of an image is calculated from its cumulative histogram, which is defined by Equation 1.28. By implementing this process in a MATLAB program, one could equalize the histogram of an image in a linear way. [Program 1.1](#C_004_c1.xhtml#p1_1) shows the implementation of the linear equalization of the histogram of an image.

The results shown in [Figure 1.26](#C_004_c1.xhtml#f1_26) were obtained after applying the code described in [Program 1.1](#C_004_c1.xhtml#p1_1). From the figure, the result of the contrast improvement can be clearly observed and can be analyzed by reviewing the corresponding histograms.

![FIGURE 1.26 Result of applying the code described in Program 1.1. (a) Original intensity image, (b) contrast-enhanced image, (c) histogram of the original image, (d) histogram of the enhanced image, (e) cumulative histogram of the original image, and (f) cumulative histogram of the enhanced image.](images/Fig01_26.jpg)

[**FIGURE 1.26**](#C_004_c1.xhtml#f1_26b) Result of applying the code described in [Program 1.1](#C_004_c1.xhtml#p1_1). (a) Original intensity image, (b) contrast-enhanced image, (c) histogram of the original image, (d) histogram of the enhanced image, (e) cumulative histogram of the original image, and (f) cumulative histogram of the enhanced image.

The MATLAB image processing toolbox implements the `histeq` function, which allows equalizing the histogram of images to increase their contrast. `histeq` increases the contrast of an image by transforming the intensity levels of the image so that the histogram of the output image is close to a specific histogram considered as a reference. The function has the following structure:

```
J = histeq(I, hgram)
J = histeq(I, n)
```

`J` =` histeq(I, hgram)` transforms the intensity values of the image `I` so that the cumulative histogram of image `J` is close to the one considered as reference `hgram`. The vector `hgram` must have a length that depends on the type of image and its characteristics. For example, for images of type uint8, we have a length of 256. To perform the transformation of the intensity levels of `I`, we select a function *f*[*T*] (pixel operation), which produces a cumulative histogram that minimizes the association defined by:

$\\underset{i}{\\Sigma}\\left| {H\_{f\_{T}}\\left( {f\_{T}\\left( i \\right)} \\right) - H\_{\\text{hgram}}\\left( i \\right)} \\right|$ (1.28)

where *H*[*f*[*T*]] is the cumulative histogram of the image transformed by the function *f*[*T*] and *H*[hgram] the cumulative histogram is considered a reference to which we want to approximate *H*[*f*[*T*]] by choosing *f*[*T*].

If the vector `hgram` is not used in the function histeq, it is considered that the transformation performed on the image `I` is done so that its histogram approaches a response that is as flat as possible.

`J` =` histeq(I, n)` transforms the intensity values of the image `I`, returning an image with only n different intensity values. The transformation is performed by mapping the intensity levels of image `I` to n different values of image `J` so that the histogram of `J` is approximately flat.

[Figure 1.27](#C_004_c1.xhtml#f1_27) shows the result of applying the function `histeq` to an image. In this example, the vector `hgram` has not been given as an argument. Therefore, the transformation of the intensity values of the source image is performed so that the histogram of the resulting image is approximately flat, which results in a cumulative histogram similar to a straight line.

![FIGURE 1.27 Result of applying the function histeq. (a) Source image, (b) result image, (c) histogram of the source image, (d) flattened histogram resulting from the operation performed by histeq, (e) cumulative histogram of the source image, and (f) cumulative histogram of the resulting image.](images/Fig01_27.jpg)

[**FIGURE 1.27**](#C_004_c1.xhtml#f1_27b) Result of applying the function `histeq.` (a) Source image, (b) result image, (c) histogram of the source image, (d) flattened histogram resulting from the operation performed by histeq, (e) cumulative histogram of the source image, and (f) cumulative histogram of the resulting image.

## 1.6 Multi-Source Pixel Operations

Sometimes it will be necessary to perform pixel operations where the intensity value of the resulting pixel depends not only on the pixel in question in an image but also on other pixels in different images. [Figure 1.28](#C_004_c1.xhtml#f1_28) shows a representation of such operations.

![FIGURE 1.28 Representation of pixel operations, in which the resulting pixel depends on the value of pixels from different images, keeping the same position.](images/Fig01_28.jpg)

[**FIGURE 1.28**](#C_004_c1.xhtml#f1_28b) Representation of pixel operations, in which the resulting pixel depends on the value of pixels from different images, keeping the same position.

As can be seen from [Figure 1.28](#C_004_c1.xhtml#f1_28), the resulting pixel is obtained from the application of a function that operates on the two pixels from two different images. It is also considered that all the pixels participating in the function are from two different images with the same position. The value from this operation represents the result, which is in the same position as its sources.

### 1.6.1 Logical and Arithmetic Operations

Logical and arithmetic operations performed between images, such as addition, subtraction, AND, and OR, can be performed pixel by pixel. An important point to consider is the fact that these operations may result in values that are outside the permissible range for the image, so sometimes a change of scale is required.

#### 1.6.1.1 Sum

The sum of the two images *I*[*A*] and *I*[*B*] is defined as:

*I*^′(*x*,*y*) = *I*[*A*](*x*,*y*) + *I*[*B*](*x*,*y*) (1.29)

A common application of this operation is to superimpose one image on another to achieve a blending effect (see [Figure 1.29](#C_004_c1.xhtml#f1_29)), as well as to add an image with artifacts or dots in different positions to simulate noise patterns.

![FIGURE 1.29 Superposition of images by applying the sum operator between two images. (a) Image 1, (b) image 2, (c) superposition of images 1 and 2.](images/Fig01_29.jpg)

[**FIGURE 1.29**](#C_004_c1.xhtml#f1_29b) Superposition of images by applying the sum operator between two images. (a) Image 1, (b) image 2, (c) superposition of images 1 and 2.

#### 1.6.1.2 Subtract

The difference between the two images *I*[*A*] and *I*[*B*] is defined as:

*I*^′(*x*,*y*) = *I*[*A*](*x*,*y*) − *I*[*B*](*x*,*y*) (1.30)

This operation is commonly used for image segmentation and enhancement. Another important use of image subtraction is in the case of movement detection \[[8](#C_004_c1.xhtml#r1_8)\]. If two images taken at different times are considered, *T*[1] y *T*[2], and we obtain their difference. What we will find with it is the change in position of the pixels that were part of the object that changed its position. [Figure 1.30](#C_004_c1.xhtml#f1_30) shows an example of position change detection by subtracting two images taken at different time instants.

![FIGURE 1.30 Movement detection by subtracting images taken at different time instants. (a) Image 1 taken at instant 1, (b) image 2 taken at instant 2, and (c) subtraction of image 1 and 2.](images/Fig01_30.jpg)

[**FIGURE 1.30**](#C_004_c1.xhtml#f1_30b) Movement detection by subtracting images taken at different time instants. (a) Image 1 taken at instant 1, (b) image 2 taken at instant 2, and (c) subtraction of image 1 and 2.

#### 1.6.1.3 AND and OR

These operations are performed between binary images using the truth table for both logic functions. Therefore, in the case of AND, both pixels must be one in order to generate a pixel one in the resulting image, while in the case of the OR function with one of the pixels of the image being one is sufficient reason to generate one in the output image. For any other combination in both cases, the pixel will be zero in the output image. These functions have their main activity in block processing, where only those pixels considered in a certain region will be considered in the processing, while the others will be set to zero or simply not taken into account.

### 1.6.2 Alpha Blending Operation

The alpha blending or compositing operation is used to combine two images, where each pixel of the resulting image is a linear combination of the pixels of the two images considered as sources. That is, if we have two images and we apply the alpha blending operation to combine them, each pixel of the resulting image will be a linear combination of both images, defined by the following equation:

*I*[*R*](*x*,*y*) = (1−*α*) ⋅ *I*[*A*](*x*,*y*) + *α* ⋅ *I*[*B*](*x*,*y*) (1.31)

By means of this operation, it is possible to blend two images. The background image is represented by the image *I*[*A*]. The image *I*[*B*] is considered transparent in the background *I*[*A*]. The association of these two images is controlled by the transparency factor *α*, which is defined in the interval \[0,1\]. [Figure 1.31](#C_004_c1.xhtml#f1_31) shows the effect of applying this operation to two images, considering different values of *α*.

![FIGURE 1.31 Effect of applying the Alpha Blending operation. (a) Image IB, (b) image IA, (c) result image IR with α = 0.3, and (d) result image IR with α = 0.7.](images/Fig01_31.jpg)

[**FIGURE 1.31**](#C_004_c1.xhtml#f1_31b) Effect of applying the Alpha Blending operation. (a) Image *I[B]*, (b) image *I[A]*, (c) result image *I[R]* with *α* = 0.3, and (d) result image *I[R]* with *α* = 0.7.

## References

1.  [Gonzalez](#C_004_c1.xhtml#r1_1b), R. C., & Woods, R. E. (2008). Digital image processing (3rd ed.). Prentice Hall.
2.  [Jain, A. K](#C_004_c1.xhtml#r1_2b). (1989). Fundamentals of digital image processing. Prentice Hall.
3.  [Woods](#C_004_c1.xhtml#r1_3b), R. E. (2015). Digital image processing (4th ed.). Pearson.
4.  [Gonzalez](#C_004_c1.xhtml#r1_4b), R. C., & Wintz, P. (1977). Digital image processing. Addison-Wesley.
5.  [Gonzalez](#C_004_c1.xhtml#r1_5b), R. C., Woods, R. E., & Eddins, S. L. (2004). Digital image processing using MATLAB. Prentice Hall.
6.  [Burger](#C_004_c1.xhtml#r1_6b), W., & Burge, M. J. (2016). Digital image processing: An algorithmic introduction using Java. Springer.
7.  [Szeliski](#C_004_c1.xhtml#r1_7b), R. (2010). Computer vision: algorithms and applications. Springer.
8.  [Milanfar](#C_004_c1.xhtml#r1_8b), P. (2013). A tour of modern image processing: From fundamentals to applications. CRC Press.

# 2 Spatial Filtering

DOI: [10.1201/9781003287414-2](https://doi.org/10.1201/9781003287414-2)

## 2.1 Introduction

The essential characteristic of pixel operations considered in [Chapter 1](#C_004_c1.xhtml) was that the new pixel value of the calculated element finally depends only and exclusively on the value of the original pixel. The result of this operation is located in the same position. Although it is possible to perform many effects on images using pixel operations, there are conditions under which it is not possible to use them to generate specific effects, as it is in the case of blurring (see [Figure 2.1](#C_005_c2.xhtml#f2_1)) or detection of image edges.

![FIGURE 2.1 If a pixel operation is used, effects such as blurring or edge detection cannot be performed. (a) Original image and (b) blurred image.](images/Fig02_01.jpg)

[**FIGURE 2.1**](#C_005_c2.xhtml#f2_1b) If a pixel operation is used, effects such as blurring or edge detection cannot be performed. (a) Original image and (b) blurred image.

## 2.2 What Is a Filter?

In an image, noise is observed where, locally, there is an abrupt change in the level of intensity, whether it increases or decreases significantly. Conversely, there are also regions in the image where the intensity of the image remains constant. The first idea of filtering an image is to eliminate noise pixels, replacing them with the average value of their neighbors \[[1](#C_005_c2.xhtml#r2_1)\].

Therefore, to calculate the new value of a pixel *I*^′(*x*,*y*), it is used its original value *I*(*x*,*y*) = *p*[0], considering also its eight neighboring pixels *p*[1], *p*[2], …, *p*[8] of the original image *I*. The association among the current pixel *p*[0] and its neighbors is modeled as the arithmetic average of these nine values:

$\\left. I^{\\prime}\\left( {x,y} \\right)\\leftarrow\\frac{p\_{0} + p\_{1} + p\_{2} + p\_{3} + p\_{4} + p\_{5} + p\_{6} + p\_{7} + p\_{8}}{9} \\right.$ (2.1)

In relative coordinates to the image, the above formulation could be expressed as:

$\\left. I^{\\prime}\\left( {x,y} \\right)\\leftarrow\\frac{1}{9} \\cdot \\begin{bmatrix} \\begin{matrix} {I\\left( {x - 1,y - 1} \\right)} & + \\\\ \\end{matrix} & \\begin{matrix} {I\\left( {x,y - 1} \\right)} & + \\\\ \\end{matrix} & {\\begin{matrix} {I\\left( {x + 1,y - 1} \\right)} & + \\\\ \\end{matrix}\\operatorname{}} \\\\ \\begin{matrix} {I\\left( {x - 1,y} \\right)} & + \\\\ \\end{matrix} & \\begin{matrix} {I\\left( {x,y} \\right)} & + \\\\ \\end{matrix} & \\begin{matrix} {I\\left( {x + 1,y} \\right)} & + \\\\ \\end{matrix} \\\\ \\begin{matrix} {I\\left( {x - 1,y + 1} \\right)} & + \\\\ \\end{matrix} & \\begin{matrix} {I\\left( {x,y + 1} \\right)} & + \\\\ \\end{matrix} & {I\\left( {x + 1,y + 1} \\right)} \\\\ \\end{bmatrix} \\right.$ (2.2)

It can also be described in compact form as follows:

$\\left. I^{\\prime}\\left( {x,y} \\right)\\leftarrow\\frac{1}{9} \\cdot {\\sum\\limits\_{j = - 1}^{1}{\\sum\\limits\_{i = - 1}^{1}{I\\left( {x + i,y + j} \\right)}}} \\right.$ (2.3)

This formulation shows all the typical elements that describe a filter. This filter is an example of one of the most used types of filters, the so-called linear filters.

Considering the information from [Chapter 1](#C_004_c1.xhtml), the difference between pixel operations and filters should be clear, especially since the result of filter operations does not only depend on a single pixel of the original image but on a set of them. The current coordinates of the pixel in the original image (*x*,*y*) normally define a region *R*(*x*,*y*) of neighbors considered. [Figure 2.2](#C_005_c2.xhtml#f2_2) shows the coordinates of the current pixel and its relationship with the considered neighbor region.

![FIGURE 2.2 Principle of filter operations. Each new pixel I^{\\prime}\\left( {x.y} \\right) is calculated from a certain region R\\left( {x,y} \\right) of neighbors whose central coordinates are related to the coordinates of the pixel to be calculated.](images/Fig02_02.jpg)

[**FIGURE 2.2**](#C_005_c2.xhtml#f2_2b) Principle of filter operations. Each new pixel *I*^′(*x*.*y*) is calculated from a certain region *R*(*x*,*y*) of neighbors whose central coordinates are related to the coordinates of the pixel to be calculated.

The size of the filter region *R*(*x*,*y*) is an important parameter since it determines how many and which neighbors of the original image pixel will be considered to calculate the new pixel. In the example discussed above, a smoothing filter with a region 3 × 3 was used, which is centered on the coordinate (*x*,*y*). With filters of higher sizes, 5 × 5,  7 × 7, or even 31 × 31 pixels, higher smoothing effects are obtained.

The shape of the filter region can be any. However, the square shape is the most used because, in addition to its ease of calculation (since it is not necessary to calculate the pixel grid by some function, as it would be necessary if it were a circular one), it allows to consider neighboring pixels in all directions. This is a desirable property of a filter. The relative importance of each neighboring pixel can also be different for a filter. That is, a different weight can be assigned to each pixel in the region depending on its relationship with the central pixel. Therefore, the closest elements to the central pixel are given greater importance, while those located further away are assigned less importance.

There are different alternatives to generating a filter. However, a systematic method is needed to generate a filter that fulfills the requirements of specific uses. There are two different categories of filters: linear and non-linear. The difference between both types of processing is the way in which the pixel within the processing region *R*(*x*,*y*) is connected with the operation, which can be linear or non-linear \[[2](#C_005_c2.xhtml#r2_2)\]. In the remainder of the chapter, both types of filters will be discussed, and some practical examples will also be shown. The main operation in filtering corresponds to the sum of the multiplications of each pixel by the coefficients in a neighborhood defined by the matrix. This matrix of coefficients is known in the computer vision community as a filter, mask, kernel, or window.

## 2.3 Spatial Linear Filters

In linear filters, the intensity values of the pixels within the processing region are combined linearly to generate the resulting pixel \[[3](#C_005_c2.xhtml#r2_3)\]. An example of this type is presented in Equation 2.3, where nine pixels that are part of a region 3 × 3 are linearly combined in a sum multiplied by the factor (1/9). With the same mechanism, a multiple numbers of filters can be defined with different behaviors on an image. To obtain different effects over the image, it is necessary to define the weights of the kernel. These weights are the values that assign the relative importance of each pixel in the linear combination.

### 2.3.1 The Filter Matrix

Linear filters are fully specified by defining the size and shape of the processing region, as well as the corresponding weights or coefficients that determine how linearly the pixel values of the original image are combined. The values of these coefficients or weights are defined in the filter matrix *H*(*i*,*j*) or simply mask. The size of the matrix *H*(*i*,*j*) determines the size of the filter processing region *R*(*x*,*y*), and its values define the weights in which the corresponding image intensity values are multiplied to obtain their linear combination \[[4](#C_005_c2.xhtml#r2_4)\]. Therefore, the filter to smooth an image considered in Equation 2.3 can be defined by the following filter mask:

$H\\left( {i,j} \\right) = \\begin{bmatrix} {1/9} & {1/9} & {1/9} \\\\ {1/9} & {1/9} & {1/9} \\\\ {1/9} & {1/9} & {1/9} \\\\ \\end{bmatrix} = \\frac{1}{9}\\begin{bmatrix} 1 & 1 & 1 \\\\ 1 & 1 & 1 \\\\ 1 & 1 & 1 \\\\ \\end{bmatrix}$ (2.4)

From Equation 2.4, it can be seen that each of the nine pixels that are defined in the mask contributes to one-ninth of the final value of the resulting pixel.

Fundamentally, the filter matrix *H*(*i*,*j*), like an image, is a two-dimensional discrete real function. Therefore, the mask has its own coordinate system, where the origin is its center. Under such conditions, we will have positive or negative coordinates (see [Figure 2.3](#C_005_c2.xhtml#f2_3)). It is important to note that the coefficients of the filter matrix outside its defined coordinates are zero.

![FIGURE 2.3 Mask grid and its corresponding coordinate system.](images/Fig02_03.jpg)

[**FIGURE 2.3**](#C_005_c2.xhtml#f2_3b) *Mask grid and its corresponding coordinate system.*

### 2.3.2 Filter Operation

The effect of a filter on an image is completely defined by the coefficients of the matrix *H*(*i*,*j*). The way in which the filtering process is carried out on the image is shown in [Figure 2.4](#C_005_c2.xhtml#f2_4). This process can be described as follows:

![FIGURE 2.4 Linear filters. The origin of the filter coefficient matrix is placed at the original image I pixel \\left( {x,y} \\right). The filter coefficients H\\left( {i,j} \\right) are multiplied by the corresponding pixels of the image, thus obtaining nine different products. All products are added, and the result is placed at the position \\left( {x,y} \\right) of the result image I′.](images/Fig02_04.jpg)

[**FIGURE 2.4**](#C_005_c2.xhtml#f2_4b) Linear filters. The origin of the filter coefficient matrix is placed at the original image *I* pixel (*x*,*y*). The filter coefficients *H*(*i*,*j*) are multiplied by the corresponding pixels of the image, thus obtaining nine different products. All products are added, and the result is placed at the position (*x*,*y*) of the result image *I′*.

For each pixel (*x*,*y*) of the image, the following steps are carried out:

1.  The filter matrix *H*(*i*,*j*) is positioned on the original image *I* at pixel *I*(*x*,*y*) in such a way that its coordinate center *H*(0,0) coincides with it.
2.  The pixels of the image that are located within the region *R*(*x*,*y*) defined by the filter matrix *H*(*i*,*j*) are multiplied by the corresponding coefficients for each position *I*^′(*x*,*y*) of the filter matrix, and the partial result of each of these multiplications is added.
3.  The outcome is placed at the position (*x*,*y*) of the resulting image.

In other words, all pixels in the resulting image are calculated using the following equation:

$I^{\\prime}\\left( {x,y} \\right) = {\\sum\\limits\_{{({i,j})}eR{({x,y})}}{I\\left( {x + i,y + j} \\right) \\cdot H\\left( {i,j} \\right)}}$ (2.5)

For a typical filter with a matrix of coefficients of size 3 × 3, the following equation specifies its operation:

$I^{\\prime}\\left( {x,y} \\right) = {\\sum\\limits\_{j = - 1}^{1}{\\sum\\limits\_{i = - 1}^{1}{I\\left( {x + i,y + j} \\right) \\cdot H\\left( {i,j} \\right)}}}$ (2.6)

The operation modeled by Equation 2.6 is applied to all coordinates of the image (*x*,*y*). Something important that must be considered at this point is that the previous equation is not literally applicable to all the pixels of the image. At the edges of the image, there are elements at which, when centering the matrix of filter coefficients, these do not have correspondence, and a result cannot be clearly established. This problem will be dealt with again with its solutions in [Section 2.5.2](#C_005_c2.xhtml#h2_5_2).

## 2.4 Calculation of Filter Operations in MATLAB

After knowing how to perform filter operations and being warned to consider their effects on the borders of the image, the way in which it is possible to implement this type of operation through programming in MATLAB^® will be shown.

The application of the spatial filters on images is carried out by applying a convolution between the pixel of interest (*x*,*y*), its neighbors, and the coefficients of the mask \[[5](#C_005_c2.xhtml#r2_5)\]. The spatial filtering processing mechanism is shown in [Figure 2.4](#C_005_c2.xhtml#f2_4). The main part of this process lies in the relationship between the coordinates of the filter and those belonging to the image. The process consists of moving the center of the filter from left to right and from top to bottom, performing the corresponding convolution for all pixels in the image. [Figure 2.5](#C_005_c2.xhtml#f2_5) shows an illustration of this process. For a filter of size *m*  ×  *n*, we have that *m* = 2*a* + 1 and *n* = 2*b* + 1, where *a* and *b* are non-negative integers. This means that filters are always designed in odd dimensions, with the smallest dimension being 3 × 3. Although this is not a requirement, working with odd coefficient matrices facilitates the processing as there is a single center, and the operation is done symmetrically.

![FIGURE 2.5 Application of the spatial filter to an image.](images/Fig02_05.jpg)

[**FIGURE 2.5**](#C_005_c2.xhtml#f2_5b) Application of the spatial filter to an image.

The value of the new pixel (*x*,*y*) generated from the filter depends on the intensity values that correspond to the filter coefficients in a defined region *R*(*x*,*y*). Considering that we have the filter coefficients and the image intensity values shown in [Figure 2.6](#C_005_c2.xhtml#f2_6), the new pixel value is computed as follows:

![FIGURE 2.6 Spatial filtering process.](images/Fig02_06.jpg)

[**FIGURE 2.6**](#C_005_c2.xhtml#f2_6b) Spatial filtering process.

$\\begin{array}{cl} {I^{\\prime}\\left( {x,y} \\right)} & {= I\\left( {x - 1,y - 1} \\right) \\cdot H\\left( {- 1, - 1} \\right)} \\\\ & {+ I\\left( {x - 1,y} \\right) \\cdot H\\left( {- 1,0} \\right) + I\\left( {x - 1,y + 1} \\right) \\cdot H\\left( {- 1,1} \\right)} \\\\ & {+ I\\left( {x,y - 1} \\right) \\cdot H\\left( {0, - 1} \\right) + I\\left( {x,y} \\right) \\cdot H\\left( {0,0} \\right)} \\\\ & {+ I\\left( {x,y + 1} \\right) \\cdot H\\left( {0,1} \\right) + I\\left( {x + 1,y - 1} \\right) \\cdot H\\left( {1, - 1} \\right)} \\\\ & {+ I\\left( {x + 1,y} \\right)H\\left( {1,0} \\right) + I\\left( {x + 1,y + 1} \\right)H\\left( {1,1} \\right)} \\\\ \\end{array}$ (2.7)

An important aspect of implementation that must be taken into account is the effect that the limits of the image have on the processing. In the limits of the image, several filter coefficients from *H* will not correspond to some elements from the image *I*. This problem and how it can be solved will be discussed later. A representation of this problem is shown in [Figure 2.7](#C_005_c2.xhtml#f2_7).

![FIGURE 2.7 Problem of the limits of the image in the processing of the convolution. In the pixel (0,0) of the image, if the filter is centered, there will be coefficients of H on which there are no correspondent pixels from the image.](images/Fig02_07.jpg)

[**FIGURE 2.7**](#C_005_c2.xhtml#f2_7b) Problem of the limits of the image in the processing of the convolution. In the pixel (0,0) of the image, if the filter is centered, there will be coefficients of *H* on which there are no correspondent pixels from the image.

A simple solution is to only consider a smaller size of the image in the processing. Under this approach, if we have an image of size *M* × *N* instead of processing the convolution between the image and filter from 1 to *N* and from 1 to *M*, the processing will be done by removing the image borders. Therefore, the processing will be conducted from 2 to *N* − 1 and from 2 to *M* − 1. Applying this, for each filter coefficient, there will be a corresponding pixel of the image.

There are two alternatives to avoid the problem of the lack of correspondence within the limits of the image. The first is to generate a smaller result image compared to the original  *M* − 2 × *N* − 1 (we have previously discussed). Another option is to copy rows and columns from the original image in order to define the missing pixels.

## 2.5 Types of Linear Filters

The function of a linear filter is specified by the value of its coefficients. Since the coefficients can consist of different values, there are an infinite number of linear filters \[[6](#C_005_c2.xhtml#r2_6)\]. From the above, the question is: For what type of effect can a filter be used? And for a certain effect, what are the most suitable filters? In practice, there are two kinds of linear filters: smoothing filters and different filters.

### 2.5.1 Smoothing Filters

The filters discussed in the preceding sections consider a smoothing effect over the original image. Every linear filter whose coefficient matrix consists only of positive coefficients has in some way a smoothing effect on an image. From this operation, it can be verified that the result is a scaled version of the average value of the region *R*(*x*,*y*) covered by the filter.

### 2.5.2 The “Box” Filter

The box filter is the simplest and oldest of all the filters that perform smoothing on an image. [Figure 2.8](#C_005_c2.xhtml#f2_8) shows (a) the three-dimensional, (b) two-dimensional, and (c) mask functions implemented by this type of filter. Due to the sharp edges that it implements and its frequency behavior, the “Box” filter is a smoothing filter that is not highly recommended for applications. The filter, as can be seen in [Figure 2.8a](#C_005_c2.xhtml#f2_8), looks like a box (hence its name) and affects each pixel of the image in the same way (since all its coefficients have the same value). A desirable characteristic of a smoothing filter is that its effect on the image is invariant to rotation. Such a property is called isotropic.

![FIGURE 2.8 The Box filter for smoothing. (a) Three-dimensional, (b) two-dimensional, and (c) coefficient matrix that implements the filter.](images/Fig02_08.jpg)

[**FIGURE 2.8**](#C_005_c2.xhtml#f2_8b) The Box filter for smoothing. (a) Three-dimensional, (b) two-dimensional, and (c) coefficient matrix that implements the filter.

### 2.5.3 The Gaussian Filter

The Gaussian filter corresponds to a two-dimensional and discrete Gaussian function, which can be formulated as follows:

$G\_{\\sigma}\\left( r \\right) = e^{\\frac{r^{2}}{2\\sigma^{2}}}\\,\\text{or}\\,\\, G\_{\\sigma}xy = e^{\\frac{x^{2} + y^{2}}{2\\sigma^{2}}}$ (2.8)

where the standard deviation *σ* represents the influence radius of the Gaussian function, as shown in [Figure 2.9](#C_005_c2.xhtml#f2_9).

![FIGURE 2.9 The Gaussian filter for smoothing. (a) Three-dimensional, (b) two-dimensional, and (c) coefficient matrix that implements the filter.](images/Fig02_09.jpg)

[**FIGURE 2.9**](#C_005_c2.xhtml#f2_9b) The Gaussian filter for smoothing. (a) Three-dimensional, (b) two-dimensional, and (c) coefficient matrix that implements the filter.

In the Gaussian filter, the central element of the filter represents the maximum weight that participates in the linear combination of the operation, while the values of the other coefficients have less influence as they move away from the center of the filter.

An important property of this filter is known as isotropy. A problem with the “Box” smoothing filter is that its attenuation also causes a degradation in important characteristics of the image, such as edges (regions of the image where there is a sudden change in intensity) or corners. The Gaussian filter is less harmful in this sense, allowing the smoothing of the regions where the intensity values are homogeneous without diluting the characteristics of the image.

[Program 2.1](#C_005_c2.xhtml#p2_1) shows the MATLAB code to implement a filter 3 × 3 that smooths the image by averaging neighboring pixels, as was discussed in Equation 2.4.

### 2.5.4 Difference Filters

If a filter contains negative numbers as part of its coefficients, its operation can be interpreted as the difference between two different sums: The sum of all the linear combinations of the positive coefficients of the filter minus the sum of all the linear combinations due to the negative coefficients within the region defined by the filter *R*(*x*,*y*). If we express this operation mathematically, it can be defined as follows:

$\\begin{array}{cl} {I^{\\prime}\\left( {x,y} \\right)} & {= {\\sum\\limits\_{{({i,j})} \\in R^{+}}{I\\left( {x + i,y + j} \\right) \\cdot \\left| {H\\left( {i,j} \\right)} \\right|}}} \\\\ & {- {\\sum\\limits\_{{({i,j})} \\in R^{-}}{I\\left( {x + i,y + j} \\right) \\cdot \\left| {H\\left( {i,j} \\right)} \\right|}}} \\\\ \\end{array}$ (2.9)

where *R*^+ refers to the part of the filter with positive coefficients *H*(*i*,*j*) > 0 and *R*^− to the part of the filter with negative coefficients  *H*(*i*,*j*) < 0. As an example, it is shown in [Figure 2.10](#C_005_c2.xhtml#f2_10): the Laplace filter of size 5 × 5. It calculates the difference between the central point (the only positive coefficient with a value of 16) and the negative sum of 12 coefficients with values from ‒1 to –2. The remaining coefficients are zero and are not considered in the processing. This filter implements the function known as “the Mexican hat,” which has the following model:

![FIGURE 2.10 The Laplace (or Mexican hat) filter. (a) Three-dimensional, (b) two-dimensional, and (c) the coefficients that define the filter.](images/Fig02_10.jpg)

[**FIGURE 2.10**](#C_005_c2.xhtml#f2_10b) The Laplace (or Mexican hat) filter. (a) Three-dimensional, (b) two-dimensional, and (c) the coefficients that define the filter.

$M\_{\\sigma}\\left( r \\right) = \\frac{1}{\\sqrt{2\\text{π}}\\sigma^{3}}\\left( {1 - \\frac{r^{2}}{\\sigma^{2}}} \\right)e^{- \\frac{r^{2}}{2\\sigma^{2}}}$ (2.10)

$M\_{\\sigma}\\left( {x,y} \\right) = \\frac{1}{\\sqrt{2\\text{π}}\\sigma^{3}}\\left( {1 - \\frac{x^{2} + y^{2}}{\\sigma^{2}}} \\right)e^{- \\frac{x^{2} + y^{2}}{2\\sigma^{2}}}$ (2.11)

The models expressed in Equation 2.11 correspond to the same formulation but in one-dimensional and two-dimensional cases. While with filters with positive coefficients, the effect obtained is smoothing, with difference filters (which have positive and negative coefficients), the effect is the opposite. Therefore, the differences between pixel intensity levels are enhanced. For this reason, these types of filters are normally used for edge detection.

## 2.6 Formal Characteristics of Linear Filters

Until now, the concept of filters has been considered in a simple way so that the reader can get a quick idea of their characteristics and properties. Although this may be sufficient from a practical point of view, there are situations where the understanding of the mathematical properties of their operations allows to design and analyze more complex filters. The operation on which the filters are based is convolution. This operation and its characteristics will be discussed throughout this chapter.

### 2.6.1 Linear Convolution and Correlation

The operation of a linear filter is based on an operation called linear convolution. This operation allows associating two continuous or discrete functions in one. For two two-dimensional discrete functions *I* and *H* the linear convolution is defined as follows:

$I^{\\prime}\\left( {x,y} \\right) = {\\sum\\limits\_{i = - \\infty}^{\\infty}{\\sum\\limits\_{j = \\infty}^{\\infty}{I\\left( {x - i,y - j} \\right) \\cdot H\\left( {i,j} \\right)}}}$ (2.12)

Or in compact form:

*I*^′ = *I* \* *H* (2.13)

The expression in Equation 2.12 is very similar to the one defined in 2.6, with the exception of the limits in the summations for *i*, *j*, and the sign in the coordinates *I*(*x*−*i*,*y*−*j*). The first difference is explained by the fact that the filter *H*(*i*,*j*) defines a region *R*(*x*,*y*) of influence that contains a finite set of coefficients; outside this region, the coefficients are considered zero or not relevant, so the limit of the sum could be extended without altering the result of the calculation.

Regarding the coordinates, Equation 2.12 can be reformulated again as follows:

$\\begin{array}{ccl} {I\\left( {x,y} \\right)} & = & {\\sum\\limits\_{{({i,j})} \\in R}{I\\left( {x - i,y - j} \\right) \\cdot H\\left( {i,j} \\right)}} \\\\ & = & {\\sum\\limits\_{{({i.j})} \\in R}{I\\left( {x + i,y + j} \\right) \\cdot H\\left( {- i, - j} \\right)}} \\\\ \\end{array}$ (2.14)

This expression is again similar to the one defined in Equation 2.5, when the operation of the filter coefficient matrix was defined, only that the coefficient matrix is inverted in the vertical and horizontal directions *H*(−*i*,−*j*). Such an inversion can be interpreted as a 180° rotation of the filter coefficient matrix *H*(*i*,*j*). [Figure 2.11](#C_005_c2.xhtml#f2_11) shows how the inversion of the coordinates is modeled by rotating the filter coefficient matrix *H*(*i*,*j*).

![FIGURE 2.11 Coordinate inversion modeling H\\left( {- i, - j} \\right) by a rotation of 180° of the filter coefficient matrix.](images/Fig02_11.jpg)

[**FIGURE 2.11**](#C_005_c2.xhtml#f2_11b) Coordinate inversion modeling *H*(−*i*,−*j*) by a rotation of 180° of the filter coefficient matrix.

A concept very close to convolution is correlation. Correlation is the process of processing the mask or filter *H*(*i*,*j*) through the image (similar to the filter operation defined by Equation 2.5). Therefore, we can say that convolution is equal to correlation only with the difference that the filter coefficient matrix is rotated 180° (with its coordinate axes inverted) before performing the linear combination of coefficients and pixel values. The mathematical operation behind each linear filter operation is convolution, and its result is exclusively dependent on the value of the coefficients of the filter matrix *H*(*i*,*j*). [Figure 2.12](#C_005_c2.xhtml#f2_12) shows the convolution process in images.

![FIGURE 2.12 Convolution with the Gaussian filter. The original image is convolved with the coefficient matrix H\\left( {i,j} \\right) producing the result.](images/Fig02_12.jpg)

[**FIGURE 2.12**](#C_005_c2.xhtml#f2_12b) Convolution with the Gaussian filter. The original image is convolved with the coefficient matrix *H*(*i*,*j*) producing the result.

### 2.6.2 Linear Convolution Properties

The importance of convolution is due to its very interesting mathematical properties. As will be seen later in this book, there is a close relationship between convolution, Fourier analysis, and their corresponding methods at frequency \[[7](#C_005_c2.xhtml#r2_7)\].

#### 2.6.2.1 Commutativity

The convolution is commutative, which means that:

*I* \* *H* = *H* \* *I*

It represents the same result if the image and the filter exchange order positions in the operation, so there is no difference if the image *I* with the coefficient matrix *H*(*i*,*j*) is convolved or vice versa. Both functions can exchange positions, obtaining the same result.

#### 2.6.2.2 Linearity

This property implies some important properties. If an image is scaled with a constant *a* and then this result is convolved by the coefficient matrix *H*, the same result would be obtained as if the image was first convolved and the result of this operation was scaled by *a*. That is:

(*a*⋅*I*) \* *H* = *a* ⋅ (*I*\**H*) (2.15)

Furthermore, if two images are added pixel by pixel and then the result is convolved by *H*, it would give the same result as if both images were firstly convolved and finally the result of each convolved image is added. That is:

(*I*[1]+*I*[2]) \* *H* = (*I*[1]\**H*) + (*I*[2]\**H*) (2.16)

It might be surprising in this context that adding a constant *b* to an image that is then convolved through the *H* window of a filter does not produce the same result as if the image was first convolved and then the constant *b* is added to it. That is:

(*b*+*I*) \* *H* ≠ *b* + *I* \* *H* (2.17)

The linearity of the filter operations due to the use of convolution is an important theoretical concept; however, in practice, the filter operations are involved in processes that limit this linearity. This fact is provoked by rounding errors or the restriction in the range of images to which they are restricted to visualize them (“Clamping”).

#### 2.6.2.3 Associativity

Convolution is an associative operator, which means that the set of operations performed one by one in a sequence could change their grouping order without affecting the original result. That is:

*A* \* (*B*\**C*) = (*A*\**B*) \* *C* (2.18)

The association capacity of the filters is important since the application sequence of a set of filters could be reduced to one, which is normally carried out for the design of coefficient matrices. The opposite case is also valid, where a filter can be broken down into simpler operations performed by smaller filters.

### 2.6.3 Filter Separability

An immediate consequence of Equation 2.18 is the possibility of describing a filter by the convolution of two or more filters that are tentatively simpler and smaller than the original. Therefore, the convolution performed by a “big” filter on an image could be decomposed by a sequence of convolutions performed by small filters such that:

*I* \* *H* = *I* \* (*H*[1]\**H*[2]\**H*[3]…*H*[*n*]) (2.19)

The advantage obtained by this separation is to increase the speed of the operations since, although the number of filters is increased, among all of them, being smaller and simpler, they perform fewer operations than the original filter.

#### 2.6.3.1 x-y Separation

Something frequent and important in the use of filters is the separation of a two-dimensional filter *H* into two one-dimensional filters that operate horizontally *H*[*x*] and *H*[*y*] vertically on an image. If we assume that we have two one-dimensional filters *H*[*x*] and *H*[*y*] that they operate in each of the directions, then:

$H\_{x} = \\left\\lbrack {1\\operatorname{}\\operatorname{}\\operatorname{}\\operatorname{}1\\operatorname{}\\operatorname{}\\operatorname{}\\operatorname{}1\\operatorname{}\\operatorname{}\\operatorname{}\\operatorname{}1\\operatorname{}\\operatorname{}\\operatorname{}\\operatorname{}1} \\right\\rbrack\\,\\,\\text{or}\\,\\, H\_{y} = \\begin{bmatrix} 1 \\\\ 1 \\\\ 1 \\\\ \\end{bmatrix}$ (2.20)

If you want to use both filters, one with the other on image *I*, both filters can be used as follows:

*I*←(*I*\**H*[*x*])\**H*[*y*]\=*I*\**H*[*x*]\**H*[*y*] (2.21)

The same result can be obtained by applying the filter *H*[*x**y*] on the image, which is the convolution of both directional filters *H*[*x*] and *H*[*y*], such as follows:

$H\_{xy} = H\_{x} \\ast H\_{y} = \\left\\lbrack {\\begin{matrix} 1 \\\\ 1 \\\\ 1 \\\\ \\end{matrix}\\operatorname{}\\operatorname{}\\begin{matrix} 1 \\\\ 1 \\\\ 1 \\\\ \\end{matrix}\\operatorname{}\\operatorname{}\\begin{matrix} 1 \\\\ 1 \\\\ 1 \\\\ \\end{matrix}\\operatorname{}\\operatorname{}\\begin{matrix} 1 \\\\ 1 \\\\ 1 \\\\ \\end{matrix}\\operatorname{}\\operatorname{}\\begin{matrix} 1 \\\\ 1 \\\\ 1 \\\\ \\end{matrix}} \\right\\rbrack$ (2.22)

Under such conditions, the “Box” *H*[*x**y*] smoothing filter can be divided into two one-dimensional filters applied in two different directions on the image. The convolution performed by the full filter *H*[*x**y*] needs 3 × 5 = 15 operations per pixel in the original image. In the case of the two filters *H*[*x*] and *H*[*y*], they require 3 + 5 = 8 operations per pixel of the image, which is much less.

#### 2.6.3.2 Gaussian Filter Separation

A two-dimensional filter can be divided into two filters in the *x* − *y* directions. Following this methodology, it can be generalized that if you have a function in two dimensions, it is also possible to divide it into two functions, where each function will deal with each dimension in particular. That is, mathematically:

*H*[*x*, *y*](*i*,*j*) = *H*[*x*](*i*) ⋅ *H*[*y*](*j*) (2.23)

A prominent case is a Gaussian function *G*[*σ*](*x*,*y*) which can be partitioned as the product of two one-dimensional functions as follows:

$G\_{\\sigma}\\left( {x,y} \\right) = e^{- \\frac{x^{2} + y^{2}}{2\\sigma^{2}}} = e^{- \\frac{x^{2}}{2\\sigma^{2}}} \\cdot e^{- \\frac{y^{2}}{2\\sigma^{2}}} = g\_{\\sigma}\\left( x \\right) \\cdot g\_{\\sigma}\\left( y \\right)$ (2.24)

Therefore, it is clear that a two-dimensional Gaussian filter *H*^(*G*, *σ*) can be divided into a pair of Gaussian *H*[*x*]^(*G*, *σ*) and *H*[*y*]^(*G*, *σ*) one-dimensional filters. They can be defined as follows:

*I*←*I*\**H*^(*G*, *σ*)\=*I*\**H*[*x*]^(*G*, *σ*)\**H*[*y*]^(*G*, *σ*) (2.25)

The Gaussian function decays slowly. Hence, to avoid errors due to rounding of coefficients, it cannot implement values of *σ* < 2.5. Therefore, for a filter that incorporates a standard deviation of *σ* = 10, a filter of dimensions 51 × 51 is needed. If the filters were separated in two, as seen above, the filter would implement the operation 50 times faster than using the original filter.

### 2.6.4 Impulse Response of a Filter

The Delta Dirac *δ* function is a neutral element in the convolution operation. When this function *δ* is convolved with an image *I*, the result is the image *I* without any change. This effect can be defined as follows:

*I* \* *δ* = *I* (2.26)

The Delta Dirac function *δ*(⋅) in the two-dimensional discrete case is defined as:

$\\delta\\left( {i,j} \\right) = \\left\\{ \\begin{matrix} {1\\,\\text{for}\\, i = j = 0} \\\\ {0\\operatorname{}\\,\\text{if}\\,\\text{not}} \\\\ \\end{matrix} \\right.$ (2.27)

The Delta Dirac function, considered as an image, is visualized as a single bright point at the origin of coordinates around an area of infinite black points. [Figure 2.13](#C_005_c2.xhtml#f2_13) shows the Delta Dirac function in two dimensions and how it is conceived as an image.

![FIGURE 2.13 The Delta Dirac function in two dimensions.](images/Fig02_13.jpg)

[**FIGURE 2.13**](#C_005_c2.xhtml#f2_13b) The Delta Dirac function in two dimensions.

If the Delta Dirac function is used as a filter and we apply the convolution of this function to an image, the result is again the original image (see [Figure 2.14](#C_005_c2.xhtml#f2_14)).

![FIGURE 2.14 The result of the Delta Dirac function δ applied to an image I.](images/Fig02_14.jpg)

[**FIGURE 2.14**](#C_005_c2.xhtml#f2_14b) The result of the Delta Dirac function δ applied to an image *I*.

The opposite case is also interesting. If the Detla Dirac function is taken as input (as if this were the image) and convolved with a filter, the result would be the matrix of filter coefficients (see [Figure 2.15](#C_005_c2.xhtml#f2_15)), that is:

![FIGURE 2.15 The result of convolving the function δ and a filter H.](images/Fig02_15.jpg)

[**FIGURE 2.15**](#C_005_c2.xhtml#f2_15b) The result of convolving the function δ and a filter *H*.

*H* \* *δ* = *H* (2.28)

The application of this property makes sense if the properties and characteristics of the filter are not known and are desired to be characterized under the condition that the filter to be analyzed is a linear filter. If we apply the impulse function, the filter information can be obtained. The response of a filter to the impulse function is called the impulse response of the filter and is of great value in the analysis and synthesis of engineering systems.

## 2.7 Add Noise to Images with MATLAB

To test the effectiveness of filters on images, it is necessary to evaluate their effects on images that contain artifacts or structures (noise) that need to be removed. As is logical to suppose, it is difficult to obtain images naturally with these characteristics. That is, it is not easy to obtain these kinds of images from the moment they are taken with a digital camera or scanner \[[8](#C_005_c2.xhtml#r2_8)\]. An easier way to get images with these characteristics is simply to artificially produce them, which means taking the image by some means and adding the artifacts through programming code.

Using MATLAB, it is possible, through its programming elements, to induce noise in images. The type of noise that can be modeled and added can be as complex as necessary. In this section, it is shown how to do it in the case of salt and pepper noise. Salt and pepper noise simulates random elements from two categories, white (salt) and black (pepper) pixels, in an image. This type of noise will be used to test the effect of filters designed in the following sections.

Due to the stochastic nature of this type of noise, it will be necessary to use some function in MATLAB that allows randomly giving a value between 1 and the maximum values that describe the size of the image and assigning it to the pair of elements that defines the position (*x*,*y*) of the pixel. Once the pixel is chosen, it is assigned a value that can be 255 (in the case of salt) or 0 (in the case of pepper). The MATLAB function that returns a pseudo-random number uniformly distributed between 0 and 1 is `rand`, whose format can be described as:

```
y = rand
```

where `y` assumes the value returned by the `rand` function, the value generated by `rand` is uniformly distributed between 0 and 1. Therefore, to cover the interval of interest, it is necessary to multiply it by the maximum limit of the interval.

An important aspect is that if the image is only distorted by placing only pixels with values of 0 and 255 when making a visual analysis or simply its display, it becomes somewhat complicated to appreciate the noise pixels. For this reason, it is a better option to add structures. The structure with which you can contaminate the image to generate noise can really be any, although the rectangular one is generally chosen for its simplicity. An important observation is that the structure must, in any case, be smaller than the filter used. Otherwise, the filter will not have the capacity to eliminate distortion. In this case, a structure of 3 × 2 is chosen since most of the filters proposed to explain their effects on images are of dimension 3 × 3. [Figure 2.16](#C_005_c2.xhtml#f2_16) shows the structure added as noise to the image, considering the relative position of the top left pixel.

![FIGURE 2.16 Structure added as noise in order to facilitate its visualization instead of the distortion of an individual pixel.](images/Fig02_16.jpg)

[**FIGURE 2.16**](#C_005_c2.xhtml#f2_16b) Structure added as noise in order to facilitate its visualization instead of the distortion of an individual pixel.

[Program 2.2](#C_005_c2.xhtml#p2_2) shows the MATLAB code that allows adding 2000 noise points, where 1000 corresponds to intensity value structures 255 (salt) and 1000 corresponds to intensity value structures 0 (pepper).

An important consideration is the need to protect the random position where the structure will be placed. If the structure is placed within the limits of the image, it will not be positioned within the image. To avoid this, the program checks if the structure is located in an appropriate position. This process guarantees that the structure will always be located in an appropriate position for its processing. [Figure 2.17](#C_005_c2.xhtml#f2_17) shows images that resulted from the execution of [Program 2.2](#C_005_c2.xhtml#p2_2).

![FIGURE 2.17 Distortion process of an image with salt and pepper noise carried out using Program 2.2. (a) Original image, (b) added salt and pepper noise (a gray background was placed to appreciate both structures 0 and 255), and (c) the image with the noise.](images/Fig02_17.jpg)

[**FIGURE 2.17**](#C_005_c2.xhtml#f2_17b) Distortion process of an image with salt and pepper noise carried out using [Program 2.2](#C_005_c2.xhtml#p2_2). (a) Original image, (b) added salt and pepper noise (a gray background was placed to appreciate both structures 0 and 255), and (c) the image with the noise.

To save time, you could use the function implemented in the image processing toolbox that allows you to add different types of noise to an image. This section will only explain how to do it for a specific type of salt and pepper noise.

The structure of the function is:

```
g=imnoise(f, ‘salt & pepper’, 0.2);
```

where `f` is the image that you want to contaminate with salt and pepper noise and 0.2 is the percentage of pixels (the number of pixels that will be salt and pepper) in the image that you want to contaminate, where 0.2, for example, indicates that 20% of the image pixels will be contaminated. `g` is the matrix that receives the image contaminated by the configured noise.

## 2.8 Spatial Non-Linear Filters

The use of linear filters to smooth and remove distortions from images has a great disadvantage; structures present in the image, such as points, edges, and lines, are also degraded (see [Figure 2.18](#C_005_c2.xhtml#f2_18)). This effect cannot be avoided by using some combination of linear filter coefficients. Therefore, if you want to smooth an image without affecting the quality of the structures present in the image, the use of linear filters is not an alternative \[[9](#C_005_c2.xhtml#r2_9)\]. This section presents and explains a special type of filter that allows solving this problem, at least in a better way than linear filters. Non-linear filters are able to eliminate noise without the undesired effects of distortions. Such filters are based on operations whose characteristics and properties are not linear.

![FIGURE 2.18 Linear smoothing degrades important structures in the image, such as edges (a) or lines (b).](images/Fig02_18.jpg)

[**FIGURE 2.18**](#C_005_c2.xhtml#f2_18b) Linear smoothing degrades important structures in the image, such as edges (a) or lines (b).

### 2.8.1 Maximum and Minimum Filters

Non-linear filters compute the result at a certain position (*x*,*y*) like the previous filters by using a certain region relative to the original image *R*. The simplest non-linear filters are the maximum and minimum filters. The maximum and minimum filters are correspondingly defined as:

$\\begin{array}{cl} {I^{\\prime}\\left( {x,y} \\right)} & {= \\min\\left\\{ {I\\left( {x + i,y + j} \\right)\\text{|}\\left( {i,j} \\right) \\in R} \\right\\}} \\\\ & {= \\text{min}\\left( {R\\left( {x,y} \\right)} \\right)} \\\\ \\end{array}$ (2.29)

$\\begin{array}{cl} {I^{\\prime}\\left( {x,y} \\right)} & {= \\text{max}\\left\\{ {I\\left( {x + i,y + j} \\right)\\text{|}\\left( {i,j} \\right) \\in R} \\right\\}} \\\\ & {= \\text{max}\\left( {R\\left( {x,y} \\right)} \\right)} \\\\ \\end{array}$

where *R*(*x*,*y*) represents the region relative to the position (*x*,*y*) defined by the filter (most of the time, it is a rectangle of 3 × 3). [Figure 2.19](#C_005_c2.xhtml#f2_19) shows the effect of the minimum filter on different image structures. As can be seen in the figure, the step of the image appears displaced to the right by the action of the minimum filter by an amount equal to the width of the region *R*(*x*,*y*) defined by the filter. On the other hand, a line is eliminated by the action of the filter as long as the width of the line is less than that defined by the filter.

![FIGURE 2.19 Effect of the minimum filter on different local shapes in an image. The original image is on top, and the result obtained by operating the filter is on the bottom. The value of A expresses the width of the filter used, which at the same time defines the region R considered by it. The step represented in image (a), due to the effect of applying the filter, is shifted to the right in A units. The line contained in image (b), if its width is less than that of A, disappears due to the effect of the filter operation.](images/Fig02_19.jpg)

[**FIGURE 2.19**](#C_005_c2.xhtml#f2_19b) Effect of the minimum filter on different local shapes in an image. The original image is on top, and the result obtained by operating the filter is on the bottom. The value of A expresses the width of the filter used, which at the same time defines the region R considered by it. The step represented in image (a), due to the effect of applying the filter, is shifted to the right in A units. The line contained in image (b), if its width is less than that of A, disappears due to the effect of the filter operation.

[Figure 2.20](#C_005_c2.xhtml#f2_20) shows the application of the minimum and maximum filters on an intensity image that was artificially contaminated with salt and pepper noise. The minimum filter eliminates the white points of the image because, in its operation, it finds the minimum of a region of influence *R*(*x*,*y*) defined by the filter, which, centered on the contaminated white pixel, will replace it with the minimum value found among its neighbors. In the same way, the pixels that have the minimum value allowed by the image (black or pepper) are enlarged in relation to the size A of the filter. The maximum filter naturally presents the opposite effect. That is, pixels representing distortions belonging to zero (pepper) or small intensity values will be eliminated, while white structures will also be increased. [Figure 2.20](#C_005_c2.xhtml#f2_20) shows the effect of applying the maximum and minimum filters to an image.

![FIGURE 2.20 Minimum and maximum filters. (a) The original image to which salt and pepper noise was artificially added (see Section 2.6), (b) image resulting from applying the 3 \\times 3 minimum filter, and (c) image resulting from applying the 3 \\times 3 maximum filter.](images/Fig02_20.jpg)

[**FIGURE 2.20**](#C_005_c2.xhtml#f2_20b) Minimum and maximum filters. (a) The original image to which salt and pepper noise was artificially added (see [Section 2.6](#C_005_c2.xhtml#h2_6)), (b) image resulting from applying the 3 × 3 minimum filter, and (c) image resulting from applying the 3 × 3 maximum filter.

### 2.8.2 The Median Filter

Obviously, it is impossible to build a filter that can remove all the imperfections or noise from the image and, at the same time, keep intact image structures considered important. It is not possible to differentiate which structures are important for the observer and which are not. The median filter is a good compromise in this dilemma.

The effect of fading edges on an image caused by the smoothing effect of linear filters is generally undesirable. The median filter allows you to remove artifacts and unwanted structures in the image without significantly affecting the edges. The median filter belongs to a special class of statistical filters, which, in addition to being non-linear, base their actions on some statistical-type operation.

In statistics, the median is the value of a set of data that leaves the same number of elements before and after it. According to this definition, the set of data less than or equal to the median will represent 50% of the data, and those that are greater than the median will represent another 50% of the total from the sample data.

Considering that *x*[1], *x*[2]⋯, *x*[*n*] is the total set of data ordered in increasing order, the median is defined as follows:

$M\_{e} = x\_{\\frac{n + 1}{2}}$ (2.30)

If *n* is odd, *M*[*e*] will be the central observation of the values once they have been ordered in increasing or decreasing order. If *n* is even, it will be the arithmetic average of the two central observations, that is:

$M\_{e} = \\frac{x\_{\\frac{n}{2}} + x\_{\\frac{n + 1}{2}}}{2}$ (2.31)

Therefore, it can be said that the median filter replaces each pixel of the image with the median of the intensity values within the region of influence *R*(*x*,*y*) defined by the filter. This can be expressed as follows:

*I*^′(*x*,*y*) = *M*[*e*](*R*(*x*,*y*)) (2.32)

To calculate the median of the data that integrates the region of interest *R*(*x*,*y*), it is only necessary to execute two steps. First, arrange the intensity values of the image that correspond to the region of influence defined by the filter in vector form. Then, rearrange them in increasing order. If there are repeated values, they will also be repeated in the new arrangement. [Figure 2.21](#C_005_c2.xhtml#f2_21) demonstrates the computation of the median on a filter with a region of size 3 × 3.

![FIGURE 2.21 Calculation of the median considering a filter of size 3 \\times 3.](images/Fig02_21.jpg)

[**FIGURE 2.21**](#C_005_c2.xhtml#f2_21b) Calculation of the median considering a filter of size 3 × 3.

Because a filter is normally defined as a matrix whose data set is odd, the median value always corresponds to the central value of the increasingly ordered vector corresponding to the region of interest  *R*(*x*,*y*).

It can be said that the median filter does not produce or calculate a new value with which the pixel of the image will be replaced, but rather this is an existing value in the region of interest of the filter selected as a result of data rearrangement. [Figure 2.22](#C_005_c2.xhtml#f2_22) illustrates the effect of a median filter on two-dimensional structures. From the results of this figure, it can be seen in 2.22a and 2.22b that when the structures are smaller than half of the filter, they are removed. On the other hand, when they are equal to or larger than half, as in 2.22c and 2.22d, they remain practically unchanged. [Figure 2.23](#C_005_c2.xhtml#f2_23) finally shows, using images, the effect of the median filter to remove distortions such as salt and pepper.

![FIGURE 2.22 Effect of the median filter on structures can be seen in (a) and (b); when the structures are smaller than half the filter. They are eliminated, while when they are equal to or greater than half, as in (c ) and (d), they remain practically unchanged.](images/Fig02_22.jpg)

[**FIGURE 2.22**](#C_005_c2.xhtml#f2_22b) Effect of the median filter on structures can be seen in (a) and (b); when the structures are smaller than half the filter. They are eliminated, while when they are equal to or greater than half, as in (c ) and (d), they remain practically unchanged.

![FIGURE 2.23 Results and comparison of the effect of the median filter. (a) The original image contaminated by salt and pepper noise (see Section 2.6). (b) Effect of the “Box” smoothing filter on the image (a). It can be seen how the filter is unable to eliminate the artifacts that distort the image; the only visible effect is their attenuation. (c) Median filter effect. It can be seen how this filter eliminates the noise present in the image.](images/Fig02_23.jpg)

[**FIGURE 2.23**](#C_005_c2.xhtml#f2_23b) Results and comparison of the effect of the median filter. (a) The original image contaminated by salt and pepper noise (see [Section 2.6](#C_005_c2.xhtml#h2_6)). (b) Effect of the “Box” smoothing filter on the image (a). It can be seen how the filter is unable to eliminate the artifacts that distort the image; the only visible effect is their attenuation. (c) Median filter effect. It can be seen how this filter eliminates the noise present in the image.

### 2.8.3 Median Filter with Multiplicity Window

The median filter considers, in its determination, a set of data. Therefore, if there is a value with a very small or very large value compared to the other data that is covered by the region of interest *R*(*x*,*y*) of the filter, it will not significantly alter the result. For this reason, the filter is very appropriate for removing salt and pepper noise.

With the median filter, all the pixels considered in the region of interest of the filter have the same importance in determining the result. As has been mentioned in several parts of this chapter, a desirable behavior in a filter would be to give greater weight to the central coefficient of the filter that corresponds to the pixel of the image to be replaced.

The median filter with a multiplicity window can be considered as a variant of the median filter, which, unlike the original, has a window *H* that gives different importance to each element depending on the corresponding coefficient of the filter matrix *H*. Thus, like linear filters, the matrix coefficients *H* scale their corresponding pixels in the image. However, the operation performed by this filter does not involve a multiplication of the filter coefficient by its corresponding pixel but multiplicity. In this context, it expresses the number of times the intensity value of the filter is presented where the median is calculated.

Under such conditions, the matrix of coefficients indicates in its total sum the number of data that are considered for the calculation of the median. Therefore, the size of the data *T* to be considered for the calculation of the median is distributed in a window of 3 × 3 considering the following matrix:

$H = \\begin{bmatrix} h\_{1} & h\_{2} & h\_{3} \\\\ h\_{4} & h\_{5} & h\_{6} \\\\ h\_{7} & h\_{8} & h\_{9} \\\\ \\end{bmatrix}$ (2.33)

*T* = *h*[1] + *h*[2] + *h*[3] + *h*[4] + *h*[5] + *h*[6] + *h*[7] + *h*[8] + *h*[9]

$T = {\\sum\\limits\_{i = 1}^{9}h\_{i}}$

As an example, consider if you have the filter *H* defined as:

$H = \\begin{bmatrix} 1 & 3 & 2 \\\\ 2 & 4 & 1 \\\\ 1 & 2 & 1 \\\\ \\end{bmatrix}$ (2.34)

The data size *T* considered is as follows:

$T = {\\sum\\limits\_{i = 1}^{9}h\_{i}} = 17$ (2.35)

Once the amount of data to be considered is known, the same method used in [Section 2.6.2](#C_005_c2.xhtml#h2_6_2) is applied to find the median of the data set. Therefore, if the data set defined by *T* is odd, the median is the central data of the collection ordered in increasing order, but if it is even, then the average of the central data of the collection will have to be calculated as it is shown in Equation 2.31. [Figure 2.24](#C_005_c2.xhtml#f2_24) illustrates the operation process of this filter.

![FIGURE 2.24 Calculation performed by the median filter with a multiplicity window of 3 \\times 3.](images/Fig02_24.jpg)

[**FIGURE 2.24**](#C_005_c2.xhtml#f2_24b) Calculation performed by the median filter with a multiplicity window of 3 × 3.

Considering this method, the coefficients of the matrix *H* must be positive, and if the coefficient in a certain position is zero, it will be noted that this pixel of the image will not be considered for the determination of the median. An example of this is the median cross filter defined in Equation 2.33, which, as its name implies, considers only the cross of the coefficient matrix data.

$H = \\begin{bmatrix} 0 & 1 & 0 \\\\ 1 & 1 & 1 \\\\ 0 & 1 & 0 \\\\ \\end{bmatrix}$ (2.36)

### 2.8.4 Other Non-Linear Filters

The median filter and its multiplicity window variant are just a few examples of non-linear filters that are frequently used and easy to explain. By the name of non-linear, we group all those filters that do not have the property of linearity. There are a large number of them that comply with the characteristic of nonlinearity. Some examples are the corner detector and the morphological filters that will be described in later chapters. An important difference between non-linear filters is that the existing mathematical and theoretical basis for this type of filter is not the same as in the case of linear filters, which are based on convolution and their associated properties.

## 2.9 Linear Spatial Filters in MATLAB

To explain the options that MATLAB implements for spatial filtering, we analyze the way in which the correlation and convolution operations are carried out in detail. Then, we will see the possible functions available in order to implement such operations in MATLAB.

### 2.9.1 Correlation Size and Convolution

To exemplify the way in which these operations are carried out, the one-dimensional case is considered for simplicity. Therefore, it is assumed that there is a function *f* and a kernel *k*, as is shown in [Figure 2.25a](#C_005_c2.xhtml#f2_25). For the correlation operation of a function and a kernel, we move both sequences in such a way that their reference points coincide, as shown in [Figure 2.25b](#C_005_c2.xhtml#f2_25). From [Figure 2.25b](#C_005_c2.xhtml#f2_25), it can be seen that there are coefficients that do not have a corresponding coefficient with which to interact. To solve this, the simplest thing is to add zeros at the beginning and at the end of the function *f* (see [Figure 2.25c](#C_005_c2.xhtml#f2_25)) so that during the displacement of the kernel. Therefore, a corresponding coefficient between both sequences is guaranteed.

![FIGURE 2.25 One-dimensional correlation operation performed between a function f and the kernel k. (a) Function and kernel, (b) alignment of both sequences at their reference point to perform correlation, (c) addition of zeros to the function to ensure correspondence of coefficients, (d) product between both sequences, and (e) ‘full’ result of the correlation.](images/Fig02_25.jpg)

[**FIGURE 2.25**](#C_005_c2.xhtml#f2_25b) One-dimensional correlation operation performed between a function *f* and the kernel *k*. (a) Function and kernel, (b) alignment of both sequences at their reference point to perform correlation, (c) addition of zeros to the function to ensure correspondence of coefficients, (d) product between both sequences, and (e) ‘full’ result of the correlation.

The correlation operation is performed by shifting the kernel to the right, where the values of the correlation sequence at each step are obtained by adding the multiplicand values of the corresponding coefficients of both sequences. As [Figure 2.25c](#C_005_c2.xhtml#f2_25) shows, the result of the first element of the correlation sequence is zero. The last value of the correlation sequence is represented by the last geometric displacement achieved by the kernel on the function *f*, in such a way that the last value of the kernel corresponds to the last value of the original function of *f* (without adding zeros). This process is shown in [Figure 2.25d](#C_005_c2.xhtml#f2_25).

If we execute the operation as described, the correlation sequence shown in [Figure 2.25e](#C_005_c2.xhtml#f2_25) will be obtained. It should be noted that if the reverse process is conducted, that is, the kernel is kept fixed and the displacement is carried out by the function *f*, the result would not be the same, so the order is important.

To use the functions implemented in MATLAB, it is important to associate the mathematical operations with the parameters used in their structure. Under such conditions, the correlation is considered ‘full’ if the operation is performed by moving the kernel *k* over the function *f*, with the addition of zeros.

Another alternative is to consider that the reference point is in the central coefficient of the kernel *k*. Therefore, the result will be equal to the size of the function *f*. This is because there will be fewer displacements between the kernel and the function. This type of operation is called ‘same’ in MATLAB. [Figure 2.26](#C_005_c2.xhtml#f2_26) shows the process of correlation with this variant.

![FIGURE 2.26 One-dimensional correlation operation performed between a function f and the kernel k considering that the reference point is the central coefficient of the kernel. (a) Function and kernel, (b) alignment of both sequences at their reference point to perform correlation, (c) addition of zeros to the function to ensure correspondence of coefficients, (d) product between both sequences, and (e) ‘same’ result of the correlation.](images/Fig02_26.jpg)

[**FIGURE 2.26**](#C_005_c2.xhtml#f2_26b) One-dimensional correlation operation performed between a function *f* and the kernel *k* considering that the reference point is the central coefficient of the kernel. (a) Function and kernel, (b) alignment of both sequences at their reference point to perform correlation, (c) addition of zeros to the function to ensure correspondence of coefficients, (d) product between both sequences, and (e) ‘same’ result of the correlation.

As a comparison, the same steps with which the ‘full’ correlation operation was developed are also established in [Figure 2.26](#C_005_c2.xhtml#f2_26). An important thing to note is that the result of this correlation has the same size as the sequence of the function *f*.

In convolution, as already explained, a 180° rotation is verified on the kernel *k*. Then, the same process of correlation is applied. As with the correlation, the cases of ‘full’ and ‘same’ resulting from the operation are also applicable here. Thus, the operation will be ‘full’ or ‘same’ if it is used as a reference point, the initial coefficient of the kernel (‘full’) or the central coefficient (‘same’). [Figure 2.27](#C_005_c2.xhtml#f2_27) shows the computation process in the case of correlation.

![FIGURE 2.27 One-dimensional convolution operation performed between a function f and the kernel k rotated by 180°. (a) Function and kernel, (b) alignment of both sequences at their reference point to perform correlation, (c) addition of zeros to the function to ensure correspondence of coefficients, (d) product between both sequences, and (e) ‘full’ result of the correlation.](images/Fig02_27.jpg)

[**FIGURE 2.27**](#C_005_c2.xhtml#f2_27b) One-dimensional convolution operation performed between a function *f* and the kernel *k* rotated by 180°. (a) Function and kernel, (b) alignment of both sequences at their reference point to perform correlation, (c) addition of zeros to the function to ensure correspondence of coefficients, (d) product between both sequences, and (e) ‘full’ result of the correlation.

From the figure, it is evident that rotating the kernel *k* by 180° reverses the reference point. The other steps are the same as those shown for the correlation case. Another important observation from the result of the convolution in its ‘full’ version is that it is exactly the same as that of the correlation for the same case, with the exception that the order of the sequence is exactly the opposite. Therefore, it is noted there is a close relationship between both operations. Similarly, the convolution can be calculated in its ‘same’ variant with the sole consideration that the kernel itself will have to be rotated. When it is inverted, it will change the order of the sequence but not the reference point. It is symmetric in relation to the two ends of the sequence remaining in the same position. This is illustrated in [Figure 2.28](#C_005_c2.xhtml#f2_28).

![FIGURE 2.28 Rotation of the kernel to apply convolution.](images/Fig02_28.jpg)

[**FIGURE 2.28**](#C_005_c2.xhtml#f2_28b) Rotation of the kernel to apply convolution.

The same concepts discussed here can be extended to the case of images. [Figure 2.29](#C_005_c2.xhtml#f2_29) illustrates the correlation and convolution operations with their ‘full’ and ‘same’ variants.

![FIGURE 2.29 Correlation and convolution operations on images. (a) Original image f and kernel k, (b) original image to which “zeros” have been added in order to guarantee that there is an image value for each kernel coefficient, (c) start of the correlation of the kernel with the image to which zeros have been added, (d) result of the ‘full’ correlation, considering the image with the additional zeros, (e) result of the correlation of the same size ‘same’ as the image, without add zeros to the original image, it is the same size as the original, (f) original image and kernel rotated 180°, to convolve the image, (g) full result of the convolution, and (h) result of the convolution of the same size ‘same’ as the image.](images/Fig02_29.jpg)

[**FIGURE 2.29**](#C_005_c2.xhtml#f2_29b) Correlation and convolution operations on images. (a) Original image *f* and kernel *k*, (b) original image to which “zeros” have been added in order to guarantee that there is an image value for each kernel coefficient, (c) start of the correlation of the kernel with the image to which zeros have been added, (d) result of the ‘full’ correlation, considering the image with the additional zeros, (e) result of the correlation of the same size ‘same’ as the image, without add zeros to the original image, it is the same size as the original, (f) original image and kernel rotated 180°, to convolve the image, (g) full result of the convolution, and (h) result of the convolution of the same size ‘same’ as the image.

### 2.9.2 Handling Image Borders

An important problem, as has been repeatedly mentioned in previous sections, is the way in which the limits of the image should be processed. When the correlation or convolution operation is applied to an image with a filter, there will be filter coefficients at the edges of the image that do not have a corresponding intensity value in the image. How this problem is treated has some effect on the final result.

There are four alternatives to solve this problem:

*   \- Adding lines of zeros on the borders
*   \- Replicating lines of values equal to the last rows or columns of the image.
*   \- Adding the lines similar to if the image was reflected in a mirror.
*   \- Adding lines as if the image repeats itself cyclically.

Next, each of these elements will be briefly described. Then these concepts will also be associated with the way in which MATLAB incorporates such solutions into its functions.

*Adding lines of zeros on the borders*. This form has already been mentioned above as a solution to the border problem in images, in which lines of zeros are added, as many as necessary (depending on the size of the filter), to guarantee the coefficient-pixel correspondence. In MATLAB, this option to add zeros to the image is considered with the flag of `‘0’`. [Figure 2.30](#C_005_c2.xhtml#f2_30) illustrates this process.

![FIGURE 2.30 Adding zeros to the image in order to guarantee the correspondence of each filter coefficient per pixel of the image.](images/Fig02_30.jpg)

[**FIGURE 2.30**](#C_005_c2.xhtml#f2_30b) Adding zeros to the image in order to guarantee the correspondence of each filter coefficient per pixel of the image.

*Replicating lines of values equal to the last rows or columns of the image*. In this option, lines are added to the image that are equal to the border lines of the image, which, in other words, would mean increasing the size of the image by repeating the last row or column of the image. They are integrated as many times as necessary (depending on filter size). This alternative is preferred over just adding zeros. In MATLAB, this option is defined by the `‘replicate’` flag. [Figure 2.31](#C_005_c2.xhtml#f2_31) illustrates this process.

![FIGURE 2.31 Add the last column or row, depending on the case, to the image in order to guarantee the correspondence of each filter coefficient per pixel of the image.](images/Fig02_31.jpg)

[**FIGURE 2.31**](#C_005_c2.xhtml#f2_31b) Add the last column or row, depending on the case, to the image in order to guarantee the correspondence of each filter coefficient per pixel of the image.

*Adding the lines similar to if the image was reflected in a mirror*. In this case, rows or columns are added to the image as if the image was reflected in a mirror at its borders. This option is a bit more complicated to implement than the previous ones since the rows or columns are not fixed like the previous ones but rather vary depending on how many it will be necessary to add (depending on the size of the filter) to the image. In MATLAB, this option is defined by the `‘symmetric’` flag. [Figure 2.32](#C_005_c2.xhtml#f2_32) illustrates this process.

![FIGURE 2.32 Add columns or rows as appropriate to the image as if the image were reflected in a mirror at the borders of the image in order to guarantee the correspondence of each filter coefficient per pixel of the image.](images/Fig02_32.jpg)

[**FIGURE 2.32**](#C_005_c2.xhtml#f2_32b) Add columns or rows as appropriate to the image as if the image were reflected in a mirror at the borders of the image in order to guarantee the correspondence of each filter coefficient per pixel of the image.

*Adding lines as if the image repeats itself cyclically*. In this case, rows and columns are added to the image, considering it as if it were a signal that is repeated in all directions; that is, as if the image was spliced with an image above and below, on one side and on the other. In MATLAB, this option is defined by the `‘circular’` flag. [Figure 2.33](#C_005_c2.xhtml#f2_33) illustrates this process.

![FIGURE 2.33 Add columns or rows to the image as if the image were repeated cyclically on the borders in order to guarantee the correspondence of each filter coefficient per pixel of the image.](images/Fig02_33.jpg)

[**FIGURE 2.33**](#C_005_c2.xhtml#f2_33b) Add columns or rows to the image as if the image were repeated cyclically on the borders in order to guarantee the correspondence of each filter coefficient per pixel of the image.

### 2.9.3 MATLAB Functions for the Implementation of Linear Spatial Filters

The MATLAB image processing toolbox implements the function `imfilter` for linear spatial filtering of images, which has the following structure:

```
g=imfilter(f,H,filter_mode,border_options,result_size)
```

Where `g` is the filtered image and `f` is the image to be filtered with the filter `H`. The `filters_mode` flag specifies whether the function will use correlation (`‘corr’`) or convolution (`‘conv’`) for filtering. The `border_options` flag refers to the way in which the border problem will be solved by the function. The options are replicate, symmetric and circular, whose effects and implications were already discussed in Section, 2.8.2. The `result_siz`e flag indicates the size of the result obtained by the filter effect. Its options can be `same` and `full`. Similarly, the effects of these options were already explained in [Section 2.8.1](#C_005_c2.xhtml#h2_8_1). [Table 2.1](#C_005_c2.xhtml#t2_1) shows a summary of the flags and their possible options.

 [**TABLE 2.1**](#C_005_c2.xhtml#t2_1b) Summary of the Elements of the Structure from the imfilter Function 

 
| Options  || Description |
| --- | --- |
| *Filter mode* |
| --- |
| `corr` || Filtering is implemented by using correlation. This option is used by default. |
| `conv` || Filtering is implemented by using convolution. |
| *Border options* |
| `0` || The picture is completed by adding “zeros”. |
| `replicate` || The image is completed by adding rows or columns that are equal to the border rows and columns of the image. It’s the default option. |
| `symetric` || The image is completed with rows and columns equal to those obtained by mirror projection of the rows and columns of the reflected image. |
| `circular` || The image is completed with rows and columns equal to those obtained if the image is considered as a periodic signal, in such a way that the image is repeated above and below, on one side and on the other. |
| *Result size* |
| `full` || The resulting filtered image is the size of the image with the columns and rows added at the borders to ensure pixel-coefficient correspondence. |
| `same` || The result of the filtered image is the size of the original image. It’s the default option. |

As mentioned before, a convolution is the same as a correlation with the filter pre-rotated 180°. The opposite also applies. A correlation gives the same result as a convolution with the filter pre-rotated 180°. The above is important since the image processing toolbox defines several special filters that have been pre-rotated to be used directly with the correlation (default option) when they were originally planned to perform convolution on the image.

When we are working with a filter using convolution, there are two different options: one is to use the `filter_mode` (conv) flag of the `imfilter` function, and the other is to rotate the filter 180° and apply the `imfilter` function with its option default (corr). To rotate a matrix (in our case, a filter) with 180°, the following function can be used:

```
Hr=rot90(H,2)
```

where `Hr` is the filter rotated 180° and `H` is the filter to be rotated.

[Figure 2.34](#C_005_c2.xhtml#f2_34) shows the use of the `imfilter` function and the effect of using the different options corresponding to the `border_options` flag, considering as filter `H`, a “Box” smoothing filter of 31 × 31, which was obtained by the following command in MATLAB:

![FIGURE 2.34 Effect of using the different options of the ‘border\_options’ flag. (a) Original image, (b) effect on the image using the option ‘0’, (c) effect on the image using the option ‘replicate’, (d) effect on the image using option ‘symmetric’, and (e) effect on image when using ‘circular’ option.](images/Fig02_34.jpg)

[**FIGURE 2.34**](#C_005_c2.xhtml#f2_34b) Effect of using the different options of the ‘border\_options’ flag. (a) Original image, (b) effect on the image using the option ‘0’, (c) effect on the image using the option ‘replicate’, (d) effect on the image using option ‘symmetric’, and (e) effect on image when using ‘circular’ option.

```
H=ones(31,31)/(31*31);
```

As can be seen from [Figure 2.34b](#C_005_c2.xhtml#f2_34), the `‘0’` option when adding rows and columns with zeros produces a smoothing effect from black to white in regions where the original image does not have black pixels. The same happens in [Figure 2.34e](#C_005_c2.xhtml#f2_34), where there are added equal rows and columns (`‘circular’`) as if it were repeated above and below, on one side and on the other.

### 2.9.4 MATLAB Functions for Non-Linear Spatial Filtering

Non-linear filtering is based on the same mechanics as moving a mask along the image. However, unlike linear filtering, its operations do not consider the sum of multiplications between the filter coefficients and the image pixels. Another marked difference between linear and non-linear filtering is the role that plays the concept of masks or filter coefficients. In linear filters, filter coefficients determine the effect of the filter. On the other hand, in non-linear operations, the filter represents only the region of influence. Therefore, the mask symbolizes the pixels that will be considered in the processing and not the way in which they participate in the processing, as is the case in linear filtering. The image processing toolbox has two functions to perform non-linear filtering on images. These are: `nlfilter` and `colfilt`.

The `nlfilter` function allows filtering using a non-linear operation on an image. Its general syntax is:

```
B = nlfilter(A, [m n], @Fun);
```

where `m` and `n` determine the size of the region of influence of the non-linear filter that will be processed across the image. `A` corresponds to the image to be filtered, while `B` will contain the filtered image. `fun` defines a user function that implements the operation of the filter. This function receives from `nlfilter` a matrix of `mxn` data and returns the result of the non-linear operation implemented on that data. The @ symbol is called the function handle, which is a MATLAB data type that contains information about the function that is being used as a reference to implement the operation.

As an example, we will calculate the median filter using the `nlfilter` function. First, we need an image that contains salt and pepper noise. Therefore, considering the image exhibited in [Figure 2.35a](#C_005_c2.xhtml#f2_35), salt and pepper-type noise is added at 10%, obtaining [Figure 2.35b](#C_005_c2.xhtml#f2_35). This image has been produced using the following command:

![FIGURE 2.35 Use of the nlfilter function. (a) Original image, (b) image distorted with salt and pepper noise, and (c) image filtered by nlfilter using the function defined in Program 2.3 that implements the median spatial non-linear filter.](images/Fig02_35.jpg)

[**FIGURE 2.35**](#C_005_c2.xhtml#f2_35b) Use of the nlfilter function. (a) Original image, (b) image distorted with salt and pepper noise, and (c) image filtered by nlfilter using the function defined in [Program 2.3](#C_005_c2.xhtml#p2_3) that implements the median spatial non-linear filter.

```
Iruido=imnoise(I, ‘salt & pepper’, 0.1);
```

For the filtering, we will use a median filter defined by a neighborhood of 5 × 5. The operation (median) will be implemented using `nlfilter,` which will receive a matrix of 25 data. From these data, the median value is computed. The function created to implement this function is specified in [Program 2.3](#C_005_c2.xhtml#p2_3). Once the function that will be used by the `nlfilter` function has been implemented, the image is filtered by using the following command:

```
R = nlfilter(Iruido, [5 5], @mediana);
```

[Figure 2.35](#C_005_c2.xhtml#f2_35) illustrates the images used for the filtering performed by `nlfilter` and the effects obtained after this process.

The `colfilt` function performs the filtering by organizing the data in column form. This function is preferred over the `nlfilter` function since it achieves the calculation in a faster way.

Considering a region of interest *m* × *n*, the `colfilt` function operates on an image *I* of size *M* × *N*, generating a matrix *A* of size *m**n* × *M**N*, in which each column corresponds to the pixels that form the area of interest centered on a position in the image. For example, the first column of matrix *A* involves the pixels that are part of the area of interest, centered on the pixel at the top left (0,0) of the image *I* of dimension *M* × *N*. The general syntax of this function is:

```
g=colfilt(I,[m n], ‘sliding’, @Fun);
```

where *m* and *n* represent the size of the considered region of interest or filter size. `‘sliding’` indicates that the mask *m*  ×  *n* is displaced along the entire image *I* performing a pixel-by-pixel operation. `fun` defines a user function that implements the operation of the filter. This function receives from `colfilt` the matrix *A* of *m**n* × *M**N* and returns, as a result, a vector of 1  ×  *M**N* (the size of the image *I*) product of the implemented non-linear operation.

As an example, the median filter will be calculated again, but now with the `colfilt` function. As in the case of the `nlfilter` function, a filter with an area of interest of 5  ×  5 is selected. The function must be implemented so that it receives an array of size 25 × *M**N* and return, as a result, a 1 × *M**N* vector representing the medians of all the pixels in the image where the mask of 5 × 5 has been centered. [Program 2.4](#C_005_c2.xhtml#p2_4) shows the implementation of this function.

## 2.10 Binary Filter

This filter is designed to work on binary images. It consists of a set of Boolean equations that allow for the removal of noise from white and black areas. The filter also has equations to reconstruct corners of figures that have degraded angles. In order to explain the operation of the filter equations, the binary image defined in [Figure 2.36](#C_005_c2.xhtml#f2_36) is used as an example during the explanations.

![FIGURE 2.36 A binary image used to exemplify the operation of the binary filter.](images/Fig02_36.jpg)

[**FIGURE 2.36**](#C_005_c2.xhtml#f2_36b) A binary image used to exemplify the operation of the binary filter.

Using the window 3 × 3 shown in [Figure 2.37](#C_005_c2.xhtml#f2_37) as a processing reference, the new value *P*[0] will be obtained from *p* and pixels *a*,  *b*,  *c*,  *d*,  *e*,  *f*,  *g*,  *h* that are its neighbors. The computation process is similar to that used in linear filters, with the exception that, in this case, logical operations are used. Therefore, the elements can only have values of True (1) and False (0).

![FIGURE 2.37 Processing window used in the binary filter operation.](images/Fig02_37.jpg)

[**FIGURE 2.37**](#C_005_c2.xhtml#f2_37b) Processing window used in the binary filter operation.

The first step is to remove the noise or black artifacts from the white areas; for this propose, the following equation is used:

*P*[0] = *p* + (*b*⋅*g*⋅(*d*+*e*)) + (*d*⋅*e*⋅(*b*+*g*)) (2.37)

The result of this processing is shown in [Figure 2.38a](#C_005_c2.xhtml#f2_38). The second step is to remove the noise or white artifacts from the black areas, for which the equation is defined as follows:

![FIGURE 2.38 Binary filter operation. (a) Removal of black artifacts, (b) removal of white artifacts, (c) regeneration of corners of white elements, and (d) regeneration of corners on black objects.](images/Fig02_38.jpg)

[**FIGURE 2.38**](#C_005_c2.xhtml#f2_38b) Binary filter operation. (a) Removal of black artifacts, (b) removal of white artifacts, (c) regeneration of corners of white elements, and (d) regeneration of corners on black objects.

*P*[0] = *p* ⋅ (((*a*+*b*+*d*)⋅(*e*+*g*+*h*))+((*b*+*c*+*e*)⋅(*d*+*f*+*g*))) (2.38)

The result of this process is shown in [Figure 2.38b](#C_005_c2.xhtml#f2_38). To reconstruct the corners of the white figure, four different equations must be used, one for each corner of the figure. That is:

For the top right corner:

$P\_{0} = \\overline{p} \\cdot d \\cdot f \\cdot g \\cdot \\overline{\\left( {a+b+c+e+h} \\right)} + p$ (2.39)

For the lower right corner:

$P\_{0} = \\overline{p} \\cdot a \\cdot b \\cdot d \\cdot \\overline{\\left( {c+e+f+g+h} \\right)} + p$ (2.40)

For the top left corner:

$P\_{0} = \\overline{p} \\cdot e \\cdot g \\cdot h \\cdot \\overline{\\left( {a+b+c+d+f} \\right)} + p$ (2.41)

For the lower left corner:

$P\_{0} = \\overline{p} \\cdot b \\cdot c \\cdot e \\cdot \\overline{\\left( {a+d+f+g+h} \\right)} + p$ (2.42)

The result of these four operations is shown in [Figure 2.38c](#C_005_c2.xhtml#f2_38). Finally, from the last four equations, another four equations are necessary for the regeneration of the corners in the black figures. They are defined as follows:

For the top right corner:

$P\_{0} = p \\cdot \\left( {d + f + g} \\right) + \\overline{\\left( {a\\cdot b\\cdot c\\cdot e\\cdot h\\cdot p} \\right)}$ (2.43)

For the lower right corner:

$P\_{0} = p \\cdot \\left( {a + b + d} \\right) + \\overline{\\left( {c\\cdot e\\cdot f\\cdot g\\cdot h\\cdot p} \\right)}$ (2.44)

For the top left corner:

$P\_{0} = p \\cdot \\left( {e + g + h} \\right) + \\overline{\\left( {a\\cdot b\\cdot c\\cdot d\\cdot f\\cdot p} \\right)}$ (2.45)

For the lower left corner:

$P\_{0} = p \\cdot \\left( {b + c + e} \\right) + \\overline{\\left( {a\\cdot d\\cdot f\\cdot g\\cdot h\\cdot p} \\right)}$ (2.46)

The result of these four operations, which define the final result of the binary filter processing, is shown in [Figure 2.38d](#C_005_c2.xhtml#f2_38).

### 2.10.1 Implementation of the Binary Filter in MATLAB

This section shows how the binary filter can be implemented to operate on binary images. In the implementation of the filter, its operation was divided into four different functions, which must be applied sequentially.

The first function, called `remove_black_noise` removes artifacts or black points that are considered noise. This function is shown in [Program 2.5](#C_005_c2.xhtml#p2_5).

The function called `remove_white_point_noise` removes artifacts or white points that are considered noise. This function is shown in [Program 2.6](#C_005_c2.xhtml#p2_6).

The function called `rebuild_white_corners` reestablishes the corners on white objects that have degraded angles. This function is shown in [Program 2.7](#C_005_c2.xhtml#p2_7).

The function called `rebuild_black_corners` reestablishes the corners on black objects that have defined angles. This function is shown in [Program 2.8](#C_005_c2.xhtml#p2_8).

## References

1.  [O’Regan](#C_005_c2.xhtml#r2_1b), J. K. (2018). Advanced digital image processing and analysis. CRC Press.
2.  [Acharya](#C_005_c2.xhtml#r2_2b), T., & Ray, A. K. (2017). Image processing: Principles and applications. CRC Press.
3.  [McAndrew](#C_005_c2.xhtml#r2_3b), A. (2017). Introduction to digital image processing with MATLAB. CRC Press.
4.  [Russ](#C_005_c2.xhtml#r2_4b), J. C. (2011). The image processing handbook (6th ed.). CRC Press.
5.  [Marques](#C_005_c2.xhtml#r2_5b), O. (2011). Practical image and video processing using MATLAB. Wiley.
6.  [Khatun](#C_005_c2.xhtml#r2_6b), F., & Rahman, M. M. (2018). A Review of Edge Detection Techniques in Image Processing. Journal of Electromagnetic Analysis and Applications, 10(8), 206–214. [https://doi.org/10.4172/2332-0796.1000150](https://doi.org/10.4172/2332-0796.1000150)
7.  [Umbaugh](#C_005_c2.xhtml#r2_7b), S. E. (2017). Digital image processing and analysis: Human and computer vision applications with CVIPtools (2nd ed.). CRC Press.
8.  [Demirkaya](#C_005_c2.xhtml#r2_8b), O., & Asyali, M. H. (2016). Image processing with MATLAB: Applications in medicine and biology. CRC Press.
9.  [Umbaugh](#C_005_c2.xhtml#r2_9b), S. E. (2005). Handbook of image processing and computer vision, Volume 1: Algorithms and techniques. Wiley-Interscience.

# 3 Edge Detection

DOI: [10.1201/9781003287414-3](https://doi.org/10.1201/9781003287414-3)

Features in an image, such as edges, are detected through local changes in intensity or color \[[1](#C_006_c3.xhtml#r3_1)\]. They play an important role in image interpretation. The subjective “clarity” of an image is directly related to the discontinuities and sharpness of the structures present in it. The human eye gives an important weight to the edges of objects since it is through these that a person can differentiate the different characteristics as well as the delimitations of the real forms. Therefore, simple traces on images are enough to interpret the classes of the objects. For this reason, edges are very important topics for digital image processing and machine vision.

## 3.1 Borders and Contours

Edges play a predominant role in human vision and probably also in other biological vision systems. The edges are not only noticeable, but it is also possible by means of a few edge lines to reconstruct the objects again ([Figure 3.1](#C_006_c3.xhtml#f3_1)). One of the main issues to be discussed is how edges originate in an image and how it is possible to locate them to be used in a post-processing stage.

![FIGURE 3.1 (a) Original image and (b) image with borders.](images/Fig03_01.jpg)

[**FIGURE 3.1**](#C_006_c3.xhtml#f3_1b) (a) Original image and (b) image with borders.

Roughly, edges can be thought of as points in an image where the intensity in each direction changes dramatically \[[2](#C_006_c3.xhtml#r3_2)\]. Depending on the intensity change presented in a specific pixel, it will be the value of the edge in the image for that point. The size of the change is normally calculated from the derivative and is used as one of the most important approaches to determining the edges of an image.

## 3.2 Edge Detection Using Gradient-Based Techniques

Consider a single dimension and take as an example an image that has a white region in the center surrounded by a dark background, like [Figure 3.2a](#C_006_c3.xhtml#f3_2).

![FIGURE 3.2 First derivative in the one-dimensional case obtained from the horizontal profile of the image. Original image (a) and the derivative of the horizontal profile obtained from the image (b).](images/Fig03_02.jpg)

[**FIGURE 3.2**](#C_006_c3.xhtml#f3_2b) First derivative in the one-dimensional case obtained from the horizontal profile of the image. Original image (a) and the derivative of the horizontal profile obtained from the image (b).

The grayscale profile along a line in the image might look like [Figure 3.2b](#C_006_c3.xhtml#f3_2). We will define this one-dimensional signal as *f*(*u*). Its first derivative is defined as follows:

$f^{\\prime}\\left( u \\right) = \\frac{df}{du}\\left( u \\right)$ (3.1)

Thus, a positive elevation is produced in every place where the intensity increases and a negative one where the intensity decreases. However, the derivative is not defined for discrete functions such as *f*(*u*), so we need a method to calculate it.

It is known that the derivative of a function at a point *x* can be interpreted by the slope of the tangent at that particular point. However, for a discrete function, the derivative at a point *u* (the slope of the tangent to that point) can be calculated from the difference between the neighboring points *u* divided by the distant value between the two points \[[3](#C_006_c3.xhtml#r3_3)\], see [Figure 3.3](#C_006_c3.xhtml#f3_3). So, the derivative can be approximated as follows:

![FIGURE 3.3 Calculation of the first derivative for a discrete function. The slope of the line through the neighboring points f\\left( {u - 1} \\right) and f\\left( {u + 1} \\right) is used as an indirect way to calculate the slope to the tangent at f\\left( u \\right).](images/Fig03_03.jpg)

[**FIGURE 3.3**](#C_006_c3.xhtml#f3_3b) Calculation of the first derivative for a discrete function. The slope of the line through the neighboring points *f*(*u*−1) and *f*(*u*+1) is used as an indirect way to calculate the slope to the tangent at *f*(*u*).

$\\frac{df}{du}\\left( u \\right) \\approx \\frac{f\\left( {u + 1} \\right) - f\\left( {u - 1} \\right)}{2} = 0.5 \\cdot \\left( {f\\left( {u + 1} \\right) - f\\left( {u - 1} \\right)} \\right)$ (3.2)

The same process can also be used for the vertical direction along the column of the image.

### 3.2.1 Partial Derivative and Gradient

The partial derivative can be thought of as the derivative of a multidimensional function along a coordinate axis (with respect to one of the function variables), for example:

$\\frac{\\partial I\\left( {x,y} \\right)}{\\partial x}\\operatorname{}\\text{and}\\operatorname{}\\frac{\\partial I\\left( {x,y} \\right)}{\\partial y}\\operatorname{}$ (3.3)

The partial derivative of the image function *I*(*u*,*v*) with respect to the variable *u* or *v* can be defined as the following vector:

$\\nabla I\\left( {x,y} \\right) = \\begin{bmatrix} \\frac{\\partial I\\left( {x,y} \\right)}{\\partial x} \\\\ \\frac{\\partial I\\left( {x,y} \\right)}{\\partial y} \\\\ \\end{bmatrix}$ (3.4)

This formulation represents the gradient vector of function *I* at the point (*x*,*y*). The value of the gradient is modeled as follows:

$\\left| {\\nabla I} \\right| = \\sqrt{\\left( \\frac{\\partial I}{\\partial x} \\right)^{2} + \\left( \\frac{\\partial I}{\\partial y} \\right)^{2}}$ (3.5)

The value of |∇*I*| is invariant to image rotations and thus also independent of the orientation of the structures contained in it. This property is important for locating the edge points of the image; thus, the value of |∇*I*| is the practical value used in most of the algorithms considered for edge detection.

### 3.2.2 Derived Filter

The components of the gradient in Equation 3.4 are nothing more than the first derivative, both in the sense of the rows and the columns of the image. According to [Figures 3.2](#C_006_c3.xhtml#f3_2) and [3.3](#C_006_c3.xhtml#f3_3), the derivative in the horizontal direction is computed as a filter operation with the following matrix of coefficients:

$H\_{x}^{D} = \\begin{bmatrix} {- 0.5} & \\underset{\\\_}{0} & 0.5 \\\\ \\end{bmatrix} = 0.5 \\cdot \\begin{bmatrix} {- 1} & \\underset{\\\_}{0} & 1 \\\\ \\end{bmatrix}$ (3.6)

where the coefficient −0.5 affects the pixel *I*(*x*−1,*y*) and 0.5 affects the pixel *I*(*x*+1,*y*). The value of the middle pixel *I*(*x*,*y*) is multiplied by zero or equally ignored (here, the element under which the underscore “\_” is considered to represent the reference point or the pixel under which the property in question is calculated). In the same way, the same effect of the filter can be established, but now in the vertical direction, being its matrix of coefficients:

$H\_{y}^{D} = \\begin{bmatrix} {- 0.5} \\\\ \\underset{\\\_}{0} \\\\ 0.5 \\\\ \\end{bmatrix} = 0.5 \\cdot \\begin{bmatrix} {- 1} \\\\ 0 \\\\ 1 \\\\ \\end{bmatrix}$ (3.7)

[Figure 3.4](#C_006_c3.xhtml#f3_4) shows the effect of applying the filters defined in Equations 3.6 and 3.7 on an image. The dependency on direction presented in [Figure 3.4](#C_006_c3.xhtml#f3_4) is easy to recognize. The horizontal gradient filter *H*[*x*]^(*D*) reacts, resulting in a larger response in the horizontal direction and highlighting the edges in the vertical direction \[[Figure 3.4b](#C_006_c3.xhtml#f3_4)\]. In the same way, the *H*[*y*]^(*D*) filter acts, causing particularly large values in the vertical direction, thereby enhancing the horizontal edges of a structure \[[Figure 3.4c](#C_006_c3.xhtml#f3_4)\]. In the regions of the image where the filter response was null \[in [Figures 3.4b](#C_006_c3.xhtml#f3_4) and [c](#C_006_c3.xhtml#f3_4)\], the values were represented by gray pixels.

![FIGURE 3.4 The first partial derivatives. (a) Synthetic image, (b) first partial derivative on the horizontal direction \\partial I\\text{/}\\partial u, (c) on the vertical direction \\partial I\\text{/}\\partial v, (d) value of the gradient \\left| {\\nabla I} \\right|. In (b) and (c) are the dark values belonging to negative values, the brightest values belonging to positive values, while gray corresponds to zero.](images/Fig03_04.jpg)

[**FIGURE 3.4**](#C_006_c3.xhtml#f3_4b) The first partial derivatives. (a) Synthetic image, (b) first partial derivative on the horizontal direction ∂*I*/∂*u*, (c) on the vertical direction ∂*I*/∂*v*, (d) value of the gradient |∇*I*|. In (b) and (c) are the dark values belonging to negative values, the brightest values belonging to positive values, while gray corresponds to zero.

## 3.3 Filters for Edge Detection

The way of computing the local gradient corresponding to each pixel of the image is what fundamentally differentiates each of the operators for edge detection. The main difference is that the gradient is calculated as distinct directional components. Likewise, the partial results (obtained by each direction) are joined into a final one. In the computation of the gradient, we are interested not only in the value of the gradient in a pixel but also in the direction of the edge in question. However, as both elements (gradient value and direction) are implicit in the gradient calculation, it is possible to obtain them easily \[[4](#C_006_c3.xhtml#r3_4)\]. Some of the best-known edge operators will be presented below, either because of their practical application or because they have been historically interesting.

### 3.3.1 Prewitt and Sobel Operators

The Prewitt and Sobel operators represent two of the most used methods in edge detection \[[5](#C_006_c3.xhtml#r3_5)\], which are very similar to each other, differing only by some details.

#### 3.3.1.1 The Filter

Both operators use a 3 × 3 coefficient matrix as a filter. This size and configuration allow the filter to be less prone to its own noise compared to the filters presented in Equations 3.6 and 3.7. The Prewitt operator uses the filter defined by

$H\_{x}^{P} = \\begin{bmatrix} {- 1} & 0 & 1 \\\\ {- 1} & 0 & 1 \\\\ {- 1} & 0 & 1 \\\\ \\end{bmatrix}\\,\\text{y}\\, H\_{y}^{P} = \\begin{bmatrix} {- 1} & {- 1} & {- 1} \\\\ 0 & 0 & 0 \\\\ 1 & 1 & 1 \\\\ \\end{bmatrix}$ (3.8)

These filters are obviously applied to the different neighbors of the pixel in question. If the filters are analyzed in their separate forms, we have the following:

$H\_{x}^{P} = \\begin{bmatrix} 1 \\\\ 1 \\\\ 1 \\\\ \\end{bmatrix}\*\\begin{bmatrix} {- 1} & 0 & {- 1} \\\\ \\end{bmatrix}\\,\\text{o}\\,\\text{bien}\\, H\_{y}^{P} = \\begin{bmatrix} 1 & 1 & 1 \\\\ \\end{bmatrix}\*\\begin{bmatrix} {- 1} \\\\ 0 \\\\ {- 1} \\\\ \\end{bmatrix}$ (3.9)

Each one of the vectors on the right, either in the case of *H*[*x*]^(*P*) or *H*[*y*]^(*P*) produces three columns or rows that constitute the coefficients of the filter defined in equation 3.8. However, as can be seen, this vector $\\begin{bmatrix} {- 1} & 0 & {- 1} \\\\ \\end{bmatrix}$ maintains the derivative approximation defined in [Section 3.2.2](#C_006_c3.xhtml#h3_2_2). It is also possible to notice how the vector on the left $\\begin{bmatrix} 1 & 1 & 1 \\\\ \\end{bmatrix}$ in both cases implies a data smoothing operation, thus showing how, apart from locating or enhancing the pixels belonging to the edges, the filter performs a smoothing operation. This makes the filter more robust to the noise presented in the image.

The Sobel operator has practically an identical filter to the Prewitt operator, with the only difference being that in this filter, greater weight is given to the central row or column of the filter. The coefficient matrix for this operator is defined as follows:

$H\_{x}^{S} = \\begin{bmatrix} {- 1} & 0 & 1 \\\\ {- 2} & 0 & 2 \\\\ {- 1} & 0 & 1 \\\\ \\end{bmatrix}\\,\\text{y}\\, H\_{y}^{S} = \\begin{bmatrix} {- 1} & {- 2} & {- 1} \\\\ 0 & 0 & 0 \\\\ 1 & 2 & 1 \\\\ \\end{bmatrix}$ (3.10)

The results of the Prewitt and Sobel filters produce estimates of the local gradient for all the pixels of the image in their two different directions, maintaining the following relationship:

$\\nabla I\\left( {x,y} \\right) \\approx \\frac{1}{6}\\begin{bmatrix} {H\_{x}^{P} \\cdot I} \\\\ {H\_{y}^{P} \\cdot I} \\\\ \\end{bmatrix}\\quad\\text{y}\\quad\\nabla I\\left( {x,y} \\right) \\approx \\frac{1}{8}\\begin{bmatrix} {H\_{x}^{S} \\cdot I} \\\\ {H\_{y}^{S} \\cdot I} \\\\ \\end{bmatrix}$ (3.11)

#### 3.3.1.2 Gradient Size and Direction

Regardless of if it is a Prewitt or Sobel operator, the results of the filters for each of the different directions will be characterized as follows:

*D*[*x*](*x*,*y*) = *H*[*x*] \* *I* y *D*[*y*](*x*,*y*) = *H*[*y*] \* *I* (3.12)

The magnitude of the edge *E*(*u*,*v*) is, in both cases, defined as the magnitude of the gradient:

$E\\left( {x,y} \\right) = \\sqrt{{(D\_{x}\\left( {x,y} \\right))}^{2} + {(D\_{y}\\left( {x,y} \\right))}^{2}}$ (3.13)

The direction of the gradient at each pixel (the angle) is calculated as follows ([Figure 3.5](#C_006_c3.xhtml#f3_5)):

![FIGURE 3.5 Representation of the magnitude of the gradient E\\left( {x,y} \\right) and its direction \\phi\\left( {x,y} \\right). The complete process for edge detection is again summarized in Figure 3.6. First, the original image is filtered through the two coefficient matrices H\_{x} and H\_{y}, and consequently, their results are gathered in the magnitude of the gradient E\\left( {x,y} \\right) and in the direction of the same \\phi\\left( {x,y} \\right).](images/Fig03_05.jpg)

[**FIGURE 3.5**](#C_006_c3.xhtml#f3_5b) Representation of the magnitude of the gradient *E*(*x*,*y*) and its direction *ϕ*(*x*,*y*). The complete process for edge detection is again summarized in [Figure 3.6](#C_006_c3.xhtml#f3_6). First, the original image is filtered through the two coefficient matrices *H*[*x*] and *H*[*y*], and consequently, their results are gathered in the magnitude of the gradient *E*(*x*,*y*) and in the direction of the same *ϕ*(*x*,*y*).

$\\phi\\left( {x,y} \\right) = \\tan^{- 1}\\left( \\frac{D\_{y}\\left( {x,y} \\right)}{D\_{x}\\left( {x,y} \\right)} \\right)$ (3.14)

The computation of the gradient direction using the Prewitt operator and the original version of the Sobel operator is relatively imprecise. Therefore, it is suggested that instead of using the Sobel filter presented in Equation 3.10, employ the version that minimizes the angle error, defined by:

$H\_{x}^{S^{\\prime}} = \\frac{1}{32}\\begin{bmatrix} {- 3} & 0 & 3 \\\\ {- 10} & 0 & 10 \\\\ {- 3} & 0 & 3 \\\\ \\end{bmatrix}\\,\\text{and}\\, H\_{y}^{S^{\\prime}} = \\frac{1}{32}\\begin{bmatrix} {- 3} & {- 10} & {- 3} \\\\ 0 & 0 & 0 \\\\ 3 & 10 & 3 \\\\ \\end{bmatrix}$ (3.15)

Due to its good results and simple implementation, the Sobel operator is widely used and employed in most commercial software packages used for digital image processing ([Figure 3.6](#C_006_c3.xhtml#f3_6)).

![FIGURE 3.6 Typical operation of filters used for edge detection. With both coefficient matrices Hx and Hy, the gradient images Dx and Dx are produced, and with them the magnitude of the gradient E\\left( {x,y} \\right)\\operatorname{} and \\phi\\left( {x,y} \\right) its direction are also calculated.](images/Fig03_06.jpg)

[**FIGURE 3.6**](#C_006_c3.xhtml#f3_6b) Typical operation of filters used for edge detection. With both coefficient matrices *H[x]* and *H[y]*, the gradient images *D[x]* and *D[x]* are produced, and with them the magnitude of the gradient *E*(*x*,*y*)  and *ϕ*(*x*,*y*) its direction are also calculated.

### 3.3.2 The Roberts Operator

The Roberts operator is one of the oldest filters used for locating edges in an image \[[6](#C_006_c3.xhtml#r3_6)\]. In this section, it will be described. A particularity of this filter is that it is extremely small, using only a 2 × 2 coefficient matrix to determine the gradient in its two different directions along its diagonals. The operator is defined as follows:

$H\_{1}^{R} = \\begin{bmatrix} 0 & \\underset{\\\_}{1} \\\\ {- 1} & 0 \\\\ \\end{bmatrix}\\quad H\_{2}^{R} = \\begin{bmatrix} {- 1} & 0 \\\\ 0 & \\underset{\\\_}{1} \\\\ \\end{bmatrix}$ (3.16)

This filter reacts particularly to the edges of the image that have a diagonal direction ([Figure 3.7](#C_006_c3.xhtml#f3_7)). However, this makes the filter not very selective in the direction of the gradient, mainly when it is calculated on regions with different orientations. The magnitude of the gradient is calculated as defined in Equation 3.5, considering both components *H*[1]^(*R*) and *H*[2]^(*R*). Nevertheless, due to the diagonal operation of the filter on the data, it can be considered that the magnitude of the gradient is formed as the resultant of two vectors (*H*[1]^(*R*) and *H*[2]^(*R*)) that are at 45°. [Figure 3.8](#C_006_c3.xhtml#f3_8) illustrates this operation.

![FIGURE 3.7 Diagonal components of the Roberts operator: (a) component H\_{2}^{R} and (b) component H\_{1}^{R}. From the images, it is easy to recognize the directional character in the calculation of this operator to find the magnitude of the gradient in each pixel of the image.](images/Fig03_07.jpg)

[**FIGURE 3.7**](#C_006_c3.xhtml#f3_7b) Diagonal components of the Roberts operator: (a) component *H*[2]^(*R*) and (b) component *H*[1]^(*R*). From the images, it is easy to recognize the directional character in the calculation of this operator to find the magnitude of the gradient in each pixel of the image.

![FIGURE 3.8 The magnitude of the gradient considering the Roberts operator. The magnitude of the gradient E\\left( {x,y} \\right) is calculated as the sum of the two orthogonal filters H\_{1}^{R} and H\_{2}^{R}, that are applied for each direction of the diagonal.](images/Fig03_08.jpg)

[**FIGURE 3.8**](#C_006_c3.xhtml#f3_8b) The magnitude of the gradient considering the Roberts operator. The magnitude of the gradient *E*(*x*,*y*) is calculated as the sum of the two orthogonal filters *H*[1]^(*R*) and *H*[2]^(*R*), that are applied for each direction of the diagonal.

### 3.3.3 Compass Operators

A problem in the design of filters for edge detection is that the more sensitive the detection of the edge of a structure is preferred, the more dependent it becomes on its direction. Therefore, to design a good operator, it is necessary to make a trade-off between response magnitude and sensitivity to gradient direction.

A solution for this is not to use only two filters that break down the filter action in two directions, either horizontally and vertically in the case of the Prewitt and Sobel operators or diagonally up or down as it is for the Roberts operator, but to use filters for a larger number of directions. A classic example is the Kirsch operator, which consists of eight different filters, each one separated from the other by 45°. Therefore, it covers all directions for efficient edge detection. The coefficient matrices of this operator are defined as follows:

$\\begin{matrix} {H\_{0}^{K} = \\begin{bmatrix} {- 1} & 0 & 1 \\\\ {- 2} & 0 & 2 \\\\ {- 1} & 0 & 1 \\\\ \\end{bmatrix},H\_{1}^{K} = \\begin{bmatrix} {- 2} & {- 1} & 0 \\\\ {- 1} & 0 & 1 \\\\ 0 & 1 & 2 \\\\ \\end{bmatrix},} \\\\ {H\_{2}^{K} = \\begin{bmatrix} {- 1} & {- 2} & {- 1} \\\\ 0 & 0 & 0 \\\\ {- 1} & 0 & 1 \\\\ \\end{bmatrix},H\_{3}^{K} = \\begin{bmatrix} 0 & {- 1} & {- 2} \\\\ 1 & 0 & {- 1} \\\\ 2 & 1 & 0 \\\\ \\end{bmatrix}} \\\\ \\end{matrix}$ (3.17)

From these eight filters *H*[0]^(*K*), *H*[1]^(*K*), ..., *H*[7]^(*K*), only four must be calculated since the last four are equal to the first four except for the sign. For example, *H*[4]^(*K*) =  − *H*[0]^(*K*). Due to the linearity property of convolution, it is clear that

*I* \* *H*[4]^(*K*) = *I* \*  − *H*[0]^(*K*) =  − (*I*\**H*[0]^(*K*)) (3.18)

The images produced by the operation of the Kirsch filters *D*[0], *D*[1], ..., *D*[7]  are generated in the following way:

$\\begin{matrix} {D\_{0} = I\*H\_{0}^{K}\\quad D\_{1} = I\*H\_{1}^{K}\\quad D\_{2} = I\*H\_{2}^{K}\\quad D\_{3} = I\*H\_{3}^{K}} \\\\ {D\_{4} = - D\_{0}\\quad D\_{5} = - D\_{1}\\quad D\_{6} = - D\_{2}\\quad D\_{7} = - D\_{3}} \\\\ \\end{matrix}$ (3.19)

The magnitude of the gradient, which can be conceived as a composition of all the images produced by the Kirsch filters, is calculated in the pixel (*x*,*y*)  as the maximum of the values of the images obtained by the operation of each of the eight filters. So, the value of the magnitude of the gradient for the pixel (*x*,*y*) is defined as follows:

$\\begin{array}{ccl} {E^{K}\\left( {x,y} \\right)} & = & {\\max\\left( {D\_{0}\\left( {x,y} \\right),D\_{1}\\left( {x,y} \\right),...,D\_{7}\\left( {x,y} \\right)} \\right)} \\\\ & = & {\\max\\left( {\\left| {D\_{0}\\left( {x,y} \\right)} \\right|,\\left| {D\_{1}\\left( {x,y} \\right)} \\right|,...,\\left| {D\_{3}\\left( {x,y} \\right)} \\right|} \\right)} \\\\ \\end{array}$ (3.20)

The direction of the gradient is determined by the filter that presents the maximal contribution in the calculation of the magnitude of the gradient. Therefore, the direction of the gradient is specified as follows:

$\\phi^{K}\\left( {x,y} \\right) = \\frac{\\text{π}}{4}l\\,\\text{where}\\, l = \\underset{0 \\leq i \\leq 7}{\\text{argmax}}\\left( {D\_{i}\\left( {x,y} \\right)} \\right)$ (3.21)

### 3.3.4 Edge Detection with MATLAB^®

Considering the previous sections as theoretical foundations, this section presents how we can use MATLAB to calculate the edges of an image. To generate programs that allow finding edges of an image using any of the Sobel, Prewitt, Roberts, or Kirsch operators, it is necessary to divide the program into three parts.

In the first part, it is necessary to generate one image per filter. Normally, there are two images that correspond to the different directions in which the operator is defined (see Equation 3.4). In this part, the filter, which is a matrix of coefficients, is spatially convolved with the original image. The result of this process is the magnitude values of the gradient in the direction defined for each filter. [Figure 3.9](#C_006_c3.xhtml#f3_9) shows this process, considering the Sobel operator.

![FIGURE 3.9 The implementation process for determining the magnitude of the gradient using the Sobel operator.](images/Fig03_09.jpg)

[**FIGURE 3.9**](#C_006_c3.xhtml#f3_9b) The implementation process for determining the magnitude of the gradient using the Sobel operator.

In the second part, the magnitude of the gradient is obtained from the resulting images from the convolution process between the filter (either horizontal or vertical) and the image (see Equation 3.5).

In the third part, a threshold **U** is set that characterizes the value from which the pixel in question is considered to be part of an edge. This value naturally defines the structural properties of the objects. By using this threshold **U**, the image with the gradient magnitudes is binarized. The elements in this image present only ones and zeros. A pixel will be one if it is an edge. Otherwise, it will be zero. [Program 3.1](#C_006_c3.xhtml#p3_1) shows the MATLAB implementation for determining the edges in an image, considering the Sobel operator as the operator.

The results of the code shown in [Program 3.1](#C_006_c3.xhtml#p3_1) are shown in [Figure 3.10](#C_006_c3.xhtml#f3_10), where it is possible to observe the original intensity image, the gradients obtained by the Sobel operator on the *x*\-axis, on the *y*\-axis, as well as the total gradient and the edges.

![FIGURE 3.10 Results of applying the code described in Program 3.1 on an intensity image, (a) original grayscale image, (b) gradient in x, (c) gradient in y, (d) total gradient, and (e) image of borders.](images/Fig03_10.jpg)

[**FIGURE 3.10**](#C_006_c3.xhtml#f3_10b) Results of applying the code described in [Program 3.1](#C_006_c3.xhtml#p3_1) on an intensity image, (a) original grayscale image, (b) gradient in *x*, (c) gradient in *y*, (d) total gradient, and (e) image of borders.

### 3.3.5 MATLAB Functions for Edge Detection

The image processing toolbox provides the function `edge`, which implements the different operators discussed in the previous sections (Sobel, Prewitt, and Roberts) [[7](#C_006_c3.xhtml#r3_7)\]. For some of these operators, it is also possible to specify the direction of the filter to calculate. Therefore, it can be indicated by the sensitivity with which the computation of the gradient in horizontal, vertical, or both directions is performed. The general structure of the function is described as follows:

```
[g,t]=edge(f, ‘method’, parameters)
```

where `f` is the image from which the edges are extracted. `method` corresponds to one of the operators listed in [Table 3.1](#C_006_c3.xhtml#t3_1). `parameters` represent the specifications that must be configured depending on the type of method used. The output `g` is a binary image where the pixels belonging to the detected edges of f have a value of 1. Otherwise, they have a value of zero. The `t` parameter is optional and provides the threshold used by the algorithm to determine which value of the gradient can be considered as an edge.

[**TABLE 3.1**](#C_006_c3.xhtml#t3_1b) Edge Detection Operators Used by the Edge Function of the Image Processing Toolbox.

 
| Operator || ‘method’ || Filters |
| --- | --- | --- |
| `Prewitt` || `‘prewitt’` || $H\_{y}^{P} = \\begin{bmatrix} {- 1} & {- 1} & {- 1} \\\\ 0 & 0 & 0 \\\\ 1 & 1 & 1 \\\\ \\end{bmatrix}\\operatorname{}H\_{y}^{P} = \\begin{bmatrix} {- 1} & {- 1} & {- 1} \\\\ 0 & 0 & 0 \\\\ 1 & 1 & 1 \\\\ \\end{bmatrix}$ |
| --- | --- | --- |
| `Sobel` || `‘sobel’` || $H\_{x}^{S} = \\begin{bmatrix} {- 1} & 0 & 1 \\\\ {- 2} & 0 & 2 \\\\ {- 1} & 0 & 1 \\\\ \\end{bmatrix}\\operatorname{}H\_{y}^{S} = \\begin{bmatrix} {- 1} & {- 2} & {- 1} \\\\ 0 & 0 & 0 \\\\ 1 & 2 & 1 \\\\ \\end{bmatrix}$ |
| `Roberts` || `‘roberts’` || $H\_{1}^{R} = \\begin{bmatrix} 0 & \\overline{1} \\\\ {- 1} & 0 \\\\ \\end{bmatrix}\\operatorname{}H\_{2}^{R} = \\begin{bmatrix} {- 1} & 0 \\\\ 0 & \\overline{1} \\\\ \\end{bmatrix}$ |

#### 3.3.5.1 Sobel Operator

The Sobel operator uses the filters described in [Table 3.1](#C_006_c3.xhtml#t3_1) to approximate the partial derivatives ∂*I*/∂*u* and ∂*I*/∂*v*. From the combination of these partial derivatives according to Equation 3.5, we obtain each pixel (*u*,*v*) the gradient value. Then, a pixel (*u*,*v*) is said to correspond to an edge of the image if the value of its gradient is greater than a pre-established threshold **U** as a criterion.

The general call to the edge detection function that the image processing toolbox implements under the Sobel method is:

```
[g,t]=edge(f, ‘sobel’, U, dir)
```

where `f` is the image from which the edges will be extracted. `U` is a threshold that is used as the criterion to classify the edges. `dir` selects the direction of the gradient, which can be ‘horizontal’ if used *H*[*x*]^(*S*) or ‘*vertical*’ if *H*[*y*]^(*S*)  is used. The option ‘`both`’, which is the default option, implies the calculation of both filters. As a result, the function obtains the image `g,` which, as stated above, contains the detected edges. `g` is a binary image where the edge pixels have the value of 1, while not edge pixels present the value of zero. If the threshold `U` is specified `t` =` U`. If `U` is not specified, the algorithm automatically determines one, uses it for edge detection, and returns its value in `t`.

#### 3.3.5.2 Prewitt Operator

The Prewitt operator uses the coefficient matrices specified in [Table 3.1](#C_006_c3.xhtml#t3_1) for edge detection. The general structure of this function is described as follows:

```
[g,t]=edge(f, ‘prewitt’, U, dir)
```

The parameters of this function are identical to those indicated in the Sobel case. The Prewitt operator is a little simpler (computationally speaking) in its implementation in relation to the Sobel case. Nevertheless, the results obtained are noisier. This is because the Sobel filter performs a smoothing operation on the data, which can be observed in the coefficients with value two in the row or column of the pixel on which the gradient is calculated.

#### 3.3.5.3 Roberts Operator

The Roberts operator uses the filters defined in [Table 3.1](#C_006_c3.xhtml#t3_1) to approximate the gradient magnitude at the pixel (*u*,*v*)). The general structure of this function is described as follows:

```
[g,t]=edge(f, ‘roberts’, U, dir)
```

The parameters of this function are identical to those described in the case of the Sobel operator. The Roberts operator represents one of the oldest methods for calculating the gradient in images. Although this method is the simplest to implement, it has limited functionality since it is non-symmetric. Therefore, it cannot detect edges that are directionally in multiples of 45°. As a comparison, [Figure 3.11](#C_006_c3.xhtml#f3_11) shows the result of applying the previous functions to each of the different operators to detect the edges in an image. In the figure, all the functions use the same threshold for all cases.

![FIGURE 3.11 Comparison of the different operators used for edge detection. (a) Original image, (b) edges detected by the Sobel operator, (c) Prewitt, and (d) Roberts. In all cases, a U = 0.05 has been used.](images/Fig03_11.jpg)

[**FIGURE 3.11**](#C_006_c3.xhtml#f3_11b) Comparison of the different operators used for edge detection. (a) Original image, (b) edges detected by the Sobel operator, (c) Prewitt, and (d) Roberts. In all cases, a U = 0.05 has been used.

## 3.4 Operators Based on the Second Derivative

Previously, the group of operators based on the first derivative has been described in [Section 3.2](#C_006_c3.xhtml#h3_2) as a way of approximating the gradient of the image. In addition to these filters, there are other types of operators that are based on the second derivative of the image function \[[8](#C_006_c3.xhtml#r3_8)\]. In an image, intensity changes can be calculated by the value of the derivative in each direction (maximum gradient) or by the zero crossing of the second derivative (Laplacian) in any direction. As can be seen, the problem of using the first derivative as an approach for edge detection results in its difficult location when representing a highly directional method or when the edge is not well defined.

Although the value of the gradient allows the detection of an edge, it is sometimes important to have information about whether the pixel presents a positive or negative transition of the gradient. This is equivalent to knowing if the pixel is on the dark or light side of the edge.

### 3.4.1 Edge Detection Using the Second-Derivative Technique

This technique is based on finding what is called zero-crossing. A zero crossing is nothing more than the transition from positive to negative or vice versa and is estimated from the second derivative.

The definition of a derivative for a one-dimensional function is as follows:

$\\frac{\\partial f}{\\partial x} = f\\left( {x + 1} \\right) - f\\left( x \\right)$ (3.22)

Likewise, from Equation 3.22, it can be said that the second derivative is defined as:

$\\frac{\\partial f^{2}}{\\partial x^{2}} = f\\left( {x + 1} \\right) - 2f\\left( x \\right) + f\\left( {x - 1} \\right)$ (3.23)

The detection of edges by means of the second derivative is based on the zero crossing of the value of the gradient in any direction. To produce this effect, we use the Laplacian, which is insensitive to rotation and isotropic.

$\\nabla^{2}I\\left( {x,y} \\right) = \\frac{\\partial^{2}I\\left( {x,y} \\right)}{\\partial x^{2}} + \\frac{\\partial^{2}I\\left( {x,y} \\right)}{\\partial y^{2}}$ (3.24)

This filter uses second derivatives. Considering Equation 3.23 in expression 3.24 of the Laplacian, we have:

$\\frac{\\partial^{2}I\\left( {x,y} \\right)}{\\partial x^{2}} = I\\left( {x + 1,y} \\right) - 2I\\left( {x,y} \\right) + I\\left( {x - 1,y} \\right)$ (3.25)

$\\frac{\\partial^{2}I\\left( {x,y} \\right)}{\\partial y^{2}} = I\\left( {x,y + 1} \\right) - 2I\\left( {x,y} \\right) + I\\left( {x,y - 1} \\right)$ (3.26)

Therefore, if the expressions 3.25 and 3.26 are replaced in 3.24, we have:

$\\begin{array}{ccl} {\\nabla^{2}I\\left( {x,y} \\right)} & = & {I\\left( {x + 1,y} \\right) + I\\left( {x - 1,y} \\right)} \\\\ & + & {I\\left( {x,y + 1} \\right) + I\\left( {x,y - 1} \\right) - 4I\\left( {x,y} \\right)} \\\\ \\end{array}$ (3.27)

If the previous equation is expressed in terms of a filter, the matrix coefficients are defined as those shown in [Figure 3.12](#C_006_c3.xhtml#f3_12).

![FIGURE 3.12 Filter that represents the calculation of the Laplacian on an image, obtained from Equation 3.23](images/Fig03_12.jpg)

[**FIGURE 3.12**](#C_006_c3.xhtml#f3_12b) Filter that represents the calculation of the Laplacian on an image, obtained from Equation 3.23

An example of the application of the Laplacian filter on a grayscale image is shown in [Figure 3.14](#C_006_c3.xhtml#f3_14). It presents the different effects of applying the double derivative in each of the directions and, finally, the result of the sum of the two, as the Laplacian is defined. The equation defined in 3.27 and expressed in the form of a filter in [Figure 3.12](#C_006_c3.xhtml#f3_12) does not consider the variations in the diagonal neighbors of the pixel in question, which can be incorporated into the filter, with the consideration that by doing this, we will increase the number of ones by 4 contained in the filter. Therefore, the central coefficient will have to be increased to 8. Considering the above, the Laplacian filter would be defined as described in [Figure 3.13](#C_006_c3.xhtml#f3_13).

![FIGURE 3.13 Laplacian filter with the extension of the diagonal neighbors to the central pixel](images/Fig03_13.jpg)

[**FIGURE 3.13**](#C_006_c3.xhtml#f3_13b) Laplacian filter with the extension of the diagonal neighbors to the central pixel

As can be seen from the calculation of the Laplacian filters, they have a response of zero in uniform grayscale regions and different for regions with varying grayscales. This is since these types of filters behave like high-pass filters. The sum of the coefficients is always zero ([Figure 3.14](#C_006_c3.xhtml#f3_14)).

![FIGURE 3.14 Use of the Laplacian filter. (a) Original figure, (b) horizontal second-order partial derivative \\partial^{2}I\\left( {x,y} \\right)\\text{/}\\partial x^{2}, (c) vertical second-order partial derivative \\partial^{2}I\\left( {x,y} \\right)/\\partial y^{2}, and (d) the Laplacian operator \\nabla^{2}I\\left( {x,y} \\right)](images/Fig03_14.jpg)

[**FIGURE 3.14**](#C_006_c3.xhtml#f3_14b) Use of the Laplacian filter. (a) Original figure, (b) horizontal second-order partial derivative ∂²*I*(*x*,*y*)/∂*x*², (c) vertical second-order partial derivative ∂²*I*(*x*,*y*)/∂*y*², and (d) the Laplacian operator ∇²*I*(*x*,*y*)

### 3.4.2 Sharpness Enhancement in Images

If the Laplacian operator is applied to an image, we will obtain its edges. However, if what is desired is to improve the sharpness of an image, then it will be necessary to preserve the low-frequency information of the original image and emphasize the details present in the image through the Laplacian filter. To achieve this effect, it is necessary to subtract from the original image a scaled version of the Laplacian filter value. So, the image with improved sharpness would be defined as described in the following equation:

*I*(*x*, *y*)[Enhanced] = *I*(*x*,*y*) − *w* ⋅ ∇²*I*(*x*,*y*) (3.28)

[Figure 3.15](#C_006_c3.xhtml#f3_15) shows the concept by which the image improves its sharpness by making the presence of its edges more prominent. To facilitate the explanation, the figure considers only the one-dimensional case.

![FIGURE 3.15 Sharpening by applying the second derivative. By subtracting a factor from the second derivative of the function, it is possible to maximize the presence of the borders in the image.](images/Fig03_15.jpg)

[**FIGURE 3.15**](#C_006_c3.xhtml#f3_15b) Sharpening by applying the second derivative. By subtracting a factor from the second derivative of the function, it is possible to maximize the presence of the borders in the image.

The effect of improving the sharpness of an image can be carried out in a single execution. Considering *w* = 1, the model of enhancement can be defined as follows:

*I*(*x*, *y*)[En] = *I*(*x*,*y*) − (1) ⋅ ∇²*I*(*x*,*y*) (3.29)

If it is replaced by the Laplacian from Equation 3.29 with the expression of Equation 3.27, the enhancement model is modeled as follows:

$\\begin{array}{ccl} {I\\left( x,y)\_{\\mathit{En}} \\right.} & = & {5I\\left( x,y \\right) - \\left\\lbrack I\\left( x + 1,y \\right) + I\\left( x - 1,y \\right) \\right\\rbrack} \\\\ & + & {I\\left( x,y + 1 \\right) + I\\left( x,y - 1 \\right)} \\\\ \\end{array}$ (3.30)

If Equation 3.30 is presented in the form of a filter, the coefficient matrix is defined as follows:

$I{(x,y)}\_{Enhanced} = \\begin{bmatrix} 0 & {- 1} & 0 \\\\ {- 1} & 5 & {- 1} \\\\ 0 & {- 1} & 0 \\\\ \\end{bmatrix}$ (3.31)

[Figure 3.16](#C_006_c3.xhtml#f3_16) presents the result of applying this filter to an image.

![FIGURE 3.16 Application of the Laplacian filter to improve the sharpness of an image. (a) Original image and (b) the image resulting from applying I{(x,y)}\_{\\text{Enhanced}} = I\\left( {x,y} \\right) - w \\cdot \\nabla^{2}I\\left( {x,y} \\right), considering w = 1.](images/Fig03_16.jpg)

[**FIGURE 3.16**](#C_006_c3.xhtml#f3_16b) Application of the Laplacian filter to improve the sharpness of an image. (a) Original image and (b) the image resulting from applying *I*(*x*, *y*)[Enhanced] = *I*(*x*,*y*) − *w* ⋅ ∇²*I*(*x*,*y*), considering *w* = 1.

### 3.4.3 Use of MATLAB for the Implementation of the Laplacian Filter and the Enhancement of Sharpness

In this section, the use of MATLAB to improve the sharpness of images is described. In this process, it is also necessary to calculate the Laplacian. The MATLAB code to improve the sharpness of an image can be divided into two simple steps. In the first step, the Laplacian filter is calculated from the filter described in [Figure 3.12](#C_006_c3.xhtml#f3_12). In the second step, the image sharpness is generated considering the information of low frequency contained in the original image minus the value of the Laplacian (see Equation 3.28), which incorporates the information that allows the enhancement of the details of the image. [Program 3.2](#C_006_c3.xhtml#p3_2) shows the coding in MATLAB to improve the sharpness of an image using the Laplacian.

The results of applying the code presented in [Program 3.2](#C_006_c3.xhtml#p3_2) are shown in [Figure 3.17](#C_006_c3.xhtml#f3_17). In this figure, it can be seen the difference between the original grayscale image and the image with contrast enhancement for *w* = 1.

![FIGURE 3.17 Results of applying the code of Program 3.2 to improve the sharpness of an image through the application of the Laplacian operator with MATLAB®, (a) original grayscale image, and (b) image with improved contrast for w = 1.](images/Fig03_17.jpg)

[**FIGURE 3.17**](#C_006_c3.xhtml#f3_17b) Results of applying the code of [Program 3.2](#C_006_c3.xhtml#p3_2) to improve the sharpness of an image through the application of the Laplacian operator with MATLAB^®, (a) original grayscale image, and (b) image with improved contrast for *w* = 1.

### 3.4.4 The Canny Filter

A well-known method for detecting edges in images is the Canny filter \[[2](#C_006_c3.xhtml#r3_2)\]. This method is based on the application of a series of filters in different directions and resolutions, which are finally combined into a single result. The method aims to achieve three different objectives: (a) to minimize the number of false edges, (b) to improve the location of edges in the image, and (c) to deliver an image whose edge width is only one pixel. The Canny filter is essentially a filter based on gradient methods, but, however, it also uses the second derivative, or Laplacian, as a criterion for edge location. Most of the time, this algorithm is used in its simple form, that is, setting only the smoothing parameter *σ*. [Figure 3.18](#C_006_c3.xhtml#f3_18) shows examples of the application of this algorithm using different values of the parameter *σ*.

![FIGURE 3.18 Canny’s algorithm applied to an image. (a) Original image, (b) image edges with \\sigma = 2, (c) image edges with \\sigma = 4, and (d) image edges with \\sigma = 6.](images/Fig03_18.jpg)

[**FIGURE 3.18**](#C_006_c3.xhtml#f3_18b) Canny’s algorithm applied to an image. (a) Original image, (b) image edges with *σ* = 2, (c) image edges with *σ* = 4, and (d) image edges with *σ* = 6.

### 3.4.5 MATLAB Tools that Implement the Canny Filter

Due to the wide use of the Canny filter as a previous stage in the segmentation and classification of objects and its robustness in determining edges, the filter is normally implemented in most commercial libraries and digital image processing tools. In MATLAB, the Canny algorithm can be calculated using the `edge` function. Its general structure is described as follows:

```
BW = edge(I, ‘canny’, U, sigma);
```

where `BW` is the image with the edges extracted, considering the Canny algorithm. `I` is the grayscale image from which the edges will be extracted. `U` is the threshold value from which the pixels are classified as edges. `sigma` represents the smoothing parameter (*σ*) that has the effect of minimizing the number of false edges.

## References

1.  [Gose](#C_006_c3.xhtml#r3_1b), E., Johnsonbaugh, R., & Jost, S. (2017). Pattern recognition and image analysis. CRC Press.
2.  [Canny](#C_006_c3.xhtml#r3_2b), J. (1986). A computational approach to edge detection. IEEE Transactions on Pattern Analysis and Machine Intelligence, 8(6), 679–698. [https://ieeexplore.ieee.org/document/4767851](https://ieeexplore.ieee.org/)
3.  [Bina](#C_006_c3.xhtml#r3_3b), S., & Ghassemian, H. (2019). A Comprehensive Review of Edge Detection Techniques for Images in Computer Vision. Journal of Computer and Communications, 7(1), 36–49. [https://doi.org/10.14257/ijmue.2017.12.11.01](https://doi.org/10.14257/ijmue.2017.12.11.01)
4.  [Hussain](#C_006_c3.xhtml#r3_4b), S., & Hussain, M. (2014). A Review of Edge Detection Techniques in Digital Image Processing. International Journal of Scientific and Engineering Research, 5(2), 222–231. [https://www.researchgate.net/journal/International-Journal-of-Science-and-Research-IJSR-2319-7064](https://www.researchgate.net/)
5.  [Singh](#C_006_c3.xhtml#r3_5b), S., & Bhatnagar, G. (2015). Comparative Analysis of Edge Detection Techniques for Digital Images. Journal of Information Technology and Computer Science, 7(1), 31–40. [https://doi.org/10.1109/ICCCIS51004.2021.9397225](https://doi.org/10.1109/ICCCIS51004.2021.9397225)
6.  [Abdullah-Al-Wadud](#C_006_c3.xhtml#r3_6b), M., Islam, M. A., & Islam, M. M. (2017). A Review of Image Edge Detection Techniques and Algorithms. Journal of Electromagnetic Analysis and Applications, 9(10), 240–251. [https://doi.org/10.1007/s11633-018-1117-z](https://doi.org/10.1007/s11633-018-1117-z)
7.  [Solomon](#C_006_c3.xhtml#r3_7b), C., & Breckon, T. (2010). Fundamentals of Digital Image Processing: A Practical Approach with Examples in MATLAB. Wiley.
8.  [Tariq](#C_006_c3.xhtml#r3_8b), M. A., Raza, A., & Abbas, M. (2019). A Comparative Study of Edge Detection Techniques in Digital Image Processing. IEEE Access, 7, 40793–40807. [https://doi.org/10.46565/jreas.2021.v06i04.001](https://doi.org/10.46565/jreas.2021.v06i04.001)

# 4 Segmentation and Processing of Binary Images

DOI: [10.1201/9781003287414-4](https://doi.org/10.1201/9781003287414-4)

## 4.1 Introduction

Image segmentation is considered an active field of research in the area of computer vision with an innumerable number of applications \[[1](#C_007_c4.xhtml#r4_1)\]. The purpose of segmentation is to divide an image into regions that, according to some context, have some relationship or meaning. Various methods and approaches have been proposed in the literature for this purpose. The choice of a particular method depends on the characteristics of the application. The segmentation must be considered as a previous step for the description, recognition, or classification of objects contained in an image \[[2](#C_007_c4.xhtml#r4_2)\]. This chapter will analyze the most popular segmentation methods and their implementation.

The binary images produced as a result of the segmentation process are images whose pixels only have one value out of two possible ones, or zero \[[3](#C_007_c4.xhtml#r4_3)\]. Normally, this pixel classification corresponds to the object (values set to one) and the background (values set to zero), although obviously, such differentiation in real images is not always possible. In this chapter, the structure of binary images will also be analyzed, considering how to isolate each of the objects present in the image and how to describe them structurally. As a simple definition, an object will be defined as a group of pixels that are connected by some kind of neighborhood while its surroundings are bordered by pixels of value zero (the background).

## 4.2 Segmentation

Segmentation is defined as the process of dividing the image into different regions so that the pixels in each region are similar (according to certain criteria) while they are different between the regions \[[4](#C_007_c4.xhtml#r4_4)\]. The objective is to distinguish between objects of interest and the rest of the image. In the simplest case, the segmentation is conducted by considering only two classes. The first class considers the object of interest, while the second class corresponds to the rest of the image, commonly known as the background. This process is also called binarization \[[5](#C_007_c4.xhtml#r4_5)\].

The most commonly used criterion in segmentation is the homogeneity of grayscale regions, although for more advanced applications, color or texture can also be used. Segmentation is often the first step in a pattern recognition system. Its function is to isolate the objects of interest for later classification \[[6](#C_007_c4.xhtml#r4_6)\].

There are many approaches to image segmentation, which can be divided according to the characteristics considered and the type of algorithm used. According to the characteristics, the segmentation methods include the intensity values of the pixels, the texture, or the magnitude of the gradient. Regarding the type of algorithm, segmentation techniques can be divided into contextual and non-contextual \[[7](#C_007_c4.xhtml#r4_7)\].

Non-contextual techniques ignore the relationship between pixels and the object they are trying to isolate. In this way, the pixels are grouped considering some global characteristics of them, such as intensity level. Among the main techniques of this category is thresholding. In thresholding, each pixel is assigned to a particular category based on its intensity level, depending on whether it exceeds a predetermined level known as a threshold.

Contextual techniques, different from non-contextual methods, additionally exploit the relationship between the pixel and the object to be isolated by incorporating homogeneity measures or criteria. In this way, a contextual method could group a set of pixels that have similar intensity and that, at the same time, are close to each other or that maintain the same direction according to their gradient value.

## 4.3 Threshold

Thresholding is a segmentation technique that assumes that objects are integrated by pixels of homogeneous intensity. In this way, each pixel is compared with a pre-fixed threshold; if the pixel intensity value is higher, the pixel is considered to belong to a certain category, but if it is lower, it will correspond to another category. Under these circumstances, the quality of the segmentation will depend on the choice of the appropriate threshold value \[[8](#C_007_c4.xhtml#r4_8)\].

In the ideal case of thresholding, the histogram that reflects the pixel distribution of the objects present in the image does not overlap, so a certain threshold value can divide both objects. [Figure 4.1a](#C_007_c4.xhtml#f4_1) shows an image containing two different square objects: A and B. Object A involves pixels with an intensity from a Gaussian distribution with a mean of 60 and a standard deviation of 10. Object B has pixels from a Gaussian distribution with a mean of 190 and a standard deviation of 10. [Figure 4.1b](#C_007_c4.xhtml#f4_1) shows the corresponding histogram of image 4.1a.

![FIGURE 4.1 Distribution of the intensities of the pixels that integrate two different objects in an image. (a) The two objects and (b) their distribution in the histogram.](images/Fig04_01.jpg)

[**FIGURE 4.1**](#C_007_c4.xhtml#f4_1b) Distribution of the intensities of the pixels that integrate two different objects in an image. (a) The two objects and (b) their distribution in the histogram.

From [Figure 4.1](#C_007_c4.xhtml#f4_1), both objects can be clearly segmented if a threshold of 128 is applied. Therefore, if the intensity of a certain pixel is greater than 128, this pixel belongs to object B. Otherwise, it is considered to belong to object A. [Figure 4.2](#C_007_c4.xhtml#f4_2) shows the result of this binarization.

![FIGURE 4.2 The result of the segmentation of Figure 4.1(a) considering the value of 128 as the threshold.](images/Fig04_02.jpg)

[**FIGURE 4.2**](#C_007_c4.xhtml#f4_2b) The result of the segmentation of [Figure 4.1(a)](#C_007_c4.xhtml#f4_1) considering the value of 128 as the threshold.

In most cases, the distribution of the pixels does not maintain a division as clear as the one shown in [Figure 4.1](#C_007_c4.xhtml#f4_1). On the contrary, the distributions tend to have overlapping regions. Indeed, the magnitude of this overlapping determines the difficulty of the segmentation since the greater the extent, the more difficult it is to determine which pixels belong to one or another distribution. [Figure 4.3](#C_007_c4.xhtml#f4_3) shows an example of this case.

![FIGURE 4.3 Objects that overlap their distributions. (a) The two objects and (b) their distribution in the histogram.](images/Fig04_03.jpg)

[**FIGURE 4.3**](#C_007_c4.xhtml#f4_3b) Objects that overlap their distributions. (a) The two objects and (b) their distribution in the histogram.

In cases of overlapping in the distributions, it is not possible to find a threshold that satisfies a correct segmentation since the belonging of the pixels in the overlap is not clear. To illustrate such an effect on segmentation, the image presented in [Figure 4.3](#C_007_c4.xhtml#f4_3) is binarized, considering the threshold of 150, which approximately represents a division between the two modes produced by the distributions. The result of the binarization is shown in [Figure 4.4](#C_007_c4.xhtml#f4_4). In the result, several pixels can be seen that could not be properly classified due to the existing overlap between the distributions of both objects.

![FIGURE 4.4 The result of the segmentation of Figure 4.3(a) considering the value of 128 as the threshold.](images/Fig04_04.jpg)

[**FIGURE 4.4**](#C_007_c4.xhtml#f4_4b) The result of the segmentation of [Figure 4.3(a)](#C_007_c4.xhtml#f4_3) considering the value of 128 as the threshold.

The uncertainty caused by the overlapping of the distributions represents the cause of the poor results in the segmentation. An auxiliary technique for eliminating the overlap between distributions is the application of the median filter to the original image as a pre-processing method. [Figure 4.5](#C_007_c4.xhtml#f4_5) shows the image that results from the application of the median filter (applied in image 4.3a) and the separation effect on its final histogram. In the processing, a 3 × 3 neighborhood was used.

![FIGURE 4.5 Effect of using the median filter on overlapped distributions. (a) The original image, (b) the image obtained by the median filter, and (c) the resulting distribution.](images/Fig04_05.jpg)

[**FIGURE 4.5**](#C_007_c4.xhtml#f4_5b) Effect of using the median filter on overlapped distributions. (a) The original image, (b) the image obtained by the median filter, and (c) the resulting distribution.

As a result of the application of the median filter, the overlapping of the distributions is eliminated in such a way that, by choosing an appropriate threshold, a perfect binarization of the image is obtained. [Figure 4.6](#C_007_c4.xhtml#f4_6) shows the result of the binarization.

![FIGURE 4.6 Result of the segmentation of Figure 4.b (a) considering the value of 145 as the threshold.](images/Fig04_06.jpg)

[**FIGURE 4.6**](#C_007_c4.xhtml#f4_6b) Result of the segmentation of Figure 4.b (a) considering the value of 145 as the threshold.

## 4.4 The Optimal Threshold

The use of the median filter does not always allow the elimination of the overlapping between two densities present in the histogram. In such circumstances, the optimal threshold must be calculated, which produces the least number of misclassified pixels. This is the set of pixels belonging to object A that are classified as if they belonged to object B and vice versa. In this way, the optimal threshold corresponds to the intercept between both distributions. [Figure 4.7](#C_007_c4.xhtml#f4_7) graphically shows the optimal threshold for a hypothetical example of distribution. The figure shows the distributions of two objects A and B that present an overlapping region T. From the figure; the intersection point clearly represents the best location to define the classification limit for each of the classes represented by their respective distributions.

![FIGURE 4.7 The optimal threshold for the binarization of two objects according to the overlapping of their distributions.](images/Fig04_07.jpg)

[**FIGURE 4.7**](#C_007_c4.xhtml#f4_7b) The optimal threshold for the binarization of two objects according to the overlapping of their distributions.

There are several approaches for determining the optimal threshold in the case of the overlapping of two distributions. Most of them operate iteratively, testing a certain threshold in such a way that the pixels of each object are closer to the average value of their respective intensities than to the average intensity value of the opposite object.

## 4.5 Otsu Algorithm

The Otsu method is the most popular method for calculating the optimal threshold. The method allows the binarization of two classes using the histogram of image intensities. The method considers an image *I* of dimension *M* × *N* with *L* − 1 gray scales. The histogram presents two overlapping areas from the distribution. The first corresponds to object A, which involves the intensity values from 0 to *k*, while the second integrates the gray levels from *k* + 1 to *L* − 1. [Figure 4.8](#C_007_c4.xhtml#f4_8) illustrates the distribution and its associated variables.

![FIGURE 4.8 Segmentation process of two distributions using the Otsu method.](images/Fig04_08.jpg)

[**FIGURE 4.8**](#C_007_c4.xhtml#f4_8b) Segmentation process of two distributions using the Otsu method.

The Otsu method starts by calculating the probabilities of each object or class:

$\\begin{matrix} {P\\left( A \\right) = {\\sum\\limits\_{i = 0}^{k}{h\\left( i \\right) = w\_{A}\\left( k \\right) = w\\left( k \\right)}}} \\\\ {P\\left( B \\right) = {\\sum\\limits\_{i = k + 1}^{L - 1}{h\\left( i \\right) = w\_{B}\\left( k \\right) = 1 - w\\left( k \\right)}}} \\\\ \\end{matrix}$ (4.1)

where *h*(*i*) represents the number of pixels of intensity *i* contained in the image. Under these conditions, the average intensity of each object can be calculated as follows:

$\\begin{matrix} {\\mu\_{A}\\left( k \\right) = \\frac{1}{w\_{A}\\left( k \\right)}{\\sum\\limits\_{i = 0}^{k}{i \\cdot h\\left( i \\right)}}} \\\\ {\\mu\_{B}\\left( k \\right) = \\frac{1}{w\_{B}\\left( k \\right)}{\\sum\\limits\_{i = k + 1}^{L - 1}{i \\cdot h\\left( i \\right)}}} \\\\ \\end{matrix}$ (4.2)

From these values, the variances can be obtained as follows:

$\\begin{matrix} {\\sigma\_{A}^{2}\\left( k \\right) = \\frac{1}{w\_{A}\\left( k \\right)}{\\sum\\limits\_{i = 0}^{k}\\left( {i - \\mu\_{A}\\left( k \\right)^{2} \\cdot h\\left( i \\right)} \\right)}} \\\\ {\\sigma\_{B}^{2}\\left( k \\right) = \\frac{1}{w\_{B}\\left( k \\right)}{\\sum\\limits\_{i = k + 1}^{L - 1}\\left( {i - \\mu\_{B}\\left( k \\right)^{2} \\cdot h\\left( i \\right)} \\right)}} \\\\ \\end{matrix}$ (4.3)

Under these circumstances, the variance within classes can be defined in terms of their variances according to the following expression:

*σ*[*D*]² = *w*[*A*](*k*) ⋅ *σ*[*A*]²(*k*) + *w*[*B*](*k*) ⋅ *σ*[*B*]²(*k*) (4.4)

Considering this formulation, the Otsu method searches for the optimal threshold that represents the intensity level *k*, which minimizes the variance within the classes (Equation 4.4). Therefore, the objective is to determine the variance value of each object so small that it can minimize their overlap. With the models defined so far, an algorithm could attempt all the possible values of *k* and return the element for which the value of *σ*[*D*]² is minimum. However, it is possible to develop a recursive formulation that implies faster computation. This requires calculating several terms, such as the total variance and the variance between objects or classes.

The total variance of the distribution calculates the variance of the entire histogram. Thus, its calculation is defined as follows:

$\\sigma\_{T}^{2} = {\\sum\\limits\_{i = 0}^{L - 1}{\\left( {i - \\mu\_{T}} \\right)^{2} \\cdot h\\left( i \\right)}}$ (4.5)

where *μ*[*T*] represents the average intensity of the histogram that represents the distribution:

$\\mu\_{T} = {\\sum\\limits\_{i = 0}^{L - 1}{i \\cdot h\\left( i \\right)}}$ (4.6)

Finally, the variance between classes *σ*[*E*]² can be considered as the subtraction between the total variance *σ*[*T*]² and the variance within the classes or objects *σ*[*T*]². Therefore, *σ*[*E*]² is defined by the following expression:

$\\begin{array}{ccl} \\sigma\_{E}^{2} & = & {\\sigma\_{T}^{2} - \\sigma\_{D}^{2}} \\\\ & = & {{{w\\left( k \\right)} \\cdot \\left( {{\\mu\_{A}\\left( k \\right)} - \\mu\_{T}} \\right)^{2}} - {\\left( {1 - {w\\left( k \\right)}} \\right) \\cdot \\left( {{\\mu\_{B}\\left( k \\right)} - \\mu\_{T}} \\right)}} \\\\ & = & {{w\\left( k \\right)} \\cdot \\left( {1 - {w\\left( k \\right)}} \\right) \\cdot \\left( {{\\mu\_{A}\\left( k \\right)} - {\\mu\_{B}\\left( k \\right)}} \\right)^{2}} \\\\ \\end{array}$ (4.7)

Since the total variance is always constant and independent of the intensity level *k*, the effect of calculating the optimal threshold depends on only the variances *σ*[*E*]² and *σ*[*D*]². Therefore, minimizing the variance within the classes *σ*[*D*]² is equivalent to maximizing the variance between the classes *σ*[*E*]². The advantage of maximizing *σ*[*E*]² is that it can be computed recursively as the values of *k* are iterated. Under such conditions, the equations for this recursion are defined below, considering that their initial values are *w*(1) = *h*(1) and *μ*[*A*](0) = 0.

$\\begin{matrix} {w\\left( {k + 1} \\right) = w\\left( k \\right) + h\\left( {k + 1} \\right)} \\\\ {\\mu\_{A}\\left( {k + 1} \\right) = \\frac{\\left( {w\\left( k \\right) \\cdot \\mu\_{A}\\left( k \\right) + \\left( {k + 1} \\right) \\cdot h\\left( {k + 1} \\right)} \\right)}{w\\left( {k + 1} \\right)}} \\\\ {\\mu\_{B}\\left( {k + 1} \\right) = \\frac{\\left( {\\mu\_{T} - w\\left( {k + 1} \\right) \\cdot \\mu\_{A}\\left( {k + 1} \\right)} \\right)}{1 - w\\left( {k + 1} \\right)}} \\\\ \\end{matrix}$ (4.8)

By using these expressions, it is possible to update *σ*[*E*]² and test if its value is the maximum as the intensity level *k* increases progressively. This simple optimization method can be used without problems because the function *σ*[*E*]² is always smooth and unimodal. [Program 4.1](#C_007_c4.xhtml#p4_1) shows the implementation of the Otsu method. In the program, a color image is first transformed into a grayscale image. Then the Otsu method is implemented according to the steps shown in Equations 4.1–4.8. [Figure 4.9](#C_007_c4.xhtml#f4_9) shows the original image and the binarization result obtained by [Program 4.1](#C_007_c4.xhtml#p4_1).

![FIGURE 4.9 Results of the Otsu method for binarization produced by Program 4.1. (a) Original image and (b) result image.](images/Fig04_09.jpg)

[**FIGURE 4.9**](#C_007_c4.xhtml#f4_9b) Results of the Otsu method for binarization produced by [Program 4.1](#C_007_c4.xhtml#p4_1). (a) Original image and (b) result image.

## 4.6 Segmentation by Region Growth

The region growth method is a segmentation algorithm based on the successive integration of pixels that are related according to a similarity criterion.

Using this approach, a pixel in the image must be chosen as the starting point. Then, its neighboring pixels are analyzed to check if any of them are similar to it. If it is similar, the pixel is included as part of the segmented region. Otherwise, it will not be considered.

Thus, the first step in the region growth method is to select an initial pixel or seed pixel **s**(x,y). Its selection is important since it must be contained in the region in which it is intended to segment. From the selection of this pixel, a local search is made around **s**(x,y) to find a pixel with similar characteristics. The similarity criteria are very diverse, and these could include texture, color, etc. The most common is intensity. Therefore, if the neighboring pixel is similar, it is included as part of the segmented region; otherwise, it is registered in a list ***L*** to subsequently consider such elements in the search for other pixels. Next, the region growth algorithm will be described step by step in order to describe the complete computational process.

### 4.6.1 Initial Pixel

The initial pixel or seed pixel **s**(x,y) must be chosen in such a way that it is within the region on which it is desired to segment. However, if additional information is considered, such as its position, this situation could speed up the segmentation process. An easy way to select it is through an interactive method. Under this approach, the point is selected directly from the image. For this purpose, MATLAB^® implements the function `getpts`. This function has the following format:

```
[y,x]=getpts();
```

where x and y represent the coordinates selected interactively with the mouse; notice how the coordinates are inverted. This is because the information is delivered in a matrix, first the row (coordinate y) and then the column (coordinate x). It is important before using the `getpts` function to display the image using `imshow`. In this way, the current graphics identifier, as provided by `imshow`, can be utilized by `getpts`. Another issue of importance represents the fact that the `getpts` function returns the values of the coordinates of the graphic object provided by the image displayed using `imshow`. For this reason, values are frequently obtained with decimal numbers, which are not appropriate to serve as indices in the selection of a matrix element. Therefore, it is necessary to truncate or cast the content of the variable to an integer type.

### 4.6.2 Local Search

Once the initial pixel **s**(x,y) is selected, the method performs a local search around it, checking similar pixels recursively. Therefore, the search process is carried out in neighborhood **V** around the four closest neighbors. Once a pixel has been found within the neighborhood with similar characteristics to the initial pixel, it replaces the role of the seed pixel, and the local search process is repeated.

The best way to implement a 4-element search neighborhood is to define an array of the form **V** = \[‒1 0; 1 0; 0 ‒1; 0 1\]. Each line expresses a particular neighbor element, while the columns indicate the displacements in the direction of horizontal (*Δ**x*) and vertical (*Δ**y*). [Figure 4.10](#C_007_c4.xhtml#f4_10) illustrates the correspondence process between Matrix **V** and the neighborhood.

![FIGURE 4.10 Correspondence process between Matrix V and the neighborhood.](images/Fig04_10.jpg)

[**FIGURE 4.10**](#C_007_c4.xhtml#f4_10b) Correspondence process between Matrix **V** and the neighborhood.

Within the search process, two important problems arise: pixels outside the image field and the search direction. The first problem occurs mainly when the search is carried out within the limits of the image, and due to the displacements, the selected pixel does not exist within the image. This situation is solved by adding a condition to the code that allows evaluating if the selected pixel exists within the limits defined for the image.

The second problem appears when, in the local search, the displacement of the pixels takes a certain direction; however, in the opposite direction, there are pixels that, according to the similarity measure, correspond to the region to be seeded. Under these conditions, the search process should be able to modify the direction when searching in a determined direction has already been exhausted. To solve this, a list ***L*** is implemented to store the unselected pixels. The position of the pixel and its intensity are recorded in the list. Therefore, the list is used in the comparison. So, when a new pixel **pn** has been found locally, its intensity is compared with the elements contained in the list ***L***. From this comparison, it could happen that a distant pixel **pd** is similar to **pn**, which would imply that pixels with similar characteristics have already been exhausted in the vicinity of **pn**. Under such conditions, a change of direction is necessary. Each time a pixel with similar characteristics is found within the local search process, the information of this pixel is extracted from the list. This action determines that the pixel information is already part of the segmented region **R**. [Figure 4.11](#C_007_c4.xhtml#f4_11) shows the store process of the list ***L*** for an image. In the image, it can be seen how the search that begins in the seed pixel **s(x,y)** has followed the direction marked by the arrow, when pixels with the characteristics to be segmented are also found in opposite directions.

![FIGURE 4.11 Store process of list L for an image.](images/Fig04_11.jpg)

[**FIGURE 4.11**](#C_007_c4.xhtml#f4_11b) Store process of list **L** for an image.

In order to check if a pixel is similar to another, considering the intensity as a similarity criterion (as is the common case), two parameters are important for the region-growing segmentation method: (A) the maximum permissible dissimilarity and (B) the similarity of the segmented region.

The maximum permissible dissimilarity (**Mp**) represents the maximum possible difference between two pixels that is considered similar. This element is considered a configuration parameter. Therefore, the searching process will be executed until the difference between the members of the list **L** and the new pixel **pn** is higher than **Mp**.

The segmented region similarity (**Srs**) defines the average intensity of the region to be segmented. This parameter allows for more robust segmentations since its value is iteratively updated each time a new pixel is found within the segmented region R. The **Srs** parameter is calculated considering the following model:

${\\mathbf{S}\\mathbf{r}\\mathbf{s}\\left( {k + 1} \\right)} = \\frac{{\\mathbf{S}\\mathbf{r}{{\\mathbf{s}\\left( k \\right)} \\cdot \\left| \\mathbf{R} \\right|}} + {I\\left( {\\mathbf{p}\\mathbf{n}} \\right)}}{\\left| \\mathbf{R} \\right| + 1}$ (4.9)

where the value of **S****r****s**(*k*+1) represents the updated value of **S****r****s**(*k*), while |**R**| corresponds to the number of elements currently part of the segmented region. Finally, *I*(**p****n**) defines the intensity of the new pixel **pn**.

[Program 4.2](#C_007_c4.xhtml#p4_2) shows the MATLAB code that implements the region-growing segmentation method. [Figure 4.12](#C_007_c4.xhtml#f4_12) exhibits the original image and the image obtained as a result of the operation of [Program 4.2](#C_007_c4.xhtml#p4_2).

![FIGURE 4.12 Results of the region growing segmentation method produced by Program 4.2. (a) Original image and (b) the resulting image.](images/Fig04_12.jpg)

[**FIGURE 4.12**](#C_007_c4.xhtml#f4_12b) Results of the region growing segmentation method produced by [Program 4.2](#C_007_c4.xhtml#p4_2). (a) Original image and (b) the resulting image.

## 4.7 Labeling of Objects in Binary Images

Object labeling is a classic image processing technique that is known in the literature and vision community as “region labeling”. A binary image is a numerical representation that presents only two classes of elements: ones (that indicate a specific object) and zeros (that correspond to the background). An example of a digital image with different objects is shown in [Figure 4.13](#C_007_c4.xhtml#f4_13). Under region labeling, the objective is to identify the number of binary objects contained in an image. The algorithm essentially consists of two steps: (1) temporary labeling of the objects and (2) the solution of multiple pixel labels belonging to the same object. The method is relatively complex (especially step 2). However, due to its moderate memory requirements, it represents a good choice for object labeling. The complete algorithm is described in [Algorithm 4.1](#C_007_c4.xhtml#a4_1).

![FIGURE 4.13 Binary image with four elements.](images/Fig04_13.jpg)

[**FIGURE 4.13**](#C_007_c4.xhtml#f4_13b) Binary image with four elements.

### 4.7.1 Temporary Labeling of Objects (Step 1)

In the first step, the image is analyzed from left to right and from top to bottom. At each movement, each pixel (*x*,*y*) is assigned a temporary label. The value of the label depends on the type of neighborhood defined, which can be 4-neighbors or 8-neighbors. For each case, the used mask can `be` defined as follows:

$N\_{4}\\left( {x,y} \\right) = \\begin{bmatrix} \\cdot & N\_{2} & \\cdot \\\\ N\_{1} & \\times & \\cdot \\\\ \\cdot & \\cdot & \\cdot \\\\ \\end{bmatrix}\\ N\_{8}\\left( {x,y} \\right) = \\begin{bmatrix} N\_{2} & N\_{3} & N\_{4} \\\\ N\_{1} & \\times & \\cdot \\\\ \\cdot & \\cdot & \\cdot \\\\ \\end{bmatrix}$ (4.10)

where × identifies the current pixel at position (*x*,*y*). In the case of 4-neighbors, only the pixels *N*[1] = *I*(*x*−1,*y*) and *N*[2] = *I*(*x*,*y*−1) are considered, while in the case of 8-neighbors, the pixels *N*[1], …, *N*[4] are considered. [Figure 4.14](#C_007_c4.xhtml#f4_14) shows the complete process of step 1 carried out on an image and considers the 8-neighbor neighborhood as the criterion.

### 4.7.2 Propagation of Labeling

It is considered that the pixel value of the object in a given position is *I*(*x*,*y*) = 1, while for a given background position, it is *I*(*x*,*y*) = 0. In addition, it is also assumed that the pixels outside the image are zero or part of the background. The neighborhood region is considered horizontally first and then vertically, defining the upper left corner as the starting point. In the process, if the current pixel *I*(*x*,*y*)is one, then a new label is assigned to it, or an existing one is assigned to it of one of its neighbors *N*(*x*,*y*) already has one. Therefore, the choice of the type of neighborhood (4-neighbors or 8-neighbors) for the determination of labels has a great impact on the final result. [Figure 4.14](#C_007_c4.xhtml#f4_14) exhibits the process of propagation of labeling.

![FIGURE 4.14 Propagation of the labeling process. (a) Original image. The first pixel in one is found in (b), all its neighboring pixels are zero. Therefore, the pixel receives the label of 2 (c). At the next iteration (d), a neighboring pixel has a label of 2, so the current pixel assumes this value as its label. In (e), there are two neighboring pixels with the labels 2 and 5, one of these values will be assumed by the current pixel, and the collision that occurred should be registered 2, 5.](images/Fig04_14.jpg)

[**FIGURE 4.14**](#C_007_c4.xhtml#f4_14b) Propagation of the labeling process. (a) Original image. The first pixel in one is found in (b), all its neighboring pixels are zero. Therefore, the pixel receives the label of 2 (c). At the next iteration (d), a neighboring pixel has a label of 2, so the current pixel assumes this value as its label. In (e), there are two neighboring pixels with the labels 2 and 5, one of these values will be assumed by the current pixel, and the collision that occurred should be registered 2, 5.

### 4.7.3 Adjacent Tagging

If two or more neighbors contain different labels, then a label collision occurs; that is, pixels that are grouped together to form the same object have a different label. For example, an object with the shape of a “U” will have different labels assigned to the left and right sides; this is because, during the displacement of the mask along the image, it is not possible to identify that the object is connected in the down part.

When two different labels are present on the same object (as in the previous case), a label collision occurs. This collision is not processed directly in step 1 but is only recorded for further processing in step 2. The number of collisions present depends on the content of the image and can only be known after step 1 has been completed.

As a result of the first step, we have an image with the pixels temporarily labeled, as well as a list of detected collisions among pixels belonging to the same object. [Figure 4.15a](#C_007_c4.xhtml#f4_15) shows the result of an image after step 1; all the pixels have a temporary label, while the collisions are registered and marked by circles in the correspondence 2, 4, 2, 5 and 2, 6. With this, we have the labels *E* = {2,3,4,5,6,7} and the collisions *C* = {2,4,2,5,2,6}, which correspond to the nodes of an undirected graph shown in [Figure 4.15b](#C_007_c4.xhtml#f4_15).

![FIGURE 4.15 Result of step 1 in the labeling process. Label collisions are represented by circles (a), labels and (b) collisions corresponding to nodes of a graph.](images/Fig04_15.jpg)

[**FIGURE 4.15**](#C_007_c4.xhtml#f4_15b) Result of step 1 in the labeling process. Label collisions are represented by circles (a), labels and (b) collisions corresponding to nodes of a graph.

### 4.7.4 Collision Resolution (Step 2)

The task of the second pass is to solve the collisions recorded in the first pass. This process is not easy since two different labels, tentatively belonging to two different objects, may be connected through a third object. This task is identical to the problem of finding connected components of a graph, where the labels *E* calculated in step 1 represent the nodes of the graph, while the collisions *C* their connections ([Figure 4.15](#C_007_c4.xhtml#f4_15)).

After counting the different labels belonging to the same object, the value of the label of each pixel of that object is replaced by a general label corresponding to the smallest of those within it (see [Figure 4.16](#C_007_c4.xhtml#f4_16)).

![FIGURE 4.16 Result of the object labeling process after the second step. All temporarily assigned labels are replaced by the smallest numerical label contained in the object](images/Fig04_16.jpg)

[**FIGURE 4.16**](#C_007_c4.xhtml#f4_16b) Result of the object labeling process after the second step. All temporarily assigned labels are replaced by the smallest numerical label contained in the object

In this section, the algorithm to identify the number of objects present in a binary image through its labeling has been described. The idea after having performed this algorithm is to have a label for each object contained in the image in such a way that it can be easily identified.

### 4.7.5 Implementation of the Object Labeling Algorithm Using MATLAB

This section explains how to implement the object labeling program described in [Algorithm 4.1](#C_007_c4.xhtml#a4_1). [Program 4.1](#C_007_c4.xhtml#p4_1) implements in MATLAB each of the three steps in which the algorithm has been divided. In the first step, the image is processed from right to left and from top to bottom. In general, during this process, a temporal label is assigned to each pixel of the image depending on whether it does not have labeled neighbors or has one or more. In the second step, the registered collisions are solved by considering the pixels that belong to the regions that have a neighborhood conflict. This process is implemented through two nested *for’s* that allow the label exchange for each of the elements in the image. The for loop used for the label exchange is determined by the label number whose value is the minimum (compared to the other in question). In the third step, the labels are reassigned. In this third step, several labels are eliminated due to the solution of collisions. Once the absolute number of labels is obtained, it would be very simple to use a for loop to reassign the labels so that they appear continuously. To implement this process, the `unique` function is used. The `unique` function obtains the sequence of unique values contained in an array; by unique, it means that no matter how many times this value is repeated in the array, it will only be presented once by the `unique` function. Its general syntax is:

```
b = unique(A)
```

where A is a matrix whose unique values contained in it are explored, while b is a vector that contains the values contained in the matrix without repetition; therefore, the value of b applied to our implementation will contain the labels that remained after performing the collision resolution process.

[Figure 4.17](#C_007_c4.xhtml#f4_17) shows the labeling of a series of objects contained in a binary image. These results were obtained as a result of the execution of the program in MATLAB shown in 4.3.

![FIGURE 4.17 Labeling of objects obtained by the execution of the MATLAB® program 4.3. (a) Original image and (b) labeled image.](images/Fig04_17.jpg)

[**FIGURE 4.17**](#C_007_c4.xhtml#f4_17b) Labeling of objects obtained by the execution of the MATLAB^® [program 4.3](#C_007_c4.xhtml#p4_3). (a) Original image and (b) labeled image.

## 4.8 Object Borders in Binary Images

Once the objects have already been labeled in a binary image, the next step could be the extraction of the contour or perimeter of each object. This process would seem to be simple since, at least intuitively, it would imply the registration of the pixels of an object on its border. However, as will be seen in this section, a series of elements are needed for the formulation of this algorithm, whose final objective is to make an organized description of a contour. Determining the contour of binary objects is one of the most frequent tasks in image analysis.

### 4.8.1 External and Internal Contours

As will be seen in Chapter 10 on morphological operations, it is possible to extract the boundary of binary regions using differences between morphological operations. However, in this section, the problem is faced from a more advanced perspective since the idea is not only to determine the contour of a binary object but also to order it in a sequence that can be later used to determine different properties. An object can present only an outer contour characterized by pixels that belong to the object, while other elements are in contact with the background of the image. On the other hand, the object can also have different inner contours. These types of artifacts appear due to holes present in the main object as a consequence of a poor segmentation process (see [Figure 4.18](#C_007_c4.xhtml#f4_18)).

![FIGURE 4.18 Binary object with outer and inner contour.](images/Fig04_18.jpg)

[**FIGURE 4.18**](#C_007_c4.xhtml#f4_18b) Binary object with outer and inner contour.

Another extra complication to the contour identification process (see [Figure 4.19](#C_007_c4.xhtml#f4_19)) occurs when an object becomes thinner to the limit of one pixel and again increases in size. This complication makes it difficult to process the contour since there are pixels that are processed twice in different directions. Therefore, it is not enough to set a starting point from which the contour is identified. It is also necessary to define a direction during the execution.

![FIGURE 4.19 The trajectory of the contour is represented as an ordered sequence of pixels, considered as a starting point p\_{s}. Pixels can appear on the path more than once.](images/Fig04_19.jpg)

[**FIGURE 4.19**](#C_007_c4.xhtml#f4_19b) The trajectory of the contour is represented as an ordered sequence of pixels, considered as a starting point *p*[*s*]. Pixels can appear on the path more than once.

Next, a combined algorithm will be presented that allows, unlike traditional algorithms, to combine the identification of the contours and the labeling of the objects present in a binary image.

### 4.8.2 Combination of Contour Identification and Object Labeling

This method integrates the concepts of object labeling and the process of contour identification. The objective is to perform a single execution of both operations. Under this approach, both the outer and inner contours are identified and also labeled. This algorithm does not need any complex data structures for its implementation and is very efficient compared to other similar methods.

The main idea of this algorithm, which is illustrated in [Figure 4.20](#C_007_c4.xhtml#f4_20), is simple and considers the following processing steps:

![FIGURE 4.20 Combination of contour identification and object labeling. (a) Case when a transition from background to an object occurs, the point is part of the outer boundary; (b) case when the transition from object to background occurs, the pixel is part of the inner boundary; and (c) case of a pixel of the object which is not a contour and assumes the label of its left neighbor.](images/Fig04_20.jpg)

[**FIGURE 4.20**](#C_007_c4.xhtml#f4_20b) Combination of contour identification and object labeling. (a) Case when a transition from background to an object occurs, the point is part of the outer boundary; (b) case when the transition from object to background occurs, the pixel is part of the inner boundary; and (c) case of a pixel of the object which is not a contour and assumes the label of its left neighbor.

The binary image *I*[*b*](*x*,*y*), as in the object labeling process, is processed from left to right and from top to bottom. This ensures that all pixels are considered.

The following situations may appear in the processing of an image:

**Case 1.** The transition from the background to a pixel *p*[*A*] whose value is one and which currently remains unlabeled ([Figure 4.20a](#C_007_c4.xhtml#f4_20)). When this happens, it means that the *p*[*A*] pixel is part of the outer contour of the object. Therefore, a new label is assigned to it, and the contour is processed, labeling each of the pixels that belong to it. In addition, all background pixels that are in contact with the object are assigned the value of ‒1.

**Case 2.** The transition from a pixel *p*[*B*] belonging to the object to a background pixel ([Figure 4.20b](#C_007_c4.xhtml#f4_20)). When this happens, it means that the pixel *p*[*B*] belongs to an interior contour. Therefore, the contour is processed, labeling the pixels. As in the previous case, the background pixels that are in contact with the object are assigned the value of ‒1.

**Case 3.** When a pixel of the object is not part of the contour, in this case, a pixel is labeled with the label value of its left neighbor ([Figure 4.20c](#C_007_c4.xhtml#f4_20)).

In algorithms 4.2–4.4 the complete process of the algorithm that combines the identification of contours and the labeling process is described. The **LabelOutlineCombination** process goes through the image row by row and calls the **OutlineTrace** function when a pixel belonging to an outer or inner contour is detected. The labeling of a pixel along the contours, as well as the surrounding background pixels, are registered in the structure “Label Map” *M**E*, by calling the **NextNode** function.

### 4.8.3 Implementation in MATLAB

This section explains how to implement the program that combines the contour identification and object labeling described in [Algorithm 4.1](#C_007_c4.xhtml#a4_1).

First, the algorithm considers, in the processing of the binary image, eliminating the elements outside the image. This makes the processing easier since the outside pixels are not considered neighbors during the execution of the algorithm. Therefore, the processing for an image of dimensions *M* × *N* considers the rows from 2 to *M* − 1 and columns from 2 to *N* − 1.

The algorithm is implemented in [Program 4.2](#C_007_c4.xhtml#p4_2). It uses in its operation two functions: OutlineTrace ([Program 4.5](#C_007_c4.xhtml#p4_5)) and *i* **NextNode** ([Program 4.6](#C_007_c4.xhtml#p4_6)). The **OutlineTrace** function allows you to process the outer and inner contours from a reference point **p**[*s*]. To do this, the **NextNode** function is called. This function allows you to determine from a point **p**[*s*] the next point *p* on the contour trace. If the next point does not exist, which could happen when it is an isolated pixel, the function returns as a response the same **p**[*s*] point with which the function is called. Therefore, if it is an isolated pixel, the **OutlineTrace** function terminates immediately; if this is not the case, the **NextNode** function is called consecutively as the contour is processed completely.

The **OutlineTrace** function defines the points **p**[*p*] and **p**[*c*] on the route, which corresponds to the previous position and the current position, respectively. Therefore, this process ends when **p**[*c*] = **p**[*p*], which happens when the procedure has made a complete turnaround in the contour (all elements have been analyzed).

The **NextNode** function determines, from the current point **p**[*c*], the next point of the contour. To do this, it will be necessary to specify an initial search direction (*d*). Starting from this direction, the function performs a search for the next contour pixel in 7 different directions clockwise. These directions are defined in the final part of the table described in [Algorithm 4.4](#C_007_c4.xhtml#a4_4). During this process, when it finds a pixel with a value of zero, the label map ME(*x*,*y*) assigns the value of ‒1. With this action, it is avoided going through this pixel again during the search process.

The detected contours are stored in a multidimensional array of the form `Co(:,:,NCo)`, where the first parameters define any size (consistent with the size of the binary image being processed) of the image containing the contour, while `NCo` indexes the number of contours ([Figure 4.21](#C_007_c4.xhtml#f4_21)).

![FIGURE 4.21 Results obtained by the algorithm that combines the identification of contours and labeling of objects. (a) Original image, (b) identified contours, and (c) labeled objects.](images/Fig04_21.jpg)

[**FIGURE 4.21**](#C_007_c4.xhtml#f4_21b) Results obtained by the algorithm that combines the identification of contours and labeling of objects. (a) Original image, (b) identified contours, and (c) labeled objects.

## 4.9 Representation of Binary Objects

The most natural way to represent images is by means of a matrix, in which each element of intensity or color corresponds to a position in the matrix. Using this representation, most programming languages can easily and elegantly manipulate images. A possible disadvantage of this representation is that the structure of the image is not considered. That is, it makes no difference whether the image contains a couple of lines or a complex scene, so the amount of memory needed to store it will only depend on its dimensions, not on its content.

Binary objects can be represented as a logical mask, where inside an object will have the value of one and outside the value of zero ([Figure 4.22](#C_007_c4.xhtml#f4_22)). Because a logical value only needs one bit to be represented, such an array type is called a bitmap.

![FIGURE 4.22 Use of a binary image as a mask for the specification of regions. (a) Original image, (b) binary mask, and (c) masked image.](images/Fig04_22.jpg)

[**FIGURE 4.22**](#C_007_c4.xhtml#f4_22b) Use of a binary image as a mask for the specification of regions. (a) Original image, (b) binary mask, and (c) masked image.

### 4.9.1 Length Encoding

Under this code, pixels are grouped together into blocks and represented by the description of these blocks contained in the image. Therefore, a block is a sequence of pixels whose value is one and that are distributed along either a row or a column. The compact way to represent these blocks is through a vector such that:

Block = row, column, length (4.11)

[Figure 4.23](#C_007_c4.xhtml#f4_23) shows an image and its representation under length encoding. This type of representation, as can be seen, is easy and fast to calculate and is even still used as a compression method by the TIFF and GIF formats.

![FIGURE 4.23 Length encoding example. This encoding method groups the pixels with a value of one, considering the rows as the grouping direction.](images/Fig04_23.jpg)

[**FIGURE 4.23**](#C_007_c4.xhtml#f4_23b) Length encoding example. This encoding method groups the pixels with a value of one, considering the rows as the grouping direction.

### 4.9.2 Chain Code

The objects present in an image can be represented not only by describing their area (as was the case for length encoding) but also through their contours. A classic form of this type of representation is the so-called chain encoding or Freeman code. By this method, the contours are represented starting from a reference point **p**[*s*] as a sequence of numbers that represent the changes in position through the contour ([Figure 4.24](#C_007_c4.xhtml#f4_24)). Therefore, for a closed contour defined by the sequence of points *B* = (*x*[1],*x*[2],...*x*[*M*]), the corresponding chain code is produced as the sequence *C*[*C*] = (*c*[1],*c*[2],...,*c*[*M*]), where:

![FIGURE 4.24 Chain codes based on the (a) 4-neighbor (a) and 8-neighbor. To calculate the chain codes, it is necessary to process the contour starting from the starting or reference point ps. The relative position of the neighboring pixels belonging to the contour determines the encoded direction value.](images/Fig04_24.jpg)

[**FIGURE 4.24**](#C_007_c4.xhtml#f4_24b) Chain codes based on the (a) 4-neighbor (a) and 8-neighbor. To calculate the chain codes, it is necessary to process the contour starting from the starting or reference point ***p****s*. The relative position of the neighboring pixels belonging to the contour determines the encoded direction value.

$\\begin{array}{rcl} c\_{i} & = & {\\text{code}\\left( {\\Delta x\_{i},\\Delta y\_{i}} \\right)} \\\\ \\left( {\\Delta x\_{i},\\Delta y\_{i}} \\right) & = & \\left\\{ \\begin{matrix} {\\left( {x\_{i + 1} - x\_{i},y\_{i + 1} - y\_{i}} \\right)\\,\\text{for}\\, 0 \\leq i < M\\operatorname{}} \\\\ {\\left( {x\_{1} - x\_{i},y\_{1} - y\_{i}} \\right)\\,\\text{for}\\, i = M} \\\\ \\end{matrix} \\right. \\\\ \\end{array}$ (4.12)

and the code (*Δ**x*[*i*],*Δ**y*[*i*]) is calculated from the data in [Table 4.1](#C_007_c4.xhtml#t4_1).

[**TABLE 4.1**](#C_007_c4.xhtml#t4_1b) Value Calculation of Code (*Δ**x*[*i*], *Δ**y*[*i*])

 
| *Δ**x*[*i*] || 1 || 1 || 0 || ‒1 || ‒1 || ‒1 || 0 || 1 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| *Δ**y*[*i*] || 0 || 1 || 1 || 1 || 0 || ‒1 || ‒1 || ‒1 |
| código (*Δ**x*[*i*],*Δ**y*[*i*]) || 0 || 1 || 2 || 3 || 4 || 5 || 6 || 7 |

Chain codes are compact in their definition since they specify only the absolute coordinates from a reference point **p**[*s*]. Furthermore, since the change in position between one point and another is specified by a parameter that has only eight possible values, it is feasible to use only 3 bits to encode each coefficient of the code.

### 4.9.3 Differential Chain Code

Under the representation of chain code, it is not possible to compare two different objects. This is due, first, to the fact that the description is dependent on the starting point **p**[*s*]. Then, the fact that a 90° rotation produces the description of a totally different contour. One way to solve this issue is through the use of the differential chain code. In this approach, instead of representing the directions of pixels in the contour, the differential chain code registers the changes in direction along the contour. Therefore, for a chain code represented by the sequence *C*[*C*] = (*c*[1],*c*[2],...,*c*[*M*]), its differential chain code *C*[*D*] = (*c*^′[1],*c*^′[2],...,*c*^′[*M*]) is obtained so that each parameter *c*[*i*]^′ is calculated as follows:

${c^{\\prime}}\_{i} = \\left\\{ \\begin{matrix} {\\left( {c\_{i + 1} - c\_{i}} \\right){mod}\\operatorname{}\\text{8}\\,\\text{for}\\,\\text{0} \\leq i < M} \\\\ {\\left( {c\_{1} - c\_{i}} \\right){mod}\\operatorname{}\\text{8}\\,\\text{for}\\, i = M} \\\\ \\end{matrix} \\right.$ (4.13)

The determination of each parameter *c*^′[*i*] defined by equation 4.13 considers the 8-neighbor neighborhood criterion. Thus, the element *c*^′[*i*] describes the change of direction between the pixels *c*[*i*] and *c*[*i* + 1] belonging to the contour. Considering this, the representation of the differential chain code of the chain code represented in [Figure 4.24(b)](#C_007_c4.xhtml#f4_24) is defined as follows:

$\\begin{matrix} {C\_{C} = \\left( {5,4,5,4,4,5,4,6,7,6,7,\\ldots,2,2,2} \\right)} \\\\ {C\_{D} = \\left( {7,1,7,0,1,7,2,1,7,1,1,\\ldots,0,0,3} \\right)} \\\\ \\end{matrix}$ (4.14)

To reconstruct the contour defined by *C*[*C*], it is necessary to know the starting point **p**[*s*] and its initial direction *d*, while in the case of *C*[*D*], it is not necessary to know anything.

### 4.9.4 Shape Numbers

The differential chain code can remain invariant to rotations performed on the contours. However, it remains dependent on the starting point from which the code is generated. If we want to compare two different differential codes *C*[*D*]¹ and *C*[*D*]² of length *M*, it is necessary to set a common starting point and perform the comparison. A more reliable alternative consists of considering a single value Val(*C*[*D*]) calculated from the *C*[*D*] sequence, where the set of *C*[*D*] coefficients multiplies a constant parameter *B* that defines the neighborhood established as a reference. The above could be modeled as follows:

$\\begin{array}{ccl} {\\text{Val}\\left( C\_{D} \\right)} & = & {c\_{1} \\cdot B^{0} + c\_{2} \\cdot B^{1} + \\ldots + c\_{M} \\cdot B^{M - 1}} \\\\ {\\text{Val}\\left( C\_{D} \\right)} & = & {\\sum\\limits\_{i = 1}^{M}{c\_{i} \\cdot B^{i - 1}}} \\\\ \\end{array}$ (4.15)

Under such conditions, the *C*[*D*] sequence can be cyclically shifted until the element *k* is found at which the value Val(*C*[*D*]) produces the maximum. That is:

Val(*C*[*D*]→*k*) = max  for  0 ≤ *k* < *M* (4.16)

*C*[*D*]→*k* defines a cyclic displacement of the *C*[*D*] sequence in *k* positions to the right. This process is illustrated by the following example:

$\\begin{array}{rcl} C\_{D} & = & \\left( {1,2,1,3,5,7,...,2,6,5} \\right) \\\\ \\left. C\_{D}\\rightarrow 2 \\right. & = & \\left( {6,5,1,2,1,3,5,7,...,2} \\right) \\\\ \\end{array}$ (4.17)

These Val(*C*[*D*]→*k*) = max values can be considered as normalized sequences and independent from the start or reference point. Therefore, they can be used as a means of comparison between chain sequences. As can be seen in Equation 4.16, the problem is that the calculation of these values results in very large values. Chain comparison cannot be considered a reliable method since the rotations, scaling, or deformations produced in the contours may produce incorrect conclusions.

### 4.9.5 Fourier Descriptors

An elegant approach to the description of contours is the so-called Fourier descriptors. They consider a set of points that describe the contour of an object (**x**[1],**x**[2],...,**x**[*M*]) where *x*[*i*] = (*x*,*y*) can be described as a sequence of complex numbers (**z**[1],**z**[2],...,**z**[*M*]) where:

**z**[*i*] = *x*[*i*] + *j**y* (4.18)

It is interpreted as a complex number with a real part *x* and an imaginary part *y*. From this data sequence, it is possible to construct a one-dimensional periodic function *f*(*s*) ∈ ℂ that describes the length of a contour. The coefficients of the Fourier transform of the function *f*(*s*) allow describing the contour of an object in the frequency domain, where the coefficients corresponding to lower frequencies describe the shape.

## 4.10 Features of Binary Objects

If you want to describe a binary image to another person, the worst strategy would undoubtedly be to say all the pixels contained in the image and their value, either zero or one. This will only confuse the person. A better way to describe the image would be to use the characteristics of the objects present, such as the number of objects, area, perimeter, etc. Such characteristics can be easily calculated by the computer by manipulating the entire image or a segment of it. In addition, these quantities can be used to discriminate different types of objects, making it possible to use pattern recognition techniques.

### 4.10.1 Features

A characteristic of a binary object is a certain quantitative measure that can be obtained by direct calculation of its pixels. A simple example of this characteristic is the number of pixels that integrate the object, which can be obtained by simply counting the number of elements that involve the object. To univocally describe an object, several characteristics are normally combined in a vector. This vector represents the signature of the object and can be used for classification purposes. This set of characteristics can be used to discriminate between objects based on the differences that they present in relation to their characteristic vectors. Features, as far as possible, should be robust. This means that they must not be influenced by irrelevant changes, for example, displacement, scaling, and rotation.

### 4.10.2 Geometric Features

An object *O* of a binary image can be considered as a distribution of points of value one **x**[*i*] = (*x*,*y*) located on a two-dimensional grid, that is:

*O* = {**x**[1],**x**[2],...,**x**[*N*]} = {(*x*[1],*y*[1]),(*x*[2],*y*[2]),...,(*x*[*N*],*y*[*N*])} (4.19)

For the calculation of most of the geometric characteristics, an object is considered as a set of ones that are grouped under a neighborhood criterion.

### 4.10.3 Perimeter

The perimeter of an object *O* is determined by the length of its outer contour. As [Figure 4.24](#C_007_c4.xhtml#f4_24) shows, for the calculation of the perimeter, it is necessary to consider the type of neighborhood considered since the distance of the perimeter of a contour under the 4-neighborhood is greater than the 8-neighborhood.

In the case of an 8-neighborhood, a horizontal or vertical movement (see [Figure 4.24(b)](#C_007_c4.xhtml#f4_24)) has a distance of one, while the diagonal movements have a distance of $\\sqrt{2}$. For a contour defined by an 8-neighborhood-based chain code *C*[*C*] = (*c*[1],*c*[2],...,*c*[*M*]), the perimeter can be calculated as follows:

$\\text{Perimeter}\\left( O \\right) = {\\sum\\limits\_{i = 1}^{M}{\\text{length}\\left( c\_{i} \\right)}}$ (4.20)

where:

$\\text{length}\\left( c\_{i} \\right) = \\left\\{ \\begin{matrix} {1\\text{~\\ for~}c = 0,2,4,6} \\\\ {\\sqrt{2}\\text{~for~}c = 1,3,5,7} \\\\ \\end{matrix} \\right.$ (4.21)

The perimeter calculated by Equations 4.20 and 4.21 produces a value that overcalculates the true distances. Under such conditions, in practice, this value is normally adjusted. Therefore, the new value of the perimeter defined as *U*(*O*) is calculated as follows:

*U*(*O*) = 0.95 \* Perimeter(*O*) (4.22)

### 4.10.4 Area

The area of an object *O* can be calculated simply by summing the pixels that integrate the object. That is:

Area(*O*) = *N* = |*O*| (4.23)

When the object whose area needs to be determined is not described by a grouped set of pixels but by the contour that surrounds it, it is possible to approximate the area by the length of its closed exterior contour (only if it does not contain interior contours). Under such conditions, it can be computed as follows:

$\\text{Area}\\left( O \\right) = \\frac{1}{2} \\cdot \\left| {\\sum\\limits\_{i = 1}^{M}\\left( {x\_{i} \\cdot y\_{\\lbrack{{({i + 1})}{mod}M}\\rbrack} - x\_{\\lbrack{{({i + 1})}{mod}M}\\rbrack} \\cdot y\_{i}} \\right)} \\right|$ (4.24)

where *x*[*i*] and *y*[*i*] are the coordinates of the points **x**[1], ..., **x**[*M*] that are part of the closed contour that involves the object. The contour defined by these points is described by the chain code *C*[*C*] = (*c*[1],*c*[2],...,*c*[*M*]). Geometric features such as area and perimeter are robust to displacement and rotation. However, they are highly sensitive to scaling.

### 4.10.5 Compaction and Roundness

Compaction is defined as the relationship between the area of an object and its perimeter. The perimeter *U*(*O*) of an object increases linearly by multiplying by a factor greater than one. On the other hand, the area of an object increases quadratically. Therefore, the compaction *C*(*O*) of an object *O* associates these two terms. It is calculated as follows:

$C\\left( O \\right) = \\frac{\\text{Area}\\left( O \\right)}{U^{2}\\left( O \\right)}$ (4.25)

This measure is invariant to displacements, rotations, and scaling. The compaction index has a value of (1/4π) for a round object of any diameter. Through normalization of the previous factor, the roundness characteristic can be established as:

$R\\left( O \\right) = 4\\text{π}\\frac{\\text{Area}\\left( O \\right)}{U^{2}\\left( O \\right)}$ (4.26)

*R*(*O*) evaluates how an object is similar to a round element. *R*(*O*) produces its maximum value (1) when it is a round object, while for other types of objects, the value ranges from 0 to 1. [Figure 4.25](#C_007_c4.xhtml#f4_25) shows the roundness values for different types of objects.

![FIGURE 4.25 Roundness value for different objects. (a) 1.00, (b) 0.7415, and (c) 0.4303.](images/Fig04_25.jpg)

[**FIGURE 4.25**](#C_007_c4.xhtml#f4_25b) Roundness value for different objects. (a) 1.00, (b) 0.7415, and (c) 0.4303.

### 4.10.6 Bounding Box

The Bounding Box of an object describes the minimum square that is able to contain it. This rectangle is defined by two points:

*B**B*(*O*) = (*x*[min],*x*[max],*y*[min],*y*[max]) (4.27)

where (*x*[min],*x*[max],*y*[min],*y*[max]) represents the maximum and minimum coordinates of each axis that define the rectangle.

## References

1.  [L hang](#C_007_c4.xhtml#r4_1b), Q., Zhu, X., & Cheng, Y. (2022). An enhanced image segmentation method based on morphological watershed transform. Journal of Visual Communication and Image Representation, 97, 104242. doi: [https://doi.org/10.1109/ICCIS.2010.69](https://doi.org/10.1109/ICCIS.2010.69)
2.  [Jähne](#C_007_c4.xhtml#r4_2b), B. (2013). Digital image processing: Concepts, algorithms, and scientific applications. Springer.
3.  [Burger](#C_007_c4.xhtml#r4_3b), W., & Burge, M. J. (2016). Digital Image Processing. Springer.
4.  [Umbaugh](#C_007_c4.xhtml#r4_4b), S. E. (2010). Digital image processing: Principles and applications. CRC Press.
5.  [Solomon](#C_007_c4.xhtml#r4_5b), C., & Breckon, T. (2010). Fundamentals of digital image processing: A practical approach with examples in MATLAB. Wiley.
6.  [Gose](#C_007_c4.xhtml#r4_6b), E., Johnsonbaugh, R., & Jost, S. (2017). Pattern recognition and image analysis. CRC Press.
7.  [Burger](#C_007_c4.xhtml#r4_7b), W., & Burge, M. J. (2010). Principles of digital image processing: Advanced methods. Springer.
8.  [Jahne](#C_007_c4.xhtml#r4_8b), B. (2005). Digital image processing: Concepts, algorithms, and scientific applicationsss (4th ed.). Springer.

# 5 Corner Detection

DOI: [10.1201/9781003287414-5](https://doi.org/10.1201/9781003287414-5)

Corners are defined as prominent points characterized by a high gradient value. However, different from edges, this high gradient value is not only presented in one direction but in distinct orientations \[[1](#C_008_c5.xhtml#r5_1)\]. Considering the previous definition, it is possible to visualize the corners as points in the image that belong to different edges at the same time.

The corners can be used in a wide range of applications, such as the tracking of objects in video sequences (tracking), to order the structures of objects in stereoscopic vision, as reference points in the measurement of geometric characteristics of objects, or in the calibration of cameras for vision systems \[[2](#C_008_c5.xhtml#r5_2)\]. Some of the advantages of the corners over other characteristics obtained from an image are their robustness to changes in perspective as well as their reliability in their location under different lighting conditions \[[3](#C_008_c5.xhtml#r5_3)\].

## 5.1 Corners in an Image

Considering that corners define a robust and remarkable feature of an image, their localization, as will be seen later, is not easy. An algorithm for corner detection must meet some important aspects, such as:

*   Detect “important” corners from “unimportant” ones
*   Detect the corners in the presence of noise
*   Fast execution to allow its implementation in real-time

As is natural, there are several approaches that are capable of fulfilling these characteristics. Most of these schemes are based on measurements of the gradient at the point that is considered a potential corner. While an edge is defined as a point in the image where the gradient value is especially high but in only one direction, a corner also has high gradient values but in more than one direction simultaneously \[[4](#C_008_c5.xhtml#r5_4)\].

The algorithms used for corner detection adopt the criterion of the first or second derivative over the image in the *x* or *y* direction as an approximation of the gradient value. A representative algorithm of this class of methods is the Harris Detector. Although there are some other detectors that have interesting features and properties, the Harris detector is currently the most frequently used method. For this reason, this algorithm is explained in more detail \[[5](#C_008_c5.xhtml#r5_5)\].

## 5.2 The Harris Algorithm

The algorithm developed by Harris and Stephens is based on the idea that a corner is a point in the image where the gradient value shows a high value in several directions simultaneously. This algorithm has the characteristic that it is robust when it classifies between corners and edges. In addition, this detector also presents a high degree of robustness with respect to orientation. Therefore, the corner alignment does not matter \[[6](#C_008_c5.xhtml#r5_6)\].

### 5.2.1 Matrix of Structures

The calculation of the Harris algorithm is based on the expansion of the first partial derivative in a pixel *I*(*x*,*y*) in the horizontal and vertical directions such that:

$I\_{x}\\left( {x,y} \\right) = \\frac{\\partial I\\left( {x,y} \\right)}{\\partial x}\\ \\text{y}\\ I\_{y}\\left( {x,y} \\right) = \\frac{\\partial I\\left( {x,y} \\right)}{\\partial y}$ (5.1)

For each pixel of the image (*x*,*y*), three different quantities are calculated that will be called HE[11](*x*,*y*), HE[22](*x*,*y*) and HE[12](*x*,*y*), where:

HE[11](*x*,*y*) = *I*[*x*]²(*x*,*y*) (5.2)

HE[22](*x*,*y*) = *I*[*y*]²(*x*,*y*) (5.3)

HE[12](*x*,*y*) = *I*[*x*](*x*,*y*) ⋅ *I*[*y*](*x*,*y*) (5.4)

These values can be interpreted as approximations of the elements of the matrix of structures defined as HE such that:

$\\text{HE} = \\begin{bmatrix} \\text{HE}\_{11} & \\text{HE}\_{12} \\\\ \\text{HE}\_{21} & \\text{HE}\_{22} \\\\ \\end{bmatrix}$ (5.5)

where HE[12] = HE[21].

### 5.2.2 Filtering of the Matrix of Structures

For the location of the corners using the Harris algorithm, it is necessary to smooth the values of each of the elements of the matrix of structures by convolving them through a Gaussian filter *H*[*σ*], such that the matrix HE is redefined as the matrix *E*, such that:

$E = \\begin{bmatrix} {\\text{HE}\_{11} \\ast H\_{\\sigma}} & {\\text{HE}\_{12} \\ast H\_{\\sigma}} \\\\ {\\text{HE}\_{21} \\ast H\_{\\sigma}} & {\\text{HE}\_{22} \\ast H\_{\\sigma}} \\\\ \\end{bmatrix} = \\begin{bmatrix} A & C \\\\ C & B \\\\ \\end{bmatrix}$ (5.6)

### 5.2.3 Calculation of Eigenvalues and Eigenvectors

Due to its symmetry, the matrix *E* can be diagonalized in such a way that:

$E^{\\prime} = \\begin{bmatrix} \\lambda\_{1} & 0 \\\\ 0 & \\lambda\_{2} \\\\ \\end{bmatrix}$ (5.7)

where *λ*[1] and *λ*[2] are the eigenvalues of the matrix *E*. These values are calculated according to:

$\\lambda\_{1,2} = \\frac{\\text{tr}\\left( E \\right)}{2} \\pm \\sqrt{\\left( \\frac{\\text{tr}\\left( E \\right)}{2} \\right)^{2} - \\det(E)}$ (5.8)

where tr(*E*) implies the trace of the matrix *E* and det (*E*) the determinant of the matrix *E*. Developing the operations of the trace and determinant of Equation 5.7, we obtain:

$\\lambda\_{1,2} = \\frac{1}{2}\\left( {A + B \\pm \\sqrt{A^{2} - 2AB + B^{2} + 4C^{2}}} \\right)$ (5.9)

Both eigenvalues *λ*[1] and *λ*[2] are positive and contain important information about the local structures contained in the image. Within a region of the image whose homogeneous content is a given intensity value, the value of *E* will be equal to zero (*E*\=0), so the eigenvalues in that region are also *λ*[1] = *λ*[2] = 0. However, at an intensity step change with a value of *λ*[1] > 0 and *λ*[2] = 0, the eigenvalues represent the magnitude of the gradient, while the eigenvectors correspond to the direction. [Figure 5.1](#C_008_c5.xhtml#f5_1) shows how the *λ*[1] and *λ*[2] values deliver essential information about the structures contained in an image.

![FIGURE 5.1 Relationship of structures in an image and their eigenvalues.](images/Fig05_01.jpg)

[**FIGURE 5.1**](#C_008_c5.xhtml#f5_1b) Relationship of structures in an image and their eigenvalues.

A corner point has a high gradient value both in the principal direction, which corresponds to the value of both eigenvalues, and in the direction normal to the principal, which corresponds to the smallest of the eigenvalues. From the above, it can be concluded that for a point to be considered a corner, the eigenvalues *λ*[1] and *λ*[2] must have significant values. Since *A*, *C* ≥ 0, it can then be seen that tr(*E*) > 0. With this and observing Equations 5.8 and 5.9, it can be noted that |*λ*[1]| ≥ |*λ*[2]|. Considering the above information and the concept that a corner point must have a significant magnitude in both eigenvalues, therefore, for the identification of a corner, only the *λ*[2] value that is the smallest is considered since if this value is large, then the value of *λ*[1] will be too.

### 5.2.4 Corner Value Function (***V***)

As can be seen from Equations 5.8 and 5.9, the difference between both eigenvalues is established as:

$\\lambda\_{1} - \\lambda\_{2} = 2 \\cdot \\sqrt{\\left( \\frac{\\text{tr}\\left( E \\right)}{2} \\right)^{2} - \\det(E)}$ (5.10)

where, in any case, it is true that (1/4) ⋅ tr(*E*) > det (*E*). At a corner point, the difference between the two eigenvalues is small. The Harris algorithm uses this property as significant and implements the function *V*(*x*,*y*) as an index to evaluate the existence of a corner:

*V*(*x*,*y*) = det (*E*) − *α*(tr(*E*))² (5.11)

*V*(*x*,*y*) according to Equation 5.6 leads to:

*V*(*x*,*y*) = (*A*⋅*B*−*C*²) − *α*(*A* + *B*)² (5.12)

where the parameter *α* controls the sensitivity of the algorithm. *V*(*x*,*y*) is defined as the function of the corner value, and the larger its value, the better it characterizes a corner point at (*x*,*y*). The value of *α* is fixed within the interval \[0.04, 0.25\]. If the value of *α* is large, it is less sensitive to corner points. For example, if you want to configure the Harris algorithm for higher sensitivity, the value of *α* should be 0.04. Therefore, it is evident that if *α* is small, a greater number of corner points will be found in the image. [Figure 5.2](#C_008_c5.xhtml#f5_2) shows the value of *V*(*x*,*y*) of an image. From the image, it can be observed how the corner values of the image experience a large value of the function *V*(*x*,*y*), while in the edges and homogeneous regions, the value will simply be almost zero.

![FIGURE 5.2 Value of V\\left( {x,y} \\right) of an image.](images/Fig05_02.jpg)

[**FIGURE 5.2**](#C_008_c5.xhtml#f5_2b) Value of *V*(*x*,*y*) of an image.

### 5.2.5 Determination of the Corner Points

A pixel (*x*,*y*) is considered a potential corner point if the following condition is met:

*V*(*x*,*y*) > *t*[*h*] (5.13)

where *t*[*h*] is the threshold that determines the corner affinity. Its typical value is within the range of 900 to 10,000, depending on the context of the image. Therefore, from the application of Equation 5.13, we will have a binary matrix containing ones (true) where the condition was fulfilled and zeros (false) where it was not valid.

To prevent the location of highly populated regions of corner points, which are calculated due to the high sensitivity of the value *α*, only those pixels whose value *V*(*x*,*y*) is the largest within a given neighborhood are selected. [Figure 5.3](#C_008_c5.xhtml#f5_3) shows an illustration of this process.

![FIGURE 5.3 Process of obtaining the significant corners. For all the corners found by applying the threshold t\_{h}, a defined neighborhood R\\left( {x,y} \\right) is selected. In this case, the corner value E5 has the maximum value of V\\left( {x,y} \\right) compared to the other values E4, E6, E7, E8, E9, and E10 that are within the neighborhood region defined by R\\left( {x,y} \\right). For this reason, E5 is selected as a valid corner.](images/Fig05_03.jpg)

[**FIGURE 5.3**](#C_008_c5.xhtml#f5_3b) Process of obtaining the significant corners. For all the corners found by applying the threshold *t*[*h*], a defined neighborhood *R*(*x*,*y*) is selected. In this case, the corner value E5 has the maximum value of *V*(*x*,*y*) compared to the other values E4, E6, E7, E8, E9, and E10 that are within the neighborhood region defined by *R*(*x*,*y*). For this reason, E5 is selected as a valid corner.

### 5.2.6 Algorithm Implementation

Because the Harris algorithm is considered a “complex” process, this section presents a summary of the algorithm and the steps that must be executed to locate the corner points in an image. All the steps are shown in [Algorithm 5.1](#C_008_c5.xhtml#a5_1).

As can be seen from [Algorithm 5.1](#C_008_c5.xhtml#a5_1), the original image must be filtered in order to eliminate the possible noise contained in it. In this step, a simple 3 × 3 low-pass averaging filter can be appropriate. Once the image has been filtered, the gradients of the image are obtained in the horizontal and vertical directions. There are different options that can verify this operation. However, we can use simple filters such as:

$H\_{x} = \\begin{bmatrix} {- 0.5} & \\overline{0} & 0.5 \\\\ \\end{bmatrix}\\ \\text{~~and~~}\\ H\_{y} = \\begin{bmatrix} {- 0.5} \\\\ \\overline{0} \\\\ 0.5 \\\\ \\end{bmatrix}$ (5.14)

or Sobel’s

$H\_{x} = \\begin{bmatrix} {- 1} & 0 & 1 \\\\ {- 2} & 0 & 2 \\\\ {- 1} & 0 & 1 \\\\ \\end{bmatrix}\\ \\text{~~y~~}\\ H\_{y} = \\begin{bmatrix} {- 1} & {- 2} & {- 1} \\\\ 0 & 0 & 0 \\\\ 1 & 2 & 1 \\\\ \\end{bmatrix}$ (5.15)

For more details and possibilities of filters to compute the gradient, see Chapter 7. Once we have obtained the values of the gradients, we proceed to calculate the values of the matrix of structures as described in lines 6 to 12 of [Algorithm 5.1](#C_008_c5.xhtml#a5_1).

With the calculated values of HE, we proceed to compute *E*, as illustrated in lines 11 and 12 of [Algorithm 5.1](#C_008_c5.xhtml#a5_1), by applying a Gaussian filter. The Gaussian filter, as discussed previously in this book, has a matrix of coefficients as shown in [Figure 5.4](#C_008_c5.xhtml#f5_4).

![FIGURE 5.4 The Gaussian filter for smoothing.](images/Fig05_04.jpg)

[**FIGURE 5.4**](#C_008_c5.xhtml#f5_4b) The Gaussian filter for smoothing.

With the value of *E*, we proceed to obtain the magnitude of the corner value *V*(*x*,*y*) for each pixel according to lines 13 and 14 of the algorithm.

Considering an appropriate value of *t*[*h*], the binary matrix *U*(*x*,*y*) is obtained according to lines 16 and 17. At this level of the algorithm, we have in the elements of the matrix *U*(*x*,*y*) the information of those points considered as potential corners since all the elements that are ones will have a value *V*(*x*,*y*) that is greater than the value considered as necessary (*t*[*h*]). However, due to the sensitivity characteristics of the algorithm (controlled by the parameter *α*) and the noise contained in the image, there will be several corner points concentrated near a point whose maximum value of *V*(*x*,*y*) will be higher compared to them. To solve this situation, step 3 of the algorithm described in lines 18–25 is implemented. In this part, using the information contained in the matrix *U*(*x*,*y*), the “true corner points” are localized. They are those that experience a maximum value *V*(*x*,*y*) compared to the other corner points contained in a neighborhood region *R*(*x*,*y*) centered around the test point. [Figure 5.5](#C_008_c5.xhtml#f5_5) shows a sequence of images with partial results of the application of [Algorithm 5.1](#C_008_c5.xhtml#a5_1) to detect corners on an artificially generated image.

![FIGURE 5.5 Application of the Harris algorithm to an artificially generated image with some partial results. (a) Original image, (b) image I\_{x}^{2}\\left( {x,y} \\right), (c) image I\_{y}^{2}\\left( {x,y} \\right), (d) image I\_{x}\\left( {x,y} \\right) \\cdot I\_{y}\\left( {x,y} \\right), (e) image of V\\left( {x,y} \\right), and (f) original image with the location of the “true corner points”.](images/Fig05_05.jpg)

[**FIGURE 5.5**](#C_008_c5.xhtml#f5_5b) Application of the Harris algorithm to an artificially generated image with some partial results. (a) Original image, (b) image *I*[*x*]²(*x*,*y*), (c) image *I*[*y*]²(*x*,*y*), (d) image *I*[*x*](*x*,*y*) ⋅ *I*[*y*](*x*,*y*), (e) image of *V*(*x*,*y*), and (f) original image with the location of the “true corner points”.

## 5.3 Determination of Corner Points Using MATLAB

Although MATLAB^® offers a function to identify features such as corners, in this section, we will implement the corner detection algorithm directly. The way to program the Harris algorithm will follow the steps indicated in [Algorithm 5.1](#C_008_c5.xhtml#a5_1). [Program 5.1](#C_008_c5.xhtml#p5_1) shows the MATLAB code that fully implements the Harris operator.

Next, some important aspects that must be considered in the programming of the Harris algorithm will be discussed. The first interesting aspect occurs when the arrays *U*(*x*,*y*) as well as *S*(*x*,*y*) are initialized with zeros. This action is a standard situation in those applications where pixels with some special characteristics are located, which in quantity will obviously be much less compared to the size of the image.

Considering the above, it is much more practical and faster to initialize the arrays with zeros and place elements inside that meet a certain property. The implemented smoothing prefilter is a “Box” type filter, with a mask of 3 × 3, while the filters used to calculate the gradients are those defined in Equation 5.14. All operations performed between images and filters in [Program 5.1](#C_008_c5.xhtml#p5_1) are performed by the MATLAB imfilter function discussed in detail in previous sections of this book.

The operations executed for the calculation of the elements of the matrix of structures, as they are element-by-element processes, are carried out by applying the MATLAB dot operator, that is, considering the expressions

*A* \* *B* (5.16)

*A*. \* *B* (5.17)

The first (5.16) implies matrix multiplication between the images *A* and *B*, while the second (5.17) defines point-to-point multiplication between all the elements of the matrices *A* and *B*.

Another important part of [Program 5.1](#C_008_c5.xhtml#p5_1) is represented by step 3. It integrates the necessary instructions for selecting the pixels whose *V*(*x*,*y*) value is maximum within a region. To program this procedure, the image is sequentially processed pixel by pixel, finding the maximum value of a neighborhood block or region established around the point in question. To do this, the limits of the block are set relative to the pixel position in question. In the case of [Program 5.1](#C_008_c5.xhtml#p5_1), the interval is set equal to 10. Therefore, considering both directions, the total size is 20. Once the limits are established, the block is extracted, and the maximum value is found. If the maximal value of the block corresponds to the central pixel of the block, then a one is set in position *S*(*x*,*y*). Therefore, the ones in *S*(*x*,*y*) represent the corner points found in the image. [Figure 5.3](#C_008_c5.xhtml#f5_3) shows the process of finding the maximum value within the considered neighborhood around the point in question.

Once the points are stored in *S*(*x*,*y*), they are plotted. To carry out this process, the image is first displayed using the well-known display function used by MATLAB: imshow. Then, using the hold on command, the image is maintained, and the points are drawn on it one by one using the plot command, placing a plus sign + at each point. [Figure 5.6](#C_008_c5.xhtml#f5_6) shows the location of the corner points detected once [Program 5.1](#C_008_c5.xhtml#p5_1) has been executed on an example image.

![FIGURE 5.6 Location of the corner points according to the Harris algorithm. (a) Original image, (b) Image with corner points located for a value of \\alpha = 0.1](images/Fig05_06.jpg)

[**FIGURE 5.6**](#C_008_c5.xhtml#f5_6b) Location of the corner points according to the Harris algorithm. (a) Original image, (b) Image with corner points located for a value of *α* = 0.1

## 5.4 Other Corner Detectors

In this section, some other existing detectors that allow finding corners of an image will be analyzed. Among the approaches analyzed are the Beaudet operator, Kitchen & Rosenfeld, and Wang & Brady \[[7](#C_008_c5.xhtml#r5_7)\]. All the operators considered here are based on the computation of the Hessian matrix or the Hessian. For this reason, it is necessary to analyze certain details about this matrix.

The Hessian matrix of a function *f* of *n* variables is a *n* × *n* square matrix that integrates the second partial derivatives of *f*. So given a real function *f* of two real variables:

*f* = (*x*,*y*) (5.18)

If all second partial derivatives of *f* exist, the Hessian matrix of *f* is defined as:

*H*[*f*](*x*,*y*) (5.19)

where

$H\_{f}\\left( {x,y} \\right) = \\begin{bmatrix} \\frac{\\partial^{2}f\\left( {x,y} \\right)}{\\partial x^{2}} & \\frac{\\partial^{2}f\\left( {x,y} \\right)}{\\partial x\\partial y} \\\\ \\frac{\\partial^{2}f\\left( {x,y} \\right)}{\\partial x\\partial y} & \\frac{\\partial^{2}f\\left( {x,y} \\right)}{\\partial y^{2}} \\\\ \\end{bmatrix}$ (5.20)

The components of the Hessian are defined as:

$I\_{xx} = \\frac{\\partial^{2}f\\left( {x,y} \\right)}{\\partial x^{2}}$ (5.21)

$I\_{yy} = \\frac{\\partial^{2}f\\left( {x,y} \\right)}{\\partial y^{2}}$ (5.22)

$I\_{xy} = \\frac{\\partial^{2}f\\left( {x,y} \\right)}{\\partial x\\partial y}$ (5.23)

### 5.4.1 Beaudet Detector

The Beaudet detector is an isotropic operator based on the calculation of the determinant of the Hessian. Therefore, if the Hessian is defined by Equation 5.20, its determinant is computed as follows:

det (*H*[*f*](*x*,*y*)) = *I*[*x**x*]*I*[*y**y*] − *I*[*x**y*]² (5.24)

Based on the calculation of the determinant, the Beaudet detector is defined as:

$B\\left( {x,y} \\right) = \\frac{\\det(H\_{f}\\left( {x,y} \\right))}{\\left( {1 + I\_{x}^{2}\\text{+I}\_{y}^{2}} \\right)^{2}}$ (5.25)

where *I*[*x*] and *I*[*y*] are defined as follows:

$I\_{x} = \\frac{\\partial f\\left( {x,y} \\right)}{\\partial x}\\ \\text{y}\\ I\_{y} = \\frac{\\partial f\\left( {x,y} \\right)}{\\partial y}$ (5.26)

Similar to the gradients, under this operator, the points from *B*(*x*,*y*) that exceed a certain predetermined threshold will be considered corners. [Program 5.2](#C_008_c5.xhtml#p5_2) shows the MATLAB program that fully implements the Beaudet detector.

[Figure 5.7](#C_008_c5.xhtml#f5_7) shows the corners detected in an example image using the Beaudet algorithm. For didactical reasons, in the following examples, the same image will be used for analysis and comparison purposes.

![FIGURE 5.7 Location of corner points according to Beaudet’s algorithm.](images/Fig05_07.jpg)

[**FIGURE 5.7**](#C_008_c5.xhtml#f5_7b) Location of corner points according to Beaudet’s algorithm.

### 5.4.2 Kitchen & Rosenfield Detector

Kitchen & Rosenfeld proposed a corner detector based on the change of gradient. Under such conditions, the Kitchen and Rosenfeld detector can be computed using the following model:

$KR\\left( {x,y} \\right) = \\frac{I\_{xx} \\cdot I\_{y}^{2} + I\_{yy} \\cdot I\_{x}^{2} - 2 \\cdot I\_{xy} \\cdot I\_{y}}{I\_{x}^{2} + I\_{y}^{2}}$ (5.27)

In this approach, the corners are considered as those values that exceed a predetermined value considered as a threshold. [Program 5.3](#C_008_c5.xhtml#p5_3) shows the MATLAB program that fully implements the Kitchen & Rosenfeld operator.

[Figure 5.8](#C_008_c5.xhtml#f5_8) shows the corners detected in an example image using the Kitchen & Rosenfeld algorithm.

![FIGURE 5.8 Location of the corner points according to the Kitchen & Rosenfeld algorithm.](images/Fig05_08.jpg)

[**FIGURE 5.8**](#C_008_c5.xhtml#f5_8b) Location of the corner points according to the Kitchen & Rosenfeld algorithm.

### 5.4.3 Wang & Brady Detector

The Wang & Brady operator for corner detection considers an image as a surface. Under such conditions, the algorithm searches for places in the image where the direction of an edge changes abruptly. To do this, a coefficient *C*(*x*,*y*) is defined where the change of direction is evaluated under the following expression:

*C*(*x*,*y*) = ∇²*I*(*x*,*y*) + *c*|∇*I*(*x*,*y*)| (5.28)

where *c* represents a parameter that calibrates the sensitivity of the algorithm. While ∇²*I*(*x*,*y*) and ∇*I*(*x*,*y*) are defined as:

$\\begin{matrix} {\\nabla^{2}I\\left( {x,y} \\right) = \\frac{\\partial^{2}I\\left( {x,y} \\right)}{\\partial x^{2}} + \\frac{\\partial^{2}I\\left( {x,y} \\right)}{\\partial y^{2}}} \\\\ {\\nabla I\\left( {x,y} \\right) = \\frac{\\partial I\\left( {x,y} \\right)}{\\partial x} + \\frac{\\partial I\\left( {x,y} \\right)}{\\partial y}} \\\\ \\end{matrix}$ (5.29)

Therefore, to detect whether a pixel is a corner or not, it is considered a threshold. Under such circumstances, if a pixel fulfills the conditions imposed by the threshold, it is considered as a corner. Otherwise, it is not a corner. Using the derivative approximation defined in Equation 7.2 (mentioned in Chapter 7), it can be established that:

$\\begin{matrix} {\\frac{\\partial I\\left( {x,y} \\right)}{\\partial x} = - 0.5I\\left( {x - 1,y} \\right) + 0.5\\left( {x + 1,y} \\right)} \\\\ {\\frac{\\partial I\\left( {x,y} \\right)}{\\partial y} = - 0.5I\\left( {x,y - 1} \\right) + 0.5\\left( {x,y + 1} \\right)} \\\\ \\end{matrix}$ (5.30)

Therefore, the operator ∇*I*(*x*,*y*) is redefined, such that:

$\\begin{array}{ccl} {{\\nabla I}\\left( {x,y} \\right)} & = & {{{- 0.5}I\\left( {{x - 1},y} \\right)} + {0.5I\\left( {{x + 1},y} \\right)} - {0.5I\\left( {x,{y - 1}} \\right)} + {0.5I\\left( {x,{y + 1}} \\right)}} \\\\ {{\\nabla I}\\left( {x,y} \\right)} & = & \\begin{bmatrix} 0 & {- 0.5} & 0 \\\\ {- 0.5} & 0 & 0.5 \\\\ 0 & 0.5 & 0 \\\\ \\end{bmatrix} \\\\ \\end{array}$ (5.31)

Similarly, it is established in Equations 7.29 and 7.30 of Chapter 7 that:

$\\begin{matrix} {\\frac{\\partial^{2}I\\left( {x,y} \\right)}{\\partial x^{2}} = I\\left( {x + 1,y} \\right) - 2I\\left( {x,y} \\right) + I\\left( {x - 1,y} \\right)} \\\\ {\\frac{\\partial^{2}I\\left( {x,y} \\right)}{\\partial y^{2}} = I\\left( {x,y + 1} \\right) - 2I\\left( {x,y} \\right) + I\\left( {x,y - 1} \\right)} \\\\ \\end{matrix}$ (5.32)

So that:

$\\begin{array}{ccl} {{\\nabla^{2}I}\\left( {x,y} \\right)} & = & {{I\\left( {{x + 1},y} \\right)} + {I\\left( {{x - 1},y} \\right)} + {I\\left( {x,{y + 1}} \\right)} + {I\\left( {x,{y - 1}} \\right)} - {4I\\left( {x,y} \\right)}} \\\\ {{\\nabla^{2}I}\\left( {x,y} \\right)} & = & \\begin{bmatrix} 0 & 1 & 0 \\\\ 1 & {- 4} & 1 \\\\ 0 & 1 & 0 \\\\ \\end{bmatrix} \\\\ \\end{array}$ (5.33)

[Program 5.4](#C_008_c5.xhtml#p5_4) shows the MATLAB program that fully implements the Wang & Brady operator.

[Figure 5.9](#C_008_c5.xhtml#f5_9) shows the corners detected in an example image using the Wang & Brady algorithm.

![FIGURE 5.9 Location of the corner points according to the Wang & Brady algorithm.](images/Fig05_09.jpg)

[**FIGURE 5.9**](#C_008_c5.xhtml#f5_9b) Location of the corner points according to the Wang & Brady algorithm.

In order to show a comparative vision of the operators considered in this section, [Figure 5.10](#C_008_c5.xhtml#f5_10) shows the application of the different algorithms: Harris, Beaudet, Kitchen & Rosenfeld, and Wang & Brady.

![FIGURE 5.10 Comparison of algorithms for corner detection: + Harris, o Beaudet, x Kitchen & Rosenfeld, and □ Wang & Brady.](images/Fig05_10.jpg)

[**FIGURE 5.10**](#C_008_c5.xhtml#f5_10b) Comparison of algorithms for corner detection: + Harris, o Beaudet, x Kitchen & Rosenfeld, and □ Wang & Brady.

## References

1.  [Acharya](#C_008_c5.xhtml#r5_1b), T., & Ray, A. K. (2017). Image processing: Principles and applications. CRC Press.
2.  [Umbaugh](#C_008_c5.xhtml#r5_2b), S. E. (2017). Digital image processing and analysis: Human and computer vision applications with CVIPtools (2nd ed.). CRC Press.
3.  [Russ](#C_008_c5.xhtml#r5_3b), J. C. (2011). The image processing handbook (6th ed.). CRC Press.
4.  [McAndrew](#C_008_c5.xhtml#r5_4b), A. (2017). Introduction to digital image processing with MATLAB. CRC Press.
5.  [Chen](#C_008_c5.xhtml#r5_5b), J., Zou, L. H., Zhang, J., & Dou, L. H. (2009). The comparison and application of corner detection algorithms. Journal of Multimedia, 4(6), 435–441.
6.  [Ye](#C_008_c5.xhtml#r5_6b), Z., Pei, Y., & Shi, J. (2009). An improved algorithm for Harris corner detection. In *2009 2nd International Congress on Image and Signal Processing* (pp. 1–4). IEEE.
7.  [Mehrotra](#C_008_c5.xhtml#r5_7b), R., Nichani, S., & Ranganathan, N. (1990). Corner detection. Pattern Recognition, 23(11), 1223–1233.

# 6 Line Detection

DOI: [10.1201/9781003287414-6](https://doi.org/10.1201/9781003287414-6)

## 6.1 Structures in an Image

An intuitive approach to finding structures in an image could consist of starting from a certain point belonging to an edge, step by step adding the pixels belonging to the entire edge, and with them determining the structure. The previous approximation can be tried both on images from gradient thresholding as well as images from segmentation. This approximation, however, will fail as it does not consider the fractures and ramifications in the edges due to the noise and the uncertainty inherent to the algorithms for calculating the gradient or the segmentation that do not incorporate any kind of criteria on the shapes that are sought in the image \[[1](#C_009_c6.xhtml#r6_1)\].

A totally different approach is the global search for structures present in the image that somehow approximate or relate to a previously specified type of form. As can be seen in [Figure 6.1](#C_009_c6.xhtml#f6_1), to the eyes of a human, the types of structures present in the images are clearly distinguishable, despite the large number of added points. Until now, the responsible biological mechanism that allows relating and recognizing structures in the images perceived by humans or animals has been unknown. A technique that allows, at least from the computational point of view, to solve this problem is the so-called Hough transform \[[2](#C_009_c6.xhtml#r6_2)\], which will be treated in detail in this chapter.

![FIGURE 6.1 Existing biological mechanisms in humans allow geometric parametric structures to be clearly identified without uncertainty, despite the set of points added as noise to the images (a) and (b).](images/Fig06_01.jpg)

[**FIGURE 6.1**](#C_009_c6.xhtml#f6_1b) Existing biological mechanisms in humans allow geometric parametric structures to be clearly identified without uncertainty, despite the set of points added as noise to the images (a) and (b).

## 6.2 Hough Transform

The Hough Transform method, devised by Paul Hough and patented in the United States of America, is commonly known in the vision community as the Hough Transform \[[3](#C_009_c6.xhtml#r6_3)\]. This transform allows locating parametric shapes from a distribution of points present in an image \[[4](#C_009_c6.xhtml#r6_4)\]. Parametric shapes are lines, circles, or ellipses, which can be described by using a few parameters. Because these types of objects (lines, circles, and ellipses), as shown in [Figure 6.2](#C_009_c6.xhtml#f6_2), are frequently presented in images, it is especially important to find them automatically.

![FIGURE 6.2 Parametric figures such as lines, circles, or ellipses are frequently present in images.](images/Fig06_02.jpg)

[**FIGURE 6.2**](#C_009_c6.xhtml#f6_2b) Parametric figures such as lines, circles, or ellipses are frequently present in images.

In this chapter, the use of the Hough Transform will be analyzed for the detection of lines on binary images produced by gradient thresholding because this is a frequent application in many vision or image processing systems \[[5](#C_009_c6.xhtml#r6_5)\], and it is also the case introduction that allows to analyze the capacities of this transform. A line in a two-dimensional space is described by using two real parameters expressed in Equation 6.1,

*y* = *k**x* + *d* (6.1)

where *k* represents the slope and the point of the axis where the line intercepts it (see [Figure 6.3](#C_009_c6.xhtml#f6_3)). A line that passes through two different points *p*[1] = (*x*[1],*y*[1]) and *p*[2] = (*x*[2],*y*[2]) must satisfy the following conditions:

![FIGURE 6.3 Two points p1 and p2 that belong to the same line, to determine the equation of the line, it will be necessary to estimate the values k and d.](images/Fig06_03.jpg)

[**FIGURE 6.3**](#C_009_c6.xhtml#f6_3b) Two points *p*1 and *p*2 that belong to the same line, to determine the equation of the line, it will be necessary to estimate the values *k* and *d*.

*y*[1] = *k**x*[1] + *d* y *y*[2] = *k**x*[2] + *d* (6.2)

where *k*, *d* ∈ ℜ. The objective, therefore, is to estimate the parameters *k* and *d* of a line that passes through different points belonging to the edges of an object. Faced with this situation, the question arises: How can it be determined what possible points a line encompasses? A possible approach would be to draw all the possible lines in an image and count exactly the points that pass over each one of them, and then delete all those lines that do not contain more than a certain number of points. The above is possible, however, because the number of possible lines that would be drawn on the image is very large, which would make it especially inefficient.

### 6.2.1 Parameter Space

The Hough Transform solves the line detection problem in a slightly different way: by producing all possible lines that pass through a pixel that corresponds to an edge of the image \[[6](#C_009_c6.xhtml#r6_6)\]. Each line *L*[*p*] that passes through a point *p*[0] = (*x*[0],*y*[0]) has the following equation:

*L*[*P*] : *y*[0] = *k**x*[0] + *d* (6.3)

where the values of *k* and *d* are varied to draw all the possible lines that have *x*[0] and *y*[0] in common. The set of solutions for *k* and *d* of Equation 6.3 corresponds to an infinite number of lines that pass through the points *x*[0] and *y*[0] (see [Figure 6.4](#C_009_c6.xhtml#f6_4)). For a given value of *k*, the corresponding solution of 6.3 is produced as a function of *d*, which would imply:

![FIGURE 6.4 Set of lines that pass through a common point p0. All possible lines Lp passing through p0 have the expression y\_{0} = kx\_{0} + d where the values k and d are variables and determine the difference between each of the defined lines.](images/Fig06_04.jpg)

[**FIGURE 6.4**](#C_009_c6.xhtml#f6_4b) Set of lines that pass through a common point *p*0\. All possible lines *L*p passing through *p*0 have the expression *y*[0] = *k**x*[0] + *d* where the values k and d are variables and determine the difference between each of the defined lines.

*d* = *y*[0] − *k**x*[0] (6.4)

This represents a linear function, where *k* and *d* are the variables and *x*[0] and *y*[0] are the constants of the parameters considered in the function. The solution set {(*k*,*d*)} of Equation 6.4 describes the parameters of all possible lines that pass through the point *p*[0] = (*x*[0],*y*[0]).

For a given pixel of the image *p*[*i*] = (*x*[*i*],*y*[*i*]), according to Equation 8.4, there is a set of straight lines defined by:

*R*[*i*] : *d* = *y*[*i*] − *k**x*[*i*] (6.5)

Having as variable parameters *k* and *d* which define the parameter space also called the Hough space, while *x*[*i*] and *y*[*i*] are the fixed parameters also called the image parameter space. The way in which both spaces are related is summarized in [Table 6.1](#C_009_c6.xhtml#t6_1).

[**TABLE 6.1**](#C_009_c6.xhtml#t6_1b) Fields of the Structure Returned by the houghlines Function

 
| Field || Description |
| --- | --- |
| **point1** || It is a 2-element vector (*x*,*y*) that specifies the start of the segment. |
| --- | --- |
| **point2** || It is a 2-element vector (*x*,*y*) that specifies the end of the segment. |
| **Theta** || Vector containing information on how linearly the parameter *θ* was divided. |
| **rho** || Vector containing information on how linearly the parameter r was divided. |

Each point *p*[*i*] in the image parameter space corresponds to a line in the Hough parameter space. Considering the above, we are interested in those points where the lines established in the Hough parameter space intersect, which will correspond to the values of *k* and *d* that represent the line of the image space that passes through the points that formulated the lines in the Hough parameter space. As shown in [Figure 6.5](#C_009_c6.xhtml#f6_5), the lines *R*[1] and *R*[2] intersect at the point *q* = (*k*[12],*d*[12]) in the Hough parameter space, which represent the points *p*[1] and *p*[2] in the parameter space of the image. So, the line in the image space will have a slope of *k*[12] and an intercept point on the y-axis of *d*[12]. The more lines in the Hough parameter space that intersect mean that the line in the image space will be made up of that number of points. So, it could be established that:

If *N**R* is the number of lines that intersect in $\\left( {\\overline{k},\\overline{d}} \\right)$ of the Hough parameter space, then there will be *N**R* points that lie on the line defined by $y = \\overline{k}x + \\overline{d}$ in the image space.

### 6.2.2 Accumulation Records Matrix

The method for locating lines in an image is based on finding the coordinates in the Hough parameter space where several lines are cut. To calculate the Hough transform, it is first necessary to discretize in a stepped manner the range of values corresponding to *k* and *d*. When counting cuts produced by the intersection of several lines in the Hough parameter space, an accumulation records matrix is used, where each cell is increased based on the number of lines that pass through that cell. In such a way that the final number *N*[*p*] stored in the register would mean that this specific line is made up of *N*[*p*] pixels of the image parameter space. [Figure 6.6](#C_009_c6.xhtml#f6_6) illustrates this process considering the one taken in [Figure 6.5](#C_009_c6.xhtml#f6_5) as an example.

![FIGURE 6.5 Relationship between the image parameter space and the Hough parameter space. (a) Image parameter space and (b) Hough parameter space. Points in the parameter space correspond to lines in the Hough parameter space, while the reverse is also true, a point in the Hough parameter space corresponds to a line in the image parameter space. In the image, the points p1 and p2 of the image parameter space correspond to the lines R1 and R2 in the Hough parameter space; likewise, the point q12 = (k12, d12) the Hough parameter space corresponds to the line L12 of the image parameter space.](images/Fig06_05.jpg)

[**FIGURE 6.5**](#C_009_c6.xhtml#f6_5b) Relationship between the image parameter space and the Hough parameter space. (a) Image parameter space and (b) Hough parameter space. Points in the parameter space correspond to lines in the Hough parameter space, while the reverse is also true, a point in the Hough parameter space corresponds to a line in the image parameter space. In the image, the points *p*[1] and *p*[2] of the image parameter space correspond to the lines *R*[1] and *R*[2] in the Hough parameter space; likewise, the point *q*[12] = (*k[1]*[2], *d*[12]) the Hough parameter space corresponds to the line L[12] of the image parameter space.

![FIGURE 6.6 Fundamental idea of the Hough transform. (a) Image parameter space and (b) accumulator in Hough parameter space. As can be seen, the accumulation register matrix is the discretized version of the Hough parameter space. For each point in the parameter space of image (a), there is a line in the Hough parameter space. The operation that is carried out is additive, which means that each cell of the matrix is increased by a value of one as a line passes through it. In this way, the points that maintain a local maximum in the Hough parameter space represent the k and d values that represent the lines in the image parameter space.](images/Fig06_06.jpg)

[**FIGURE 6.6**](#C_009_c6.xhtml#f6_6b) Fundamental idea of the Hough transform. (a) Image parameter space and (b) accumulator in Hough parameter space. As can be seen, the accumulation register matrix is the discretized version of the Hough parameter space. For each point in the parameter space of image (a), there is a line in the Hough parameter space. The operation that is carried out is additive, which means that each cell of the matrix is increased by a value of one as a line passes through it. In this way, the points that maintain a local maximum in the Hough parameter space represent the k and d values that represent the lines in the image parameter space.

### 6.2.3 Parametric Model Change

So far, the basic idea of the Hough transform has been shown. However, the representation of the straight line defined in Equation 6.1 cannot be used due to the computational error caused in the vertical lines where *k* = ∞. A better option represents the use of the equation:

*x* ⋅ cos (*θ*) + *y* ⋅ sin(*θ*) = *r* (6.6)

which does not present any singularity and also allows a linear quantification of its parameters *r* and *θ*. [Figure 6.7](#C_009_c6.xhtml#f6_7) illustrates the singularity problem in Equation 6.1 and shows how to relate Equation 6.6 to the line problem. With the use of Equation 6.6 for the description of lines, the Hough parameter space varies. So, the parameter space of the coordinates *r* and *θ* and the point *p*[*i*] = (*x*[*i*],*y*[*i*]) of the image parameter space are related according to the equation:

![FIGURE 6.7 Different types of parameters that can be used to characterize lines. Option (a) shows the singularity for when trying to characterize a vertical line; in that case k = \\infty, when choosing the characterization of lines by this type of parameter, any type of line could be represented except those close to the vertical position. A better approach would be the use of Equation 6.6, which, in addition to not showing the singularity, allows a linear quantification of its parameters, where the relationship between the line and the parameters is characterized in (b), with the referred line being the normal to the vector defined by r and \\theta.](images/Fig06_07.jpg)

[**FIGURE 6.7**](#C_009_c6.xhtml#f6_7b) Different types of parameters that can be used to characterize lines. Option (a) shows the singularity for when trying to characterize a vertical line; in that case *k* = ∞, when choosing the characterization of lines by this type of parameter, any type of line could be represented except those close to the vertical position. A better approach would be the use of Equation 6.6, which, in addition to not showing the singularity, allows a linear quantification of its parameters, where the relationship between the line and the parameters is characterized in (b), with the referred line being the normal to the vector defined by *r* and *θ*.

*r*[*x*[*i*], *y*[*i*]] = *x*[*i*] ⋅ cos (*θ*) + *y*[*i*] ⋅ sin(*θ*) (6.7)

where the range of values for *θ* is 0 ≤ *θ* < π (see [Figure 6.8](#C_009_c6.xhtml#f6_8)). If the center of the image (*x*[*c*],*y*[*c*]) is used as a reference point to define image pixel coordinates (so that there could be positive and negative indices for both *x* and *y*), then the range of values of *r* is restricted to half being defined by:

![FIGURE 6.8 Partial results obtained from the application of the Hough algorithm for line detection in a simple image. (a) Original image and (b) the matrix of the accumulator records of the Hough parameter space.](images/Fig06_08.jpg)

[**FIGURE 6.8**](#C_009_c6.xhtml#f6_8b) Partial results obtained from the application of the Hough algorithm for line detection in a simple image. (a) Original image and (b) the matrix of the accumulator records of the Hough parameter space.

 − *r**x*, *y*[max][max] (6.8)

where:

$r{\\sqrt{\\left( \\frac{M}{2} \\right)^{2} + \\left( \\frac{N}{2} \\right)^{2}}}\_{\\text{max}}$ (6.9)

where *M* and *N* represent the width and height of the image.

## 6.3 Hough Transform Implementation

[Algorithm 6.1](#C_009_c6.xhtml#a6_1) shows the way in which the parameters of the lines present in an image are found by means of the Hough Transform, using the one shown in Equation 6.6 as the straight-line model. A binary image is used as input to the algorithm, which contains edge information (extracted using methods such as those explained in [Chapter 3](#C_006_c3.xhtml)). From now on, it will be used as a convention that a one in the image determines that the pixel is part of the border and a zero that it is part of the background.

As a first step, all the cells of the accumulation register matrix are set to zero (statement 1). Then the binary image is traversed (sentence 3) *I*(*x*,*y*), in such a way that each time an edge pixel is found (that is, its value is one), the values of *r* are obtained from Equation 6.6, performing a sweep of the parameter *θ*. from 0 to sentences 5 and 6). However, to find the values of *r*, the center (*x*[*c*],*y*[*c*]) of the image *I*(*x*,*y*) is used as reference coordinates. For each pair (*r*,*θ*) obtained from the scan, the register of the accumulation matrix is increased (statement 7) by the indices corresponding to *r* and *θ*. In this way, once all the pixels of the image have been traversed, the registers that have been increased, obtaining the local maxima (sentence 8) that will correspond to the values of (*r*,*θ*) that will define the lines identified in the image. *I*(*x*,*y*). In order to find the local maxima of the accumulator record matrix, a threshold is first applied so that only the points greater than that threshold remain, and then a search is performed on the image, finding the local maxima found in the image. considering a given neighborhood. The fact that the values of several registers neighboring the register with the maximum value, whose indices *r* and *θ* represent the parameters that model the real line contained in **I**(**x**,**y**), have large values, is due to the noise and inaccuracies produced by a faulty quantization of the Hough parameter space.

[Figure 6.9](#C_009_c6.xhtml#f6_9) shows a series of images that represent the partial results of [Algorithm 6.1](#C_009_c6.xhtml#a6_1). [Figure 6.9a](#C_009_c6.xhtml#f6_9) represents the original image produced artificially to exemplify the use of Hough’s algorithm for line detection. [Figure 6.9b](#C_009_c6.xhtml#f6_9) shows the edges obtained by applying Canny’s algorithm (see Chapter 7). In [Figure 6.9c](#C_009_c6.xhtml#f6_9), the content of the accumulation records matrix of the image is shown. It can also be observed that the bright points represent those locations whose values have increased significantly, becoming highly potential points of the real parameters *r* and *θ* that represent the real lines of the original image *I*(*x*,*y*). [Figure 6.9d](#C_009_c6.xhtml#f6_9) shows the image produced by applying a threshold to the accumulation records matrix. [Figure 6.9e](#C_009_c6.xhtml#f6_9) locates the records that have a maximum value considering a given neighborhood. Finally, [Figure 6.9f](#C_009_c6.xhtml#f6_9) shows the lines found using the Hough algorithm with parameters *r* and *θ*.

![FIGURE 6.9 Partial results obtained from the application of the Hough algorithm for line detection in a real image. (a) Original image, (b) the edges of the original image, (c) the matrix of the accumulator records of the Hough parameter space, (d) image obtained from the application of the threshold to (c), (e) location of the maximum points, and (f) lines obtained by the application of the Hough algorithm.](images/Fig06_09.jpg)

[**FIGURE 6.9**](#C_009_c6.xhtml#f6_9b) Partial results obtained from the application of the Hough algorithm for line detection in a real image. (a) Original image, (b) the edges of the original image, (c) the matrix of the accumulator records of the Hough parameter space, (d) image obtained from the application of the threshold to (c), (e) location of the maximum points, and (f) lines obtained by the application of the Hough algorithm.

In [Figure 6.9e](#C_009_c6.xhtml#f6_9), it can be seen from the maximum points obtained that the closest points (5 and 6), practically contiguous, represent the parallel lines of [Figure 6.9a](#C_009_c6.xhtml#f6_9) that have the same slope, that is, the same value of *θ*.

## 6.4 Encoding the Hough Transform in MATLAB

In this section, the Hough transform is implemented in the detection of lines using MATLAB^® as a programming language; however, it is worth mentioning that the tools already implemented in MATLAB that allow directly detecting the lines in the image by means of the Hough transform are not used in this section.

For the implementation of the Hough transform, it is necessary to consider 3 different parts of the code. [Program 6.1](#C_009_c6.xhtml#p6_1) shows the commented code that implements the Hough transform used for line detection.

In the first part, in addition to initializing some variables, the Hough transform indicated by steps 1–7 of [Algorithm 6.1](#C_009_c6.xhtml#a6_1) is implemented.

The second part of Program 8.1 is made up of the necessary instructions for choosing the pixels whose value of **MRAcc** is maximum within a block considered as the neighborhood region. To program such an event, the matrix (to which the threshold *t*[*h*] was applied) is traversed sequentially, pixel by pixel, finding the maximum value of a neighborhood block or region *R*(*x*,*y*) established around the point in question. To do this, the limits of the block relative to the pixel in question are set. In the case of [Program 6.1](#C_009_c6.xhtml#p6_1), the interval is set equal to 10, which, considering it in both directions, would be 20. Once the limits are established, the block is extracted and the maximum is found. If the maximum of the block corresponds to the central pixel of the block relative to that of the scanning process, a one is placed in that position in the End matrix in such a way that the indices where there are ones in End will correspond to the parameters that define the lines of the original image. [Figure 6.10](#C_009_c6.xhtml#f6_10) shows the process of finding the maximum within the considered neighborhood around the point in question.

![FIGURE 6.10 Process for obtaining the register of significant accumulators. Of all the points found by applying the threshold th, the one whose value MRAcc is the maximum in a defined neighborhood R(x,y), is selected. In this case, the point value P5 has the maximum value of MRAcc compared to the other values P4, P6, P7, P8, P9, and P10 that are within the neighborhood region defined by R(x,y).](images/Fig06_10.jpg)

[**FIGURE 6.10**](#C_009_c6.xhtml#f6_10b) Process for obtaining the register of significant accumulators. Of all the points found by applying the threshold *th*, the one whose value MRAcc is the maximum in a defined neighborhood *R*(*x*,*y*), is selected. In this case, the point value P5 has the maximum value of MRAcc compared to the other values P4, P6, P7, P8, P9, and P10 that are within the neighborhood region defined by *R*(*x*,*y*).

In the third part, the straight lines found by applying the Hough Transform are displayed. For this, it is considered that the values of the parameters *r* and *θ* represent the vector that is perpendicular to the straight line that represents the one detected in the parameter space of the image. To formulate the model of the line to display, the only thing to consider is that if the slope of the vector is defined by *m* = *p*[*y*]/*p*[*x*], considering that *p*[*y*] and *p*[*x*] are its vertical and horizontal projection, respectively, the slope of the line detected, which is the normal to this vector, will be the inverse and opposite to that of the vector (−*p*[*x*]/*p*[*y*]). [Figure 6.11](#C_009_c6.xhtml#f6_11) shows an illustration of this process.

![FIGURE 6.11 Slope of the detected line, which is the inverse and opposite to that of the vector defined by the parameters of the Hough Transform.](images/Fig06_11.jpg)

[**FIGURE 6.11**](#C_009_c6.xhtml#f6_11b) Slope of the detected line, which is the inverse and opposite to that of the vector defined by the parameters of the Hough Transform.

It is important to mention that the images contained in [Figure 6.9](#C_009_c6.xhtml#f6_9) were obtained by executing [Program 6.1](#C_009_c6.xhtml#p6_1), in which what is described by the code can be observed graphically.

## 6.5 Line Detection Using MATLAB Functions

MATLAB contains 3 functions: `hough`, `houghpeaks`, and `houghlines,` which, when applied sequentially, allow the detection of lines in an image [[7](#C_009_c6.xhtml#r6_7)\]. The core of these functions is represented by the Hough transform implemented in the Hough function, while the other two `houghpeaks` and `houghlines` are used as helper detection and display functions.

As explained, this set of functions must be used sequentially for a line detection application. The operations performed by each of these functions correspond to the parts into which [Program 6.1](#C_009_c6.xhtml#p6_1) was divided, coding in MATLAB for the same functionality.

The `hough` function implements the Hough Transform, generating the array of accumulation registers; the `houghpeaks` function determines the registers whose maximum value defines the parameters of the detected lines; and finally, the `houghlines` function allows displaying the lines found by the combination of the `hough` and `houghpeaks` functions.

The `hough` function allows calculating the Hough Transform on a binary image that, as a prerequisite, contains the edges of an image. The syntax of this function is:

```
[H, theta, rho] = hough(BW);
```

where `BW` is a binary image containing the edges. The function returns 3 different values that are `H`, which contains the array of accumulator registers, and two vectors `theta` and `rho` that contain information on how linearly the parameters *r* and *θ* were divided in the array of accumulator registers of `H`.

When the Hough function is used with the syntax shown, it linearly divides the parameters *r* and *θ*, into 1997 values for the parameter *r* and 180 for the value of *θ*. So, the size of the accumulation records matrix will be 1997 × 180. The resolution of `rho` depends, as shown in Equation 6.9, on the size of the image, while that of `rho` is 1 degree, since there are 180 different indices to represent 180 degrees.

The `houghpeaks` function allows you to locate the maximum values of the array of accumulation registers. The syntax of this function is:

```
peaks = houghpeaks(H, numpeaks, ‘Threshold’, val);
```

where `H` is the accumulator record array computed by the `hough` function. The value `numpeaks` is a scalar that specifies the number of maximum values to identify in `H`. If the value of `numpeaks` is omitted in the syntax, the default value is 1. `‘Threshold’` is a scalar that specifies the threshold from which the `H` values are considered maximum. A simple way to determine a threshold that is correct and suitable for the accumulation record array is to use a proportional part of the maximum value found. An example is represented by the expression 0.5\*max(H(:)), which implies that the defined threshold is 50% of the maximum value register.

The function `houghpeaks` obtains as a result a matrix of dimensions *Q* × 2, where *Q* is a value from 0 to `numpeaks` (maximum value to identify) and 2 implies the indices corresponding to the parameters *r* and *θ* that define the accumulator register found as maximum.

The `houghlines` function extracts the lines associated with the `BW` image calculated by the Hough Transform, implemented from the combination of the `hough` and `houghpeaks` functions. The syntax of this function is defined by:

```
lines = houghlines(BW, theta, rho, peaks);
```

where `BW` is the binary image in which the lines were detected through the Hough Transform, `theta` and `rho` are the vectors that define the way in which the accumulating records matrix was linearly divided and, at the same time, both calculated by the function `hough`. On the other hand, `peaks` is a matrix that was calculated by the `houghpeaks` function of dimension *Q* × 2, where *Q* is the number of lines detected and 2 are the indices corresponding to the parameters *r* and *θ*.

The `houghlines ` function returns, as a result, an array of structures called `lines`. A structure is a grouping of data of different types under the same name. These data are called fields and are accessed using the format:

```
Name_of_the_structure.field1=3;
```

So, in the example above, field1, part of the structure `Name_of_the_structure` was assigned the value of 3. An array of structures is a set of index-driven structures that can be accessed using the format

```
Name_of_the_structure(1).field1=3;
```

where the value in parentheses refers to a structure identified by index 1.

The fields that the `lines` structure has are `point1`, `point2`, `theta`, and `rho`. Their meanings are summarized in Table 6.2.

### 6.5.1 Example of Line Detection Using MATLAB Functions

At the end of this section, an example is established that integrates the way in which the functions of the MATLAB image processing toolbox, described above, are used for the detection of lines in an image.

Considering as image `Im` to which it is desired to extract its lines as the one shown in [Figure 6.12a](#C_009_c6.xhtml#f6_12), its edges are extracted by applying the function:

![FIGURE 6.12 Detected lines by using the Hough transform method. (a) original image and (b) detected lines.](images/Fig06_12.jpg)

[**FIGURE 6.12**](#C_009_c6.xhtml#f6_12b) Detected lines by using the Hough transform method. (a) original image and (b) detected lines.

```
BW = edge(Im,’canny’,0.1,0.1);
```

Resulting in image 6.12b. In this image, the Hough transform is applied by executing the function:

```
[H, theta, rho] = hough(BW);
```

To be able to graph the array of accumulation registers `H`, we will first have to convert this array from type `double` to type `uint8`, writing:

```
Hu=uint8(H);
```

to then make the graph by executing the following sequence:

```
imshow(Hu,[],’XData’,theta,’YData’,rho,’InitialMagnification’,’fit’);
```

where the values of the `‘XData’` and `‘YData’` parameters replace the normal indices of the `Hu` matrix and the combination of the `‘InitialMagnification’` and `‘fit’` parameters allow the full-scale image of the window containing the graph to be displayed. The result is shown in [Figure 6.13](#C_009_c6.xhtml#f6_13). You can also improve the deployment by using the command:

![FIGURE 6.13 The matrix of the accumulator records of the Hough parameter space corresponding to the original image of Figure 6.12(a)](images/Fig06_13.jpg)

[**FIGURE 6.13**](#C_009_c6.xhtml#f6_13b) The matrix of the accumulator records of the Hough parameter space corresponding to the original image of [Figure 6.12(a)](#C_009_c6.xhtml#f6_12)

```
axis on, axis normal
```

by applying the function:

```
P = houghpeaks(H,8,’threshold’,ceil(0.3*max(H(:))));
```

At most, the 8 points with the highest value of the accumulation record matrix `H` are obtained, considering 30% of the maximum value found as the threshold. In order to display the maximum points found in the accumulation matrix, the following command sequence is executed:

```
hold on
x = theta(P(:,2));
y = rho(P(:,1));
plot(x,y,’s’);
```

which allows retaining the image to place objects on it and obtain the vectors of the `x` and `y` coordinates of the maximum points. The image obtained by the previous sequence is shown in [Figure 6.13](#C_009_c6.xhtml#f6_13).

Lastly, the lines corresponding to those of the parameters found by means of the `houghlines` function are obtained. However, since placing all the found line segments presupposes doing so by a repeat method, an .m file is programmed that allows finding the line segments and displaying the lines one by one on the `BW` border image. The .m file is shown encoded in [Program 6.2](#C_009_c6.xhtml#p6_2) ([Figure 6.14](#C_009_c6.xhtml#f6_14)).

![FIGURE 6.14 Image of edges, on which the line segments found by the combination of the hough, houghpeaks, and houghlines functions are placed. For the display of the lines, the code shown in Program 6.2 was used.](images/Fig06_14.jpg)

[**FIGURE 6.14**](#C_009_c6.xhtml#f6_14b) Image of edges, on which the line segments found by the combination of the hough, houghpeaks, and houghlines functions are placed. For the display of the lines, the code shown in [Program 6.2](#C_009_c6.xhtml#p6_2) was used.

## References

1.  [Duan](#C_009_c6.xhtml#r6_1b), D., Xie, M., Mo, Q., Han, Z., & Wan, Y. (2010). An improved Hough transform for line detection. In 2010 International Conference on Computer Application and System Modeling (ICCASM 2010) (Vol. 2, pp. V2–354). IEEE.
2.  [Illingworth](#C_009_c6.xhtml#r6_2b), J., & Kittler, J. (1988). A survey of the Hough transform. *Computer vision, graphics, and image processing*, 44(1), 87–116.
3.  [Kiryati](#C_009_c6.xhtml#r6_3b), N., Eldar, Y., & Bruckstein, A. M. (1991). A probabilistic Hough transform. *Pattern Recognition*, 24(4), 303–316.
4.  [Ballard](#C_009_c6.xhtml#r6_4b), D. H. (1981). Generalizing the Hough transform to detect arbitrary shapes. *Pattern Recognition*, 13(2), 111–122.
5.  [Hassanein](#C_009_c6.xhtml#r6_5b), A. S., Mohammad, S., Sameer, M., & Ragab, M. E. (2015). *A survey on Hough transform, theory, techniques and applications*. arXiv preprint arXiv:1502.02160.
6.  [Russ](#C_009_c6.xhtml#r6_6b), J. C. (2011). *The image processing handbook* (6th ed.). CRC Press.
7.  [McAndrew](#C_009_c6.xhtml#r6_7b), A. (2017). *Introduction to digital image processing with MATLAB*. CRC Press. 

# *Index*

*   accumulation records matrix [*187*](#C_009_c6.xhtml#f6_5), [187](#C_009_c6.xhtml#p187), [*188*](#C_009_c6.xhtml#f6_6)
*   algorithm, labeling [130–132](#C_007_c4.xhtml#p130)
*   alpha blending operation [33](#C_004_c1.xhtml#p33), [*34*](#C_004_c1.xhtml#f1_30)

*   Beaudet detector [173–174](#C_008_c5.xhtml#p173), [*182*](#C_008_c5.xhtml#f5_10) 
    *   location of corner points [*176*](#C_008_c5.xhtml#f5_7)
    *   MATLAB, implementation in [174–175](#C_008_c5.xhtml#p174)
*   binary filter [80–87](#C_005_c2.xhtml#p80) 
    *   image used to exemplify operation [*80*](#C_005_c2.xhtml#f2_36)
    *   MATLAB, implementation in [82–87](#C_005_c2.xhtml#p82)
    *   operation [*80*](#C_005_c2.xhtml#f2_36)
    *   processing window used [*80*](#C_005_c2.xhtml#f2_36)
    *   rebuild\_black\_corners function [85–87](#C_005_c2.xhtml#p85)
    *   rebuild\_white\_corners function [84–85](#C_005_c2.xhtml#p84)
    *   remove\_black\_noise function [82](#C_005_c2.xhtml#p82)
    *   remove\_white\_point\_noise function [83](#C_005_c2.xhtml#p83)
*   binary images 
    *   features of objects [156–158](#C_007_c4.xhtml#p156)
    *   labeling of objects [129–138](#C_007_c4.xhtml#indx-term21)
    *   object borders in [138–151](#C_007_c4.xhtml#indx-term22)
    *   optimal threshold [119](#C_007_c4.xhtml#p119)
    *   Otsu algorithm [120–123](#C_007_c4.xhtml#p120)
    *   representation of objects [151–155](#C_007_c4.xhtml#p151)
    *   segmentation [114–115](#C_007_c4.xhtml#p114)
    *   thresholding [116–118](#C_007_c4.xhtml#p116)
*   Boolean equations [80](#C_005_c2.xhtml#indx-term28)
*   bounding box [158](#C_007_c4.xhtml#p158)
*   box filter [44](#C_005_c2.xhtml#p44), [*44*](#C_005_c2.xhtml#f2_8)
*   brightness histograms [12–13](#C_004_c1.xhtml#indx-term42), [*13*](#C_004_c1.xhtml#f1_13)
*   brightness of an image [2–3](#C_004_c1.xhtml#p2)

*   Canny filter [111–112](#C_006_c3.xhtml#p111) 
    *   algorithm applied to an image [*112*](#C_006_c3.xhtml#f3_18)
    *   MATLAB tools that implement [112–113](#C_006_c3.xhtml#p112)
*   chain code [152–154](#C_007_c4.xhtml#p152), [*153*](#C_007_c4.xhtml#f4_24)
*   colfilt function [78–79](#C_005_c2.xhtml#p78)
*   color component histograms [13](#C_004_c1.xhtml#indx-term137)
*   color image histogram 
    *   brightness histograms [12–13](#C_004_c1.xhtml#indx-term42), [*13*](#C_004_c1.xhtml#f1_13)
    *   color component histograms [13](#C_004_c1.xhtml#indx-term137)
*   compaction [158](#C_007_c4.xhtml#p158)
*   Compass operators [96–98](#C_006_c3.xhtml#indx-term46)
*   contour identification 
    *   MATLAB, algorithm for combining contour identification and object labeling in [145–151](#C_007_c4.xhtml#p145), [*146*](#C_007_c4.xhtml#f4_21)
    *   and object labeling combination [139–145](#C_007_c4.xhtml#p139), [*140*](#C_007_c4.xhtml#f4_19)
*   contrast of image [2–3](#C_004_c1.xhtml#p2)
*   corner detection 
    *   Beaudet detector [173–176](#C_008_c5.xhtml#p173)
    *   corners in an image [160–161](#C_008_c5.xhtml#p160)
    *   Harris algorithm [161–168](#C_008_c5.xhtml#p161)
    *   Kitchen & Rosenfield detector [176–178](#C_008_c5.xhtml#p176)
    *   MATLAB, corner points determination using [168–172](#C_008_c5.xhtml#p168)
    *   other corner detectors [173–182](#C_008_c5.xhtml#indx-term57)
    *   Wang & Brady detector [178–182](#C_008_c5.xhtml#p178), [*181*](#C_008_c5.xhtml#f5_9), [*182*](#C_008_c5.xhtml#f5_10)
*   corners 
    *   advantages of [160](#C_008_c5.xhtml#indx-term61)
    *   in an image [160–161](#C_008_c5.xhtml#indx-term62)
    *   defined [160](#C_008_c5.xhtml#p160)
    *   detection (*see* [corner detection](#Z_010_index.xhtml#idx46))
*   correlation 
    *   linear convolution and [48–49](#C_005_c2.xhtml#indx-term65)
    *   one-dimensional correlation operation [*67*](#C_005_c2.xhtml#f2_25)
    *   size and convolution [66–68](#C_005_c2.xhtml#p66), [*71*](#C_005_c2.xhtml#f2_29)
*   cumulative histogram [18–19](#C_004_c1.xhtml#p18)

*   Delta Dirac function [52–54](#C_005_c2.xhtml#p52), [*53*–*54*](#C_005_c2.xhtml#f2_13)
*   difference filters [46–47](#C_005_c2.xhtml#indx-term209)
*   differential chain code [154](#C_007_c4.xhtml#p154)

*   edge detection 
    *   borders and contours [89–90](#C_006_c3.xhtml#indx-term74)
    *   filters for [92–104](#C_006_c3.xhtml#p92)
    *   gradient-based techniques [90–92](#C_006_c3.xhtml#indx-term76)
*   equalizing histogram using MATLAB [27–30](#C_004_c1.xhtml#p27)

*   features, of binary objects [156](#C_007_c4.xhtml#p156) 
    *   area [157](#C_007_c4.xhtml#p157)
    *   bounding box [158](#C_007_c4.xhtml#p158)
    *   compaction and roundness [158](#C_007_c4.xhtml#p158)
    *   geometric [156](#C_007_c4.xhtml#p156)
    *   perimeter [156–157](#C_007_c4.xhtml#p156)
*   filters [36–38](#C_005_c2.xhtml#indx-term84) 
    *   binary (*see* [binary filter](#Z_010_index.xhtml#idx8))
    *   Canny (*see* [Canny filter](#Z_010_index.xhtml#idx31))
    *   Laplacian (*see* [Laplacian filter](#Z_010_index.xhtml#idx169))
    *   linear (*see* [linear filters](#Z_010_index.xhtml#idx182))
    *   linear spatial filters in MATLAB (*see* [linear spatial filters in MATLAB](#Z_010_index.xhtml#idx83))
    *   MATLAB, operation calculation in [41–43](#C_005_c2.xhtml#p41)
    *   matrix [39](#C_005_c2.xhtml#p39)
    *   operation [39–40](#C_005_c2.xhtml#p39), [*40*](#C_005_c2.xhtml#f2_4)
    *   separability [51–52](#C_005_c2.xhtml#p51)
    *   spatial non-linear (*see* [spatial non-linear filters](#Z_010_index.xhtml#idx337))
*   filter separability 
    *   Gaussian filter separation [52](#C_005_c2.xhtml#p52)
    *   x-y separation [51–52](#C_005_c2.xhtml#p51)
*   formal characteristics of linear filters [47–48](#C_005_c2.xhtml#indx-term98) 
    *   filter separability [51–52](#C_005_c2.xhtml#p51)
    *   impulse response [52–54](#C_005_c2.xhtml#p52)
    *   linear convolution and correlation [48–49](#C_005_c2.xhtml#p48)
    *   linear convolution properties [49–51](#C_005_c2.xhtml#indx-term102)
*   Fourier descriptors [155](#C_007_c4.xhtml#indx-term349)
*   Freeman code [152–154](#C_007_c4.xhtml#p152), [*153*](#C_007_c4.xhtml#f4_24)

*   gamma correction 
    *   described [22](#C_004_c1.xhtml#p22)
    *   gamma function [23–24](#C_004_c1.xhtml#p23)
    *   illumination function [*22*](#C_004_c1.xhtml#f1_22)
    *   principle of [*24*](#C_004_c1.xhtml#f1_24)
    *   use of [24](#C_004_c1.xhtml#indx-term110)
*   Gaussian filter [44–46](#C_005_c2.xhtml#p44), [167](#C_008_c5.xhtml#p167) 
    *   implementation of smoothing 3 × 3 filter in MATLAB [45–46](#C_005_c2.xhtml#p45)
    *   separation [52](#C_005_c2.xhtml#p52)
    *   for smoothing [*45*](#C_005_c2.xhtml#f2_9)
*   gradient-based techniques [90–91](#C_006_c3.xhtml#indx-term116) 
    *   derived filter [92](#C_006_c3.xhtml#p92)
    *   first derivative in one-dimensional case obtained [*90*](#C_006_c3.xhtml#f3_2)
    *   partial derivative and gradient [91–92](#C_006_c3.xhtml#p91)

*   Harris algorithm 
    *   algorithm implementation [165–168](#C_008_c5.xhtml#p165)
    *   application of [*168*](#C_008_c5.xhtml#f5_5)
    *   corner points determination [164](#C_008_c5.xhtml#p164), [*165*](#C_008_c5.xhtml#f5_3)
    *   corner value function *(V)* [163–164](#C_008_c5.xhtml#indx-term124), [*164*](#C_008_c5.xhtml#f5_2)
    *   eigenvalues and eigenvectors calculation [162–163](#C_008_c5.xhtml#p162), [*163*](#C_008_c5.xhtml#f5_1)
    *   filtering of matrix of structures [162](#C_008_c5.xhtml#p162)
    *   location of corner points [*172*](#C_008_c5.xhtml#f5_6)
    *   MATLAB implementation of [168–172](#C_008_c5.xhtml#indx-term130)
    *   matrix of structures [161](#C_008_c5.xhtml#indx-term131)
*   Hessian matrix [173](#C_008_c5.xhtml#p173)
*   histeq function [30](#C_004_c1.xhtml#p30), [*31*](#C_004_c1.xhtml#f1_27)
*   histogram 
    *   auto-contrast operation [*15*–*17*](#C_004_c1.xhtml#f1_15)
    *   automatic contrast adjustment [15–18](#C_004_c1.xhtml#p15)
    *   color component histograms [13](#C_004_c1.xhtml#indx-term137), [*14*](#C_004_c1.xhtml#f1_14)
    *   color image (*see* [color image histogram](#Z_010_index.xhtml#idx37))
    *   cumulative [18–19](#C_004_c1.xhtml#p18)
    *   described [7–8](#C_004_c1.xhtml#p7)
    *   grayscale image [*7*](#C_004_c1.xhtml#f1_7)
    *   histeq function [30](#C_004_c1.xhtml#p30), [*31*](#C_004_c1.xhtml#f1_27)
    *   image acquisition characteristics [8–11](#C_004_c1.xhtml#indx-term145)
    *   image dynamics and effects [*12*](#C_004_c1.xhtml#f1_12)
    *   linear equalization [19–21](#C_004_c1.xhtml#p19), [*20*–*21*](#C_004_c1.xhtml#f1_20)
    *   MATLAB, calculation by [11–12](#C_004_c1.xhtml#p11)
    *   pixel operations effects on [13–14](#C_004_c1.xhtml#p13), [*15*](#C_004_c1.xhtml#f1_15)
    *   vector of [*8*](#C_004_c1.xhtml#f1_8)
*   Hough transform method [184–185](#C_009_c6.xhtml#p184) 
    *   accumulation records matrix [*187*](#C_009_c6.xhtml#f6_5), [187–188](#C_009_c6.xhtml#p187)
    *   fundamental idea [*188*](#C_009_c6.xhtml#f6_6)
    *   implementation [190–191](#C_009_c6.xhtml#p190), [*192*](#C_009_c6.xhtml#f6_9)
    *   MATLAB, encoding in [191–197](#C_009_c6.xhtml#p191)
    *   parameter space [185–187](#C_009_c6.xhtml#p185)
    *   parametric model change [188–190](#C_009_c6.xhtml#p188), [*189*](#C_009_c6.xhtml#f6_7)

*   illumination, of image [2–3](#C_004_c1.xhtml#p2)
*   imadjust function [26](#C_004_c1.xhtml#p26), [*27*](#C_004_c1.xhtml#f1_25)
*   image acquisition characteristics of histogram [8](#C_004_c1.xhtml#p8) 
    *   contrast [9](#C_004_c1.xhtml#p9), [*11*](#C_004_c1.xhtml#f1_11)
    *   dynamics [9–11](#C_004_c1.xhtml#indx-term169)
    *   lighting [9](#C_004_c1.xhtml#p9)
    *   lighting errors detected [*10*](#C_004_c1.xhtml#f1_10)
*   impulse response of filter [52–54](#C_005_c2.xhtml#p52), [*53*–*54*](#C_005_c2.xhtml#f2_13)
*   initial pixel or seed pixel [124–125](#C_007_c4.xhtml#p124)
*   intensity value change in pixel 
    *   contrast and illumination or brightness [2–3](#C_004_c1.xhtml#indx-term175), [*3*](#C_004_c1.xhtml#f1_2)
    *   image complement [4–5](#C_004_c1.xhtml#p4), [*5*](#C_004_c1.xhtml#f1_4)
    *   result delimitation by pixel operations [3–4](#C_004_c1.xhtml#p3)
    *   segmentation by threshold [5–6](#C_004_c1.xhtml#p5), [*6*](#C_004_c1.xhtml#f1_5)
*   isotropic property [44](#C_005_c2.xhtml#p44), [45](#C_005_c2.xhtml#p45)

*   Kirsch operator [97](#C_006_c3.xhtml#p97)
*   Kitchen & Rosenfield detector [176](#C_008_c5.xhtml#p176), [*182*](#C_008_c5.xhtml#f5_10) 
    *   location of the corner points [*178*](#C_008_c5.xhtml#f5_8)
    *   MATLAB, implementation in [176–178](#C_008_c5.xhtml#p176)

*   LabelOutlineCombination process [141–143](#C_007_c4.xhtml#p141) 
    *   NextNode function [141](#C_007_c4.xhtml#p141), [144–145](#C_007_c4.xhtml#p144)
    *   OutlineTrace function [141](#C_007_c4.xhtml#p141), [143–144](#C_007_c4.xhtml#p143)
*   Laplacian filter 
    *   application to improve sharpness of an image [*109*](#C_006_c3.xhtml#f3_16)
    *   calculation on an image [*106*](#C_006_c3.xhtml#f3_12)
    *   with extension of diagonal neighbors to central pixel [*107*](#C_006_c3.xhtml#f3_14)
    *   MATLAB use for implementation and sharpness enhancement [109–111](#C_006_c3.xhtml#p109)
    *   use of [*107*](#C_006_c3.xhtml#f3_14)
*   linear convolution 
    *   associativity property [50–51](#C_005_c2.xhtml#p50)
    *   commutativity property [50](#C_005_c2.xhtml#p50)
    *   and correlation [48–49](#C_005_c2.xhtml#indx-term201)
    *   linearity property [50](#C_005_c2.xhtml#p50)
    *   properties [49–51](#C_005_c2.xhtml#indx-term203)
*   linear equalization of histogram of an image [27](#C_004_c1.xhtml#p27), [28](#C_004_c1.xhtml#p28), [*29*](#C_004_c1.xhtml#f1_26)
*   linear filters [*40*](#C_005_c2.xhtml#f2_4) 
    *   box filter [44](#C_005_c2.xhtml#p44)
    *   difference filters [46–47](#C_005_c2.xhtml#indx-term209)
    *   formal characteristics [47–54](#C_005_c2.xhtml#indx-term210)
    *   Gaussian filter [44–46](#C_005_c2.xhtml#p44)
    *   smoothing filters [43](#C_005_c2.xhtml#indx-term374)
    *   types [43–47](#C_005_c2.xhtml#indx-term213)
*   linear spatial filters in MATLAB 
    *   correlation size and convolution [66–68](#C_005_c2.xhtml#p66), [*71*](#C_005_c2.xhtml#f2_29)
    *   functions for implementation [73–75](#C_005_c2.xhtml#p73)
    *   functions for non-linear spatial filtering [75–79](#C_005_c2.xhtml#p75)
    *   handling image borders [68–73](#C_005_c2.xhtml#indx-term218), [*72*–*73*](#C_005_c2.xhtml#f2_30)
    *   one-dimensional convolution operation [*70*](#C_005_c2.xhtml#f2_27)
    *   one-dimensional correlation operation [*67*](#C_005_c2.xhtml#f2_25), [*69*](#C_005_c2.xhtml#f2_26)
    *   rotation of kernel to apply convolution [*70*](#C_005_c2.xhtml#f2_27)
*   line detection 
    *   Hough transform (*see* [Hough transform method](#Z_010_index.xhtml#idx140))
    *   line segments and display lines one by one on BW edge image [201–202](#C_009_c6.xhtml#p201)
    *   MATLAB function, using [198–202](#C_009_c6.xhtml#p198), [*200*](#C_009_c6.xhtml#f6_12), [*201*](#C_009_c6.xhtml#f6_13)
    *   structures in image [183–184](#C_009_c6.xhtml#p183)
*   logical and arithmetic operations between images [30–31](#C_004_c1.xhtml#p30) 
    *   subtract [32](#C_004_c1.xhtml#p32), [*34*](#C_004_c1.xhtml#f1_30)
    *   sum [31–32](#C_004_c1.xhtml#p31), [*33*](#C_004_c1.xhtml#f1_29)
    *   AND y OR [32](#C_004_c1.xhtml#p32)
*   luminance histogram [13](#C_004_c1.xhtml#p13)

*   mask grid and its corresponding coordinate system [*39*](#C_005_c2.xhtml#f2_3)
*   MATLAB 
    *   adding noise to images with [55–58](#C_005_c2.xhtml#p55)
    *   Beaudet algorithm implementation in [174–175](#C_008_c5.xhtml#p174)
    *   binary filter implementation [82–87](#C_005_c2.xhtml#p82)
    *   borders determination of an image [100–101](#C_006_c3.xhtml#p100), [*102*](#C_006_c3.xhtml#f3_10)
    *   Canny filter, tools that implement [112–113](#C_006_c3.xhtml#p112)
    *   contour identification and object labeling, algorithm for combining [145–151](#C_007_c4.xhtml#p145)
    *   corner points determination using [168–172](#C_008_c5.xhtml#p168)
    *   edge detection with [98–101](#C_006_c3.xhtml#p98)
    *   filter operation calculation in [41–43](#C_005_c2.xhtml#p41)
    *   functions for edge detection [101–104](#C_006_c3.xhtml#p101)
    *   Harris algorithm, implementation of [169–171](#C_008_c5.xhtml#p169)
    *   Hough transform encoding [191–197](#C_009_c6.xhtml#p191)
    *   implementation of smoothing 3×3 filter in [45–46](#C_005_c2.xhtml#p45)
    *   Kitchen & Rosenfield algorithm implementation in [176–178](#C_008_c5.xhtml#p176)
    *   in Laplacian filter and sharpness enhancement [109–111](#C_006_c3.xhtml#p109), [*111*](#C_006_c3.xhtml#f3_17)
    *   linear spatial filters in [66–87](#C_005_c2.xhtml#indx-term255)
    *   line detection using functions of [198–202](#C_009_c6.xhtml#p198), [*200*](#C_009_c6.xhtml#f6_12), [*201*](#C_009_c6.xhtml#f6_13)
    *   object labeling algorithm using [135–138](#C_007_c4.xhtml#p135), [*138*](#C_007_c4.xhtml#f4_17)
    *   pixel operations (*see* [MATLAB pixel operations](#Z_010_index.xhtml#idx229))
*   MATLAB pixel operations [24–25](#C_004_c1.xhtml#indx-term262) 
    *   command line functions [11–12](#C_004_c1.xhtml#indx-term263)
    *   command line segmentation [25–26](#C_004_c1.xhtml#p25)
    *   contrast adjustment [26](#C_004_c1.xhtml#p26)
    *   contrast and illumination [25](#C_004_c1.xhtml#p25)
    *   histogram equalization using [27–30](#C_004_c1.xhtml#p27)
    *   imadjust function [26](#C_004_c1.xhtml#p26), [*27*](#C_004_c1.xhtml#f1_25)
    *   segmenting image by thresholding [25–26](#C_004_c1.xhtml#p25)
*   median filter [61–63](#C_005_c2.xhtml#p61), [*63*](#C_005_c2.xhtml#f2_21) 
    *   effect of [*63*](#C_005_c2.xhtml#f2_21)
    *   with multiplicity window [63–65](#C_005_c2.xhtml#p63)
    *   results and comparison of effect [*64*](#C_005_c2.xhtml#f2_23)
*   Mexican hat [46](#C_005_c2.xhtml#p46), [*47*](#C_005_c2.xhtml#f2_10)
*   multi-source pixel operations 
    *   alpha blending operation [33](#C_004_c1.xhtml#p33), [*34*](#C_004_c1.xhtml#f1_30)
    *   logical and arithmetic operations [30–33](#C_004_c1.xhtml#indx-term280), [*33*](#C_004_c1.xhtml#f1_29), [*34*](#C_004_c1.xhtml#f1_30)

*   NextNode function [141](#C_007_c4.xhtml#p141), [144–146](#C_007_c4.xhtml#p144), [149–151](#C_007_c4.xhtml#p149)
*   nlfilter function [76–78](#C_005_c2.xhtml#p76)
*   non-linear spatial filtering 
    *   colfilt function [78–79](#C_005_c2.xhtml#p78)
    *   MATLAB functions [75–79](#C_005_c2.xhtml#indx-term288)
    *   nlfilter function [76–78](#C_005_c2.xhtml#p76)

*   object borders in binary images [138](#C_007_c4.xhtml#indx-term290) 
    *   contour identification and object labeling combination [139–145](#C_007_c4.xhtml#p139), [*140*](#C_007_c4.xhtml#f4_19)
    *   external and internal contours [138–139](#C_007_c4.xhtml#indx-term293), [*139*](#C_007_c4.xhtml#f4_18), [*140*](#C_007_c4.xhtml#f4_19)
    *   MATLAB, algorithm for combining contour identification and object labeling in [145–151](#C_007_c4.xhtml#p145), [*146*](#C_007_c4.xhtml#f4_21)
*   object labeling in binary images 
    *   adjacent tagging [132–134](#C_007_c4.xhtml#p132)
    *   algorithm [130–132](#C_007_c4.xhtml#p130), [135–138](#C_007_c4.xhtml#p135)
    *   collision resolution (step 2) [134–135](#C_007_c4.xhtml#indx-term301)
    *   described [129](#C_007_c4.xhtml#p129)
    *   with four elements [*130*](#C_007_c4.xhtml#f4_13)
    *   MATLAB, implementation using [135–138](#C_007_c4.xhtml#p135), [*138*](#C_007_c4.xhtml#f4_17)
    *   propagation [132](#C_007_c4.xhtml#p132), [*133*](#C_007_c4.xhtml#f4_14)
    *   result of [*134*](#C_007_c4.xhtml#f4_15)
    *   temporary (step 1) [130–132](#C_007_c4.xhtml#indx-term309)
*   operator 
    *   based on second derivative [104–113](#C_006_c3.xhtml#p104)
    *   comparison for edge detection [105](#C_006_c3.xhtml#p105)
    *   defined [96](#C_006_c3.xhtml#p96)
*   optimal threshold [119](#C_007_c4.xhtml#p119)
*   Otsu method [120–123](#C_007_c4.xhtml#p120) 
    *   binarization of distribution of two overlapping classes, implementation for [122–123](#C_007_c4.xhtml#p122)
    *   results of [*124*](#C_007_c4.xhtml#f4_9)
    *   segmentation process of two distributions [*120*](#C_007_c4.xhtml#f4_8)
*   OutlineTrace function [141](#C_007_c4.xhtml#p141), [143–145](#C_007_c4.xhtml#p143), [148–149](#C_007_c4.xhtml#p148)

*   pixel operations [*36*](#C_005_c2.xhtml#f2_1) 
    *   described [1–2](#C_004_c1.xhtml#p1)
    *   Gamma Correction [22–30](#C_004_c1.xhtml#p22)
    *   histogram (*see* [histogram](#Z_010_index.xhtml#idx125))
    *   intensity value change [2–6](#C_004_c1.xhtml#p2)
    *   MATLAB (*see* [MATLAB pixel operations](#Z_010_index.xhtml#idx229))
    *   multi-source [30–34](#C_004_c1.xhtml#p30)
    *   representation [*1*](#C_004_c1.xhtml#f1_1)
*   Prewitt and Sobel operators in edge detection [104](#C_006_c3.xhtml#p104) 
    *   filter [93–94](#C_006_c3.xhtml#p93)
    *   gradient size and direction [94–96](#C_006_c3.xhtml#p94)

*   rebuild\_black\_corners function [85–87](#C_005_c2.xhtml#p85)
*   rebuild\_white\_corners function [84–85](#C_005_c2.xhtml#p84)
*   region growth segmentation method [123–124](#C_007_c4.xhtml#p123) 
    *   correspondence process between Matrix V and neighborhood [*125*](#C_007_c4.xhtml#f4_10)
    *   implementation of [128–129](#C_007_c4.xhtml#p128)
    *   initial pixel or seed pixel [124–125](#C_007_c4.xhtml#p124)
    *   local search [125–129](#C_007_c4.xhtml#p125)
    *   results of [*127*](#C_007_c4.xhtml#f4_12)
    *   store process of list L for an image [*126*](#C_007_c4.xhtml#f4_11)
*   region labeling [129](#C_007_c4.xhtml#p129)
*   remove\_black\_noise function [82](#C_005_c2.xhtml#p82)
*   remove\_white\_point\_noise function [83](#C_005_c2.xhtml#p83)
*   representation of binary objects [151](#C_007_c4.xhtml#indx-term345), [*151*](#C_007_c4.xhtml#f4_22) 
    *   chain code [152–154](#C_007_c4.xhtml#p152), [*153*](#C_007_c4.xhtml#f4_24)
    *   differential chain code [154](#C_007_c4.xhtml#p154)
    *   Fourier descriptors [155](#C_007_c4.xhtml#indx-term349)
    *   length encoding [152](#C_007_c4.xhtml#p152)
    *   shape numbers [154–155](#C_007_c4.xhtml#indx-term351)
*   results delimitation by pixel operations 
    *   homogeneous operations [3–4](#C_004_c1.xhtml#indx-term352), [*4*](#C_004_c1.xhtml#f1_3)
    *   image complement [4–5](#C_004_c1.xhtml#p4)
    *   segmentation by threshold [5–6](#C_004_c1.xhtml#p5), [*6*](#C_004_c1.xhtml#f1_5)
*   Roberts operator [96](#C_006_c3.xhtml#p96), [104](#C_006_c3.xhtml#p104) 
    *   diagonal components of [*97*](#C_006_c3.xhtml#f3_7)
    *   magnitude of the gradient considering [*97*](#C_006_c3.xhtml#f3_7)
*   roundness [158](#C_007_c4.xhtml#indx-term361)

*   second-derivative technique 
    *   Canny filter [111–112](#C_006_c3.xhtml#p111)
    *   edge detection using [105–107](#C_006_c3.xhtml#p105)
    *   Laplacian filter [106–107](#C_006_c3.xhtml#p106)
    *   operators based on [104–113](#C_006_c3.xhtml#p104)
    *   sharpness enhancement in images [*108*](#C_006_c3.xhtml#f3_15), [108–109](#C_006_c3.xhtml#indx-term367)
*   seed pixel [124–125](#C_007_c4.xhtml#p124)
*   segmentation technique 
    *   contextual techniques [115](#C_007_c4.xhtml#indx-term369)
    *   defined [114–115](#C_007_c4.xhtml#p114)
    *   non-contextual techniques [115](#C_007_c4.xhtml#indx-term371)
    *   by region growth [123–129](#C_007_c4.xhtml#p123)
    *   thresholding [115–118](#C_007_c4.xhtml#p115)
*   smoothing filters [43](#C_005_c2.xhtml#indx-term374)
*   Sobel operators [103](#C_006_c3.xhtml#indx-term375)
*   spatial filtering 
    *   application to an image [*41*](#C_005_c2.xhtml#f2_5)
    *   binary filter [80–87](#C_005_c2.xhtml#p80)
    *   filter [36–38](#C_005_c2.xhtml#p36)
    *   linear filters (*see* [linear filters](#Z_010_index.xhtml#idx182))
    *   linear filters types [43](#C_005_c2.xhtml#p43)
    *   MATLAB, adding noise to images with [55–58](#C_005_c2.xhtml#p55)
    *   MATLAB, calculation of filter operations in [41–43](#C_005_c2.xhtml#p41)
    *   process [*42*](#C_005_c2.xhtml#f2_6)
    *   spatial linear filters [38–40](#C_005_c2.xhtml#indx-term384)
    *   spatial non-linear filters [59–66](#C_005_c2.xhtml#indx-term385)
*   spatial non-linear filters 
    *   linear smoothing [59](#C_005_c2.xhtml#p59)
    *   maximum and minimum filters [59–61](#C_005_c2.xhtml#indx-term388), [*59*–*61*](#C_005_c2.xhtml#f2_18)
    *   median filter [61–63](#C_005_c2.xhtml#p61)
    *   multiplicity window, median filter with [63–65](#C_005_c2.xhtml#p63)
    *   other non-linear filters [65–66](#C_005_c2.xhtml#indx-term391)

*   thresholding 
    *   distribution of intensities of pixels [*116*](#C_007_c4.xhtml#f4_1)
    *   effect of using median filter on overlapped distributions [*118*](#C_007_c4.xhtml#f4_5)
    *   objects overlapping distributions [*117*](#C_007_c4.xhtml#f4_3)
    *   result of segmentation [*116*–*118*](#C_007_c4.xhtml#f4_1)

*   Wang & Brady detector [178–182](#C_008_c5.xhtml#p178), [*182*](#C_008_c5.xhtml#f5_10) 
    *   location of corner points [*181*](#C_008_c5.xhtml#f5_9)
    *   MATLAB, implementation in [180–181](#C_008_c5.xhtml#p180)

*   zero-crossing [105](#C_006_c3.xhtml#p105)