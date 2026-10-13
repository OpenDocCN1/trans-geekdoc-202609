
# Data Hiding or Information Hiding

Data hiding or information hiding is a general term that encompasses two sub-disciplines: steganography and watermarking.

**Steganography** is a process of transmitting secret information hidden in an innocent-looking cover medium so that its existence is undetectable. The secret information is always hidden in an unseen manner.

**Watermarking** is the process of imperceptibly altering the cover medium to embed information about the cover medium. Watermarking is closely related to steganography; however, there are differences between them. In watermarking, the secret information is related to the cover medium. Steganography relates to secret point-to-point communications between two parties where the secret information is not related to the cover medium. Watermarking has additional features: it must have resilience against attacks that attempt to remove the hidden secret information. Steganography does not have the notion of attacks because the secret information is not related to the cover and does not create any suspicion for attackers.

## Figure 3. A General Watermarking Model

![Figure978-1-7998-2701-6.ch006.f03](i/ch006.f03.png)

A general watermarking model is shown in Figure 3. It involves two processes: embedding and extraction. In this model, the cover medium is referred to as cover data (`I`) and can be text, audio, image, or video. The embedding process inserts the secret information, referred to as watermark (`W`), inside the cover data in an encrypted form using the key (`k`). The key can be either secret or non-secret. The output of the embedding process is composite data, referred to as watermarked data (`I[W]`), containing the encrypted secret information inside the cover data. This watermarked data may be attacked by hackers to destroy the embedded watermark, generating a hacked version of the watermarked data (`I[W]'`). Once the watermarked data is hacked, the cover data becomes susceptible to all kinds of fraud. The extraction process separates the cover data and watermark from the watermarked data. The watermark removed from the watermarked data is known as the extracted watermark (`W[E]`), called a confidence measure.

It is used for the verification and validation of the cover data. The extraction process may be carried out with or without knowledge of the cover data or watermark. Depending on the target application, the extraction process may be either lossy or lossless.

# History of Watermarking

Watermarking is not recent to this century. More than 700 years ago, watermarking was employed in Italy to represent the paper brand and mills that produced it. In the 18th century, watermarking began to be used for anti-counterfeiting measures on money and other documents (Muharemagic & Furht, 2004). The term "watermark" was introduced at the end of the 18th century. Since the marks resemble the effect of water on paper, the term "watermark" was chosen. In 1954, Emil Hembrook filed a patent for his identification towards digital watermarking in music. This was the first work carried out in digital watermarking and became an example. In 1988, Komatsu and Tominaga used the term "Digital Watermarking" for the first time in literature. Since 1995, interest in watermarking research started growing (Muharemagic & Furht, 2004; Cox, Miller, Linnartz & Kalker, 1999).

# Relevance of Watermarking in Medical Images

Medical Image Processing (MIP) refers to techniques used to create and manipulate images of the human body for clinical purposes. Clinical purposes include medical procedures seeking to reveal and diagnose disease. The field has research potential attempting to understand processes in humans or animal models. While general image processing techniques are used for medical images, they require special treatment due to their special nature. Medical images are derived from different acquisition methods such as X-Ray, Computed Tomography (CT), Magnetic Resonance Imaging (MRI), Ultra Sound Imaging, Nuclear Imaging, Fundus Imaging, etc. Hence, medical images differ based on acquisition methods. They also differ based on the subject whose images are being acquired. Medical images are processed to infer information about the volume under the skin, exclusively to probe the anatomy of hidden objects below the skin. Medical images can be either 2-D projection information or full 3-D mapped information. Medical image protection and authentication are important in an e-healthcare environment where all visual information and clinical records are stored and exchanged in digital form. Medical image watermarking is a process for enhancing information security, verification, and fidelity. At the same time, it is necessary to preserve as much original information as possible in the image to avoid performance loss for physicians.

# Security Features of Medical Images

The security of medical images is obtained from strict ethics and legislative rules which can be classified into three fixed characteristics: confidentiality, reliability, and availability (Dutta, Singh, Singh, Burget & Prinosil, 2015; Melkemi, Kamal, Singh & Golea, 2017; Hai, Dong Qing, & Ke, 2018; Sliwa, 2019).

## Confidentiality

It means that only entitled users have access to the images in the scheduled system.

## Reliability

It is given by two features:

1.  **Integrity**: Ensuring that the images have not been modified by an unauthorized person.
2.  **Authentication**: Ensuring that the image indeed belongs to the correct patient and is issued from the correct source.

## Availability

It is the capability of an image to be used by entitled users in the normal scheduled conditions of access and exercise.

In the case of medical image security, the first two characteristics mainly have to be considered. The watermarking scheme has been recognized to control image reliability by emphasizing its integrity and authenticity (Coatrieux, Maitre, Sankur, Rolland & Collorec, 2000). A digital watermark is a secret key-dependent signal inserted into digital data which can be later detected or extracted to make an assertion. In medical images, alterations due to the insertion process are not accepted by physicians for diagnosis. Therefore, the requirements in medical images differ from multimedia applications (Amato, Cozzolino, Mazzeo & Romano, 2018; Wang, Ding & Gu, 2019; Karmakar & Basu, 2019; Bhatt, 2017).

When medical images are exchanged in public or private networks, two main questions are raised:

1.  **Whose image is that?** It refers to the hospital which sends the image for diagnosis and associated patient details.
2.  **Is the received image genuine?** It refers to the authentication of the image.
3.  **Source verification**: It checks that the image is received from the proper source and ensures that it is not modified.

These questions can be answered using two different branches of application in watermarking schemes: copyright protection and authentication. Copyright protection protects the owner's intellectual property and traces the source of illegal copies of the content. Authentication checks whether the received image has been altered and localizes the tampered regions. Authentication is the first and basic step in any security architecture whose success prevents other issues in the systems.

This chapter focuses on developing a watermarking scheme for the authentication of Digital Fundus Image (DFI), a special class of medical images. The next few sections will discuss the significance of DFI and its security.

# Digital Fundus Image
