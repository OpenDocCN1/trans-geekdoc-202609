
Random forest (RF) and DL-based approaches outperform the others among various classifiers. The performance is based on 55,000 training scenarios. In contrast to traditional DL-based systems, the dataset used in this experiment is relatively limited. The output of both the DL-based and RF classifiers improves as the training data grow. A DL-based classifier, on the other hand, usually outperforms other classifiers for large datasets, and it can be generalized for similar types of applications. For example, if a classifier is needed to detect the application used by TOR, only the output layer needs to be retrained, while the other layers will remain unchanged.

### 6.5: Web site defacement detection

Defacement attacks alter the content of a Web site and, as a result, modify the appearance of the Web site. It is one of the most significant threats to business, enterprise, and government Web sites and web applications. Deep-learning-based solutions can perform detection by constructing detection profiles from both regular and defaced web pages as training data [^(229)](#fn229)

## 7: Conclusion and future scope

On the one side, machine learning isn’t a magic bullet when it comes to defending the computer systems. There are undoubtedly numerous issues with interpretability, especially in the case of deep learning algorithms. However, with the increasing amount of data and dwindling number of experts, machine learning is the only solution. It works now and will be needed in the not-too-distant future. It’s best to get started right away. Another noteworthy point to mention is that hackers are increasingly using machine learning in their attacks.

The integration of AI and cyberspace security will present an increasing number of application scenarios as AI and cyberspace security evolve at a rapid pace. There are a range of exciting and open topics for integrated cyber protection and AI technologies in the future. The cascading relation of malicious activities during an attack life cycle should be considered in future research like breach, manipulation, and data theft. There are the different metrics that are used to assess the success of DL in cyber security tasks. However, since different datasets were used for training and research, a fair assessment of all of the different methods was impossible. As a result, benchmark datasets are important for advancing deep learning in the cyber security domain. As a result, the aim of this survey is to create a useful body of work that will enable researchers to advance the state of ML and DL for cyber security systems.

## References

# Chapter 11: A secure biometric authentication system for smart environment using reversible data hiding through encryption scheme

V.M. Manikandan ^()Computer Science and Engineering, SRM University-AP, Amaravati, Andhra Pradesh, India

## Abstract

Biometric authentication is used in its fullest potential in all smart environments. Face recognition and fingerprint recognition are the two most popular approaches for biometric authentication. In some places, where a higher level of security is required can be equipped with the combination of face recognition and fingerprint recognition. In general, from the client side, the biometric data will be collected using a camera and fingerprint scanner, and that information will be transmitted to a cloud service provider to do the complex tasks, such as face recognition and fingerprint recognition. In such situations, the transmission of face images and fingerprints from the client side to a server is a major concern since an intruder may try to grab that information, and later, they can use that information to control the authentication system. In this chapter, we discuss a secure mechanism to send the face images and the fingerprints with the aid of a reversible data hiding (RDH) through the encryption scheme. RDH is a process of hiding some data by using a concealing medium in such a way that later the extraction of the hidden message is possible along with the recovery of the original images. In a RDH through encryption scheme, the RDH process and the image encryption process will be combined into a single task to hide the secret message in an image. In this chapter, we propose a new model in which the compressed fingerprint data as a secret message will be embedded into the face image through a reversible data hiding through the encryption scheme. The encrypted image obtained after RDH through encryption will be transmitted to the cloud service provider for further processing.

### Keywords

Reversible data hiding; Biometric authentication; Cloud computing; Information security; Image encryption

## 1: Introduction

For the last few years, face recognition-based authentication systems are in various places to ensure the entry of authorized persons in the restricted places. Even nowadays, face recognition-based authentication in the Internet of things (IoT)-controlled smart homes are very common [^(230)](#fn230)

1.  Capture the image of a person using a digital camera
2.  Detect the face regions from the person images
3.  Compare the features of the detected face with the features in the database and identify the person.

Note that the features of the face images of authenticated people also should be stored securely and storing it on the client side will be difficult due to limited resources. These issues are solved by the prominent technology called cloud computing. There are lots of cloud service providers available now to provide a sufficient amount of storage and computational facility. So nowadays most of the people or companies are using cloud storage to keep the biometric data, such as face images [^(231)](#fn231)

There is a lot of research going on areas like face detection and face recognition. The main challenges in face recognition are the identification of faces from low lighting images, where some portion of faces may be occluded with some other objects, identification of faces with spectacles or cap, etc. [^(232)](#fn232)

Similar to the face recognition system, fingerprint recognition is a universally accepted biometric authentication scheme and is used in places to mark attendance in offices or to provide access to restricted places [^(233)](#fn233)

The combinations of fingerprint and face recognition can be used at the places where we need to provide a better level of security [^(234)](#fn234)

Data hiding is a widely studied area of research in the field of secure data transmission in the last three decades. In this scheme, a secret message will be concealed using a cover medium, and the cover medium can be any digital data, such as image, audio, and video.

In this chapter, we propose a new model for the secure transmission of face images and fingerprints by using a RDH through an encryption scheme [^(235)](#fn235)

![Fig. 1 The proposed framework.](images/B978032385209800002X/f11-01-9780323852098.jpg)

Fig. 1 The proposed framework.

The novelty of the proposed scheme is listed in the following:

*   The RDH scheme is introduced in the domain of biometric security.
*   The proposed scheme embeds the compressed fingerprint details in the face images during encryption. This ensures secure communication of fingerprints and protects the confidentiality of the face images.
*   We introduce the use of run-length encoding and Elias gamma encoding procedure for fingerprint compression.
