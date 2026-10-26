
As the possibility of obtaining real-time images. The technique proved useful in the assessment of soft-tissue architecture and perfusion because it provided pictures through the reflection of high-frequency sound waves through the tissues. Since ultrasound equipment was portable and did not use any radiation, it could be applied both for treatment and for diagnosis.

The effectiveness of these imaging techniques was boosted early on by the application of digital image processing in medicine. Digital radiography, which replaced older film-based procedures, did more than transfer, modify, and archive pictures. One of the outcomes of this shift was the invention of picture archiving and communication systems (PACS), which revolutionized how medical pictures are handled in healthcare organizations. Historically, the expansion of digital medical imaging systems created the foundation for more extensive subsequent advances in image processing and interpretation, including the incorporation of AI and machine learning into medical imaging systems.

All these developments can be described as a combined set that revolutionized the diagnostics of the human body by offering clinicians effective and efficient methods to visualize and analyze patients. The innovations of this period laid the foundation for the huge developments that are characteristic of imaging processes that have the capability to enhance medical research, diagnosis, and treatment.

## 2.2 The emergence of digital imaging

Another major advance in medical picture processing is the migration from analog to digital images; it shifted paradigms of how medical pictures are acquired, stored, and reviewed. This process began in the second half of the twentieth century due to gradual progress in computer technology and the realization of the disadvantages of an analog system.

Analog techniques dominated the early stages of imaging systems, but these systems suffered from problems such as image decay over time, the inability to duplicate images, and difficulties in processing and enhancing pictures. Such limitations were offset by the advent of the capability to digitize visible images based on the revolutionary concept of digital imaging as applied to medical imaging.

In the seventies, Sir Godfrey Hounsfield came up with perhaps one of the most important and initial steps towards digital imaging now known as CT. CT technology based on current computer algorithms used X-ray pictures taken from different angles and created cross-sectional images. This was one of the very first practical applications of digital image processing in the medical arena, demonstrating that the technique has the capability of providing more detailed and in-depth information than conventional methods of X-ray imaging.

In both the 1980s and 1990s, the technologies used for digital imaging improved significantly through the integration of MRI and advances in ultrasound imaging. The above modalities greatly profited from the manipulation of digital data.

- **Sobel and Prewitt operators:** First used in the 1960s, such operators were among the first to perform edge detection in images by highlighting areas with large differences in intensity. These simple edge detection methods serve as the foundation for advanced edge detection methods that are used to segment medical images and to extract features from the images.
- **Canny edge detector:** The Canny edge detector, designed in 1986, was superior to previous methods in that it used a multistage algorithm to detect all kinds of edges in noisy images. This algorithm is still one of the principal methods of image analysis for edge and structure detection in medical images.

### 2.3.1 Image filtering techniques for introductory courses

- **Gaussian filtering:** The method of using Gaussian filters for image smoothing and noise removal gained popularity in the 1970s. Gaussian filtering is used in medical imaging for preprocessing images in a way that noise is eliminated, allowing significant features to be readable.

![](img/18722240e44c225d7ff2f58a10eecb4a_172_0.png)

Figure 2: Milestones in image processing algorithms.

- **Median filtering:** Though initially employed as a reliable technique for eradicating salt-and-pepper noise from images, median filtering has recently found many applications in medical imaging, enhancing image quality without blurring edges.

### 2.3.2 A review of newer image segmentation techniques

- **Region growing and splitting:** The local region-based segmentation approach, including region growing/merging and region splitting, was developed in the 1970s and 1980s. These methods group images according to similarity measures defined by homogeneity criteria and prove useful for delineating structures in medical images.
- **Active contour models (snakes):** Active contour models, or snakes, introduced by Kass et al. in 1988, are among the most popular techniques for image segmentation; they minimize energy and allow a contour to evolve along object boundaries. They have been widely used in medical image segmentation, especially for the delineation of anatomical structures.

### 2.3.3 Improved methods of reconstruction

- **Filtered backprojection (FBP):** Among the developments that arose during the progress of CT, the FBP algorithm, which originated in the 1970s, is credited with offering a technique for reconstructing images from projection data. FBP continues to be widely used for this purpose in computerized tomography.
- **Iterative reconstruction techniques:** In the 1990s and 2000s, iterative reconstruction algorithms were introduced to address problems with clinical image quality and artifacts. These methods successively update the estimate of an image and are currently used in clinical practice to improve the accuracy of diagnoses.

### 2.3.4 Incorporation of basics of machine learning and deep learning

- **Early neural networks:** In the 1980s, artificial neural networks worked as feature extractors and for picture classification. This early work paved the way for future developments of more advanced machine learning techniques in medical imaging; however, their feasibility and use were quite limited at that time.
- **CNNs:** A tremendous innovation came in the late 1990s when LeCun et al. devised CNNs that improved image processing. The primary application of CNNs in modern medical image analysis owes much to their capacity to extract hierarchical features from pictures. Examples of applications of CNNs include functions such as image segmentation and classification, where they deliver the best performance.
- **GANs (generative adversarial networks):** Recent GANs, introduced by Goodfellow et al. in 2014, have provided the capability to create high-quality synthetic medical images and to perform data augmentation. The application of GANs for enhancing image quality and generating training data sets for machine learning models is on the rise.

These are the milestones in image processing algorithms that have significant relevance to the medical imaging field. All have evolved into sophisticated techniques to improve image quality, extract useful information and features, and, above all, enable better diagnosis, which in turn has made an impressive difference in healthcare solutions.

## 2.4 Key technological innovations

### 2.4.1 New developments in imaging hardware and sensor devices

The development of medical image hardware has gone through different stages; major changes in the kind and quality of images have led to improvements in diagnosis. These early imaging systems had poorly developed sensors or detectors that created limitations in sensitivity and/or resolution that hampered the work of a diagnostic system. The latest detectors have been developed with high-resolution and other innovative sensor technologies, which make the images clearer. Technologies such as digital radiography, which replaced conventional film-based technologies with digital sensors, have helped improve image quality and reduce radiation exposure, thereby improving the efficiency of the imaging process. In addition, the design of solid-state detectors and photostimulable phosphor plates has also enabled improved image acquisition and processing.

### 2.4.2 Use of GPUs to support image processing endeavors

Graphics processing units (GPUs) have been successfully introduced into medical image processing pipelines, and their addition has enhanced computational performance manyfold. Originally developed for graphics computations, these GPUs have a parallel processing structure that is amenable to the computations needed in medical imaging. Their use has increased throughput for processing large volumes of imaging data and for tasks such as image reconstruction, enhancement, and analysis. Technological advances in GPUs have helped realize complex algorithms, such as those used in deep learning, accelerating medical image analysis.
