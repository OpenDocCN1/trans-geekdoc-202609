
The rest of this chapter is organized as follows: [Section 2](#B978032385209800002X.xhtml#s0015) discusses the literature review in detail; [Section 3](#B978032385209800002X.xhtml#s0020) details the proposed scheme; [Section 4](#B978032385209800002X.xhtml#s0025) gives the illustrative description; [Section 5](#B978032385209800002X.xhtml#s0030) details the experimental study and result analysis; [Section 6](#B978032385209800002X.xhtml#s0035) concludes the chapter.

## 2 Literature Review

RDH is an active area of research in the field of information security. RDH schemes allow us to hide some secret messages in digital content for secure transmission. At the receiving end, the original cover content can be recovered while extracting the hidden message. Existing RDH schemes are mainly used for the following two applications:

1.  **Medical image transmission**: In medical image transmission, RDH schemes are used to transmit patient records along with the medical image [[236]](#fn236).
2.  **Cloud service providers**: Cloud service providers use RDH schemes to hide some additional metadata information in the digital content uploaded by users to the cloud. Since the data uploaded by users should be returned to the cloud user as it is, the cloud service provider should not make any permanent changes to the uploaded data. In this case, the cloud service provider can use RDH schemes [[237]](#fn237).

Existing RDH schemes can be broadly classified into three categories:

1.  **RDH on natural images**: In the data hiding process, the data hider will change the original pixel values. Famous RDH schemes based on natural images are based on the concepts of histogram shifting, difference expansion, etc. Some other schemes are also available [[238]](#fn238).
2.  **RDH on encrypted images**: In this scheme, the data hider will get an encrypted image and will modify the encrypted pixels in the RDH process. There are mainly two methods of RDH on encrypted images: vacating room before encryption and vacating room after encryption [[239]](#fn239).
3.  **RDH through encryption**: In this scheme, RDH will take place in the process of encryption of the image. The RDH process will be fine-tuned so that data hiding in the encryption process is possible [[240]](#fn240).

In our proposed scheme, we have adopted the RDH through encryption scheme, where the face image captured by the camera is treated as the original image and the compressed fingerprint data is treated as the data. By using the RDH through encryption scheme, the fingerprint data will be embedded in the face image. Finally, we will get an encrypted image with a hidden message.

RDH through encryption was introduced in 2018. An overview of existing RDH through encryption schemes is given in [Table 1](#B978032385209800002X.xhtml#t0010).

**Table 1** Overview of existing RDH through encryption schemes.

| Scheme | Basic Method |
| :--- | :--- |
| Scheme [[241]](#fn241) | • Uses three different encryption and/or decryption keys.<br>• Can embed a single bit in a block of size B × B pixels.<br>• Entropy is used as a key metric for image recovery. |
| Scheme [[242]](#fn242) | • Uses three different encryption and/or decryption keys.<br>• Can embed a single bit in a block of size B × B pixels.<br>• Uses a trained Support Vector Machine model (SVM) for data extraction and image recovery. |
| Scheme [[243]](#fn243) | • Uses three different encryption and/or decryption keys.<br>• Can embed three bits in a block of size B × B pixels.<br>• Ensures 0 bit error rate in image recovery.<br>• Uses a trained Support Vector Machine model (SVM) for data extraction and image recovery. |

<div class="small_device"> <p class="table_fig"><img src="images/B978032385209800002X/t0010.png" alt="Table 1" /></p></div>

## 3 Proposed Scheme

This section details the proposed scheme. The scheme will be used for a biometric authentication system in which we use a cloud service provider to store the details of authenticated personnel. The proposed scheme adopts a two-level authentication scheme using face recognition and fingerprint recognition for authentication. During enrollment and authentication, the user's face image and fingerprint must be transmitted to cloud storage. To securely transmit biometric details such as face images and fingerprints, we have used the RDH through encryption process scheme. The proposed scheme uses an RDH through encryption scheme, which is very similar to the scheme reported in reference [[244]](#fn244).

| Step 1 | Capture a color face image using a camera |
| :--- | :--- |
| Step 2 | Capture a fingerprint using a fingerprint scanner |
| Step 3 | Convert the fingerprint image (grayscale) to its corresponding binary image |
| Step 4 | Apply run-length encoding to the binary fingerprint |
| Step 5 | Encode the run-length sequence using the Elias gamma coding process |
| Step 6 | Hide the compressed fingerprint details in the face image with the help of RDH through encryption to obtain an encrypted image with hidden data |
| Step 7 | Transmit the encrypted face image with fingerprint details to the cloud service provider |

One of the limitations of the RDH scheme is the low embedding rate. The fingerprint data is compressed to ensure that the RDH scheme does not face any difficulty in embedding the details in the face image. All three color planes (i.e., R, G, and B) are extracted separately from the face image, and each plane is processed separately while embedding the fingerprint data. Each color plane will be divided into non-overlapping blocks, and one bit of data from the compressed fingerprint details will be embedded in each block. The output of the data hiding phase will finally result in an encrypted image. The encrypted image can be securely transmitted to the cloud service provider for storage or authentication purposes. The cloud will process the received data and send an authentication control message back to the client to activate certain hardware modules, allowing the user to enter the restricted area. The sequence of operations at the sender side is given in Algorithm 1.

**Algorithm 1: Proposed Algorithm for Hiding Fingerprint Data in Face Image**

| Input | Face image F (RGB format), Fingerprint image P, and Encryption keys K[1] and K[2] |
| :--- | :--- |
| Output | Encrypted face image E with embedded compressed version of P |

| 1 | Convert P to its corresponding binary image by thresholding and retain in P. |
| 2 | Find the run-length encoding sequence L from the binary fingerprint image P. |
| 3 | Encode the run-length sequence L using the Elias gamma coding scheme to obtain P^c. |
| 4 | Find all three color planes R, G, and B from the given face image F. Let these three color planes be represented as F^R, F^G, F^B. |
| 5 | Generate two pseudo-random integer matrices M⁰ and M¹ based on encryption keys K[1] and K[2]. |

