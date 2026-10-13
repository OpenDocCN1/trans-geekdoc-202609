
# Watermarking Characteristics and Applications

It exhibits a number of watermarking characteristics [106] depicted in Figure 4.

**Robustness** is defined as algorithm capability to repel noise. **Security** refers to difficulty in altering or removing the watermark without destruction of cover image. **Data payload** refers to the amount of contained information. The **transparency** of watermark is resultant of imperceptibility. The **authentication framework** is main focus area of fragile watermark. The total cost in revealing and enclosing the watermark is defined as **computational watermark**. The other important features are defined in Singh, Kumar, Singh, & Mohan (2017).

| Figure 4. Various characteristics of watermark |
| --- |
| ![Figure978-1-7998-2701-6.ch004.f04](i/ch004.f04.png) |

## Watermark Applications

Different watermarking methods are used for different applications. These include digital forensic, copyright protection, health care, military, medical applications etc. as represented below (Vallabha, 2003; Kumar, Singh, & Kumar, 2018).

1.  **Copyright Protection**: The secret information is hidden for providing the copyright protection to digital information.
2.  **Broadcast monitoring**: It enables the proprietors to verify where, when and amount of time content is broadcast through satellite television and cable.
3.  **Fingerprinting**: The source of illegal distribution is traced by this method as it contains the intended recipient's identification information.
4.  **Medical Applications**: The method offers the confidentiality and authentication of medical data. It provides value added methods for health-care applications.
5.  **Electronic Voting System**: As the evolution in computer network, Internet reached worldwide. It is the method of scheduling the elections by security preference during elections. Due to rapid internet usage in the fields of shopping, banking, secured transactions is an important factor.
6.  **Remote Education**: Distance education is the most prevailing among villages. The smart technology needed for the remote education. Watermarking provided the authentication to distance learning data.
7.  **Security on Cloud**: As number of increasing images, content based image retrieval is considered. Amount of storage taken by images is more as compared text. So, cloud storage is an example (Xia et al., 2016).

The authentication for sensitive images is to be performed before transferring to another place. So, unique watermark is inserted by cloud server before sending an encrypted image to server. The unauthorized user is outlined when illegal image is found.

## Attacks on Watermarking

In the applications of watermarking, the data is treated in a way as it spreads the receiver of watermark (Sherekar, Thakare, & Jain, 2011). In the definition of watermarking, the attack is harming of unhidden secret information in the process of watermarking. Further, data attacked is described by watermarked data processed. The attacks are classified as:

1.  **Active Attacks**: In this type of attack, the watermark is removed by the hacker and it is made undetectable. The main aim is to distort the embedded watermark so that it may not be recognized. Examples are copy control, finger printing, copyright protection etc.
2.  **Passive Attacks**: The watermark is identified in passive kind of attack. The deletion or destruction is not performed. They play an important role in covert channels.
3.  **Forgery Attacks**: The new watermark is inserted by the hacker instead of removing the old watermark.
4.  **Collusion Attacks**: They are from active attacks. The number of instances of same information is used by the hacker where each instance consists of different marks, in order to build a duplicate copy without any mark.
5.  **Simple Attacks**: It can also be said as noise attack or waveform attack. This is one of the simplest attack as it embedded watermark is harmed without recognizing a single watermark. Examples are waveform based compression, addition of noise, gamma correction etc.
6.  **Ambiguity Attack**: This kind of attack confuse the user by generating fake original data or watermarked data. One of the example is inversion attack.
7.  **Cryptographic Attack**: The main goal in this attack is to break the security method in techniques of watermarking and finding the mode for removing the information of already inserted watermark. This technique has limited application due to high computational complexity.
8.  **Removal Attack**: Without hampering the security of watermark technique, watermarked data is completely removed (Voloshynovskiy, Pereira, Pun, Eggers, &Su, 2001). No key is used in embedding of watermark. It uses quantization and denoising.
9.  **Geometric Attack**: The main goal is to synchronization of watermark detection with the inserted information without removing the inserted watermark.

# REVIEW OF MULTIMEDIA WATERMARKING TECHNIQUES

## Digital Watermarking Techniques

Digital watermark is composed of various methods for protecting the digital data from being modified and also the unauthorized access to data. The watermarking techniques are categorized into transform and spatial domain. The embedding of watermarks is performed in spatial domain and functionality is performed on pixel (Singh, Sharma, Dave, & Mohan, 2012). The pixel values are altered in this technique. It mainly uses `LSB` technique for modification process. The main goal of transform domain technique is alteration of transform domain coefficient. The mainly used methods for watermarking in transform domain are `DFT`, `DWT` and `DCT`. The transform domain is much more effective then spatial domain technique due to security and robustness.

### Spatial Domain Watermarking

This technique depicts an image as a combination of pixels. In order to attach the watermark, colour value of pixels and pixel intensity is modified. They consume less amount of time and also exhibit less complexity. Each and every operation in this technique is simple but have the higher computational speed. These are comparatively less robust to attacks. In the `LSB` technique (Neeta, Snehal, & Jacobs, 2006), the embedding of watermarks is performed in least significant bit of arbitrarily selected pixels. It can easily be implemented over the images and the quality of an image is not disrupted. The main disadvantage is that non robustness to signal processing operations leading to depletion of watermarks due to attacks of signal processing. It withstands against simple attacks like addition of noise and cropping.

### Transform Domain Watermarking

In this method, no embedding of watermark is performed on cover image. In the first step, transformation of cover image is performed and then embedding of watermarks is performed to transformed image. In addition, for extraction of image inverse transform is calculated for manipulated coefficients (Akiyama, Motoyoshi, Uchida, & Nakanishi, 2006). These are robust against attacks such as JPEG compression. They are useful in robust watermarking for assuring the flexibility of watermark to most popular attacks of signal processing. Numerous transform watermarking techniques exist such as Singular Value Decomposition (`SVD`), Discrete Wavelet Transform (`DWT`), Discrete Cosine Transform (`DCT`) and Discrete Fourier Transform (`DFT`). These methods posses high imperceptibility, effective alterations to signal processing attacks and image alterations. The computation cost in this method is more in comparison to spatial domain based method.
