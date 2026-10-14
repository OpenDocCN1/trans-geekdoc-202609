
Source-based and destination-based watermarking. Source watermarking is required for ownership identification or authentication and is used where multiple copies of data are distributed and a unique watermark is used to recognize the owner and prevent the data from getting compromised. In case of illegal reselling/distributing of data/information, destination-based watermarking can be used. Hence, fingerprint watermarking is considered as an effective and accurate method to eliminate the issues regarding the security of data. In order to enhance the privacy of fingerprint data, watermarking techniques are an effective tool. It is kept in a BufferedImage where its pixels, RGB colors and other characteristics are preserved. In this process, extract image data and calculate the values of different characteristics by using BufferedImage. Then Color model object and Raster object are two parts of an image that is an object of BufferedImage. The Color model is used to extract pixel data of an image and translates it into color components i.e., red, green and blue in a computer. A rectangular array of pixels is represented by the Raster. After this, sample values are stored in a DataBuffer and to locate a sample value, a sample model can be used. Raw image data and sample model which describes organization of data in the buffer is held by a DataBuffer (Figure 29.3).

## 29.7 Mosaicking on Biometrics

### 29.7.1 Fingerprint Quality Improvement by Using Mosaicking Technique

#### 29.7.1.1 Introduction

It is evident that security systems and forensics are the main application areas of biometrics. Sometimes, it has been observed and found that it is not necessary to capture the fingerprints in a complete or perfect shape and size from the crime scenes or even from the scanners. Sometimes it is about the angle used to scan the image, carelessness of using the image acquisition devices, environment, climate conditions, injury on the fingertip or sweating that makes image acquisition of low quality or incomplete in nature. With the wrong angle, only a limited portion is being captured and that is the time when it becomes very complicated to use this as a measure of security. It is very difficult to identify an individual based on partial/incomplete impression. Mosaicking is the solution to this sort of condition where impartial data is being captured by image acquisition device. Also, it is a popular area of investigation among the researchers these days.

This method is used to provide authentic access and security to the data that needs to be protected. Fingerprint mosaicking algorithms provide accurate and precise solutions and address the issues related to biometric security, ensuring no loss in the quality of fingerprint impression and high performance can be achieved [38].

Two stages of fingerprint verification, i.e., enrollment stage and authentication stage, are the components of fingerprint identification systems. In the enrollment stage, fingerprint images are captured and saved in the database. Multiple images of the same fingerprint are stored during image acquisition stage so that the image from every angle can be captured, which can be used to ultimately design the composite image from various impressions and used in the future for verification of authentic user. In the authentication stage, stored fingerprint impressions are matched against the query template. Various applications used by commercial, financial and other sectors use solid-state sensors. And solid-state sensors are known for the acquisition of limited amount of ridges and valleys from the fingertip impression. This limited information acquired from fingertips is not sufficient for effective authentication. Thus, the performance of fingerprint identification system will get affected because the overlap region captured from the query image and stored impression is small and consists of fewer numbers of ridges and minutiae which increase the false rejection or genuine acceptance rates [37].

Fingerprint mosaicking is a perfect solution for this problem and it is designed in the form of a composite image by combining multiple impressions. This composite image of fingerprint generates more information and requires less space rather than storing multiple impressions, which is used to improve matching efficiency by reducing matching time.

Another reason for reduced acquisition performance of sensors is that they cover a small amount of area, which is why they do not provide sufficient information about the fingerprint impressions that is required. This also creates a negative impact over the identification efficiency. Fingerprint mosaicking is a technique used to create an approximation of an image from multiple dab images. These images are captured while user dabs (presses) the fingertip on the image acquisition device. If the rolled image is created from these dabbed images and after merging them, it improves fingerprint area and low quality fingerprint impressions.

Mosaicking can be classified as touch-based and touchless-based mosaicking. When the images are collected through the sensors where the fingerprint comes in the physical contact of a scanner. The fingertip actually needs to be swiped on the screen of sensors and then mosaicking will take place and composite template is created. Another type of mosaicking is touchless-based where fingerprint acquisition is done without physical contact. Rather than using the sensors to swipe the fingers, cameras and CCD are used to acquire the image. This way of image acquisition is used to avoid image deformations which are the results of non-uniform pressure, dirt or any other reason like this and provides better results than touch-based image acquisition (Figure 29.4).

The outcomes of both matching processes are compared and will be analyzed. An algorithm is demonstrated in the following steps:

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_891_0.png)

Figure 29.4 Block diagram of fingerprint mosaicking process.

#### 29.7.1.2 Fingerprint Mosaicking Algorithm

1. Two or more fingerprints of an image are acquired by acquisition devices to create a composite image.
2. Then apply fast Fourier transformation (FFT) and calculate conjugate of the result after FFT. Afterwards, calculate the parameters like height and width of images after mosaicking.
3. After mosaicking, load the image for further processing and save the mosaicked image in the database.
4. Then minutiae extraction of mosaicked fingerprint image will take place.
5. Minutiae extraction of query image will get processed.
6. Then comparing both the images, the matching algorithm will check the efficacy of the process.
7. Performance analysis of the process.

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_892_0.png)

Figure 29.5 GUI interface.

#### 29.7.1.3 Experimental Results

The following screenshots are representing the process of fingerprint mosaicking:

1. Graphical User Interface (Figure 29.5).
2. Fingerprint images are loaded (Figure 29.6).
3. Mosaicked image is generated (Figure 29.7).

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_892_1.png)

Figure 29.6 Loading fingerprint image in the axes.

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_893_0.png)

Figure 29.7 Mosaicked image.

4. After mosaicked image generation, it is saved in the database for matching process (Figure 29.8).
5. For template matching another GUI is called (Figure 29.9).
6. Query image and stored image are being compared and for that image is fetched from the database (Figure 29.10).

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_893_1.png)

Figure 29.8 Saving the mosaicked image.

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_894_0.png)

Figure 29.9 GUI for matching.

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_894_1.png)

Figure 29.10 Fingerprint image loaded for matching.

7. Histogram equalization of loaded fingerprint image is done (Figure 29.11).
8. FFT is performed on the image generated (Figure 29.12).
9. Binarization of the fingerprint image is done, i.e. it is being converted in the form of 0 and 1 (Figure 29.13).
