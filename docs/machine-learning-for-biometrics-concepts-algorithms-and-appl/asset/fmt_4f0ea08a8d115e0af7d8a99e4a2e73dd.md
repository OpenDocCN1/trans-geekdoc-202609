
$$\\mathit{CR} = \\frac{\\textit{Total\\ number\\ of\\ bits\\ in\\ the\\ original\\ fingerprint\\ image}}{\\textit{The\\ number\\ of\\ bits\\ in\\ the\\ compressed\\ fingerprint\\ image}}$$

![si1_e](images/B978032385209800002X/si1_e.png)

### 2. Security analysis
The randomness in the encrypted image is evaluated using entropy and histogram analysis.

### 3. Analysis of a histogram-based measure for classifying original image block and wrongly decrypted block

### A. Analysis of the compression ratio

In the proposed scheme, we have used the run-length encoded sequence and Elias gamma encoding procedure to compress a binary fingerprint image. The size of the fingerprint images in the SOCOFing dataset is 103 × 96, which needs 9888 bits in the original binary representation. The run-length encoding procedure makes use of the redundancy in the adjacent bits. For the 100 randomly selected images, the compression ratio obtained after the compression is graphically shown in [Fig. 3](#B978032385209800002X.xhtml#f0020).

### B. Security Analysis

![Fig. 3 Compression ratio obtained from 100 fingerprint images.](images/B978032385209800002X/f11-03-9780323852098.jpg)

**Fig. 3** Compression ratio obtained from 100 fingerprint images.

As per the proposed scheme, we can use any random stream generator for encryption purposes. For the simulation purpose, we have used the `RC4` random stream generator. The proposed scheme can use any secure random stream generator for encryption purposes. To analyze the security of the encryption process, we have used histogram analysis and entropy.

Four sample face images and the histograms of all those images are given in [Fig. 4](#B978032385209800002X.xhtml#f0025). To show that the final encrypted image that we have obtained after the RDH process is having enough randomness in pixel distribution, we have plotted the histograms of encrypted images, which are given in [Fig. 5](#B978032385209800002X.xhtml#f0030).

![Fig. 4 Original face images and their histograms.](images/B978032385209800002X/f11-04-9780323852098.jpg)

**Fig. 4** Original face images and their histograms.

![Fig. 5 Face images obtained after RDH through encryption process and the corresponding histograms.](images/B978032385209800002X/f11-05-9780323852098.jpg)

**Fig. 5** Face images obtained after RDH through encryption process and the corresponding histograms.

The entropy measure obtained from 50 randomly selected face images after the data hiding process is shown in [Fig. 6](#B978032385209800002X.xhtml#f0035). It can be seen that from all those images the entropy value after the encryption process is maximum (very close to 8) irrespective of the entropy from the original image. The `E1` measure shows the entropy of the original face image, and the `E2` indicates the entropy obtained after data hiding through the encryption process.

### C. Analysis of new histogram-based measure

![Fig. 6 Analysis of entropy measure from original image and encrypted image.](images/B978032385209800002X/f11-06-9780323852098.jpg)

**Fig. 6** Analysis of entropy measure from original image and encrypted image.

The key idea that we have used for data extraction and image recovery is a histogram-based measure. The peak value from the histogram is used to distinguish original image blocks from the wrongly recovered block. Note that at the cloud service provider's side, they know two different keys have been used by the users during the data hiding and image encryption process. Which stream cipher is used for encrypting a selected block is not known to the receiver. So they will create histograms of both the blocks that are obtained after attempting the encryption process and the histogram of the newly obtained blocks is analyzed. In a face image, there is a high probability that the pixels in a block are highly close in turn. To depict the reason to use the histogram-based measure to recover the image block, we have plotted the peak value observed from the correctly recovered image block (`OM`) and the wrongly recovered image block (`WM`).

From [Fig. 7](#B978032385209800002X.xhtml#f0040), it can be observed that always the measure is high from the correctly recovered block as compared to wrongly recovered blocks.

![Fig. 7 Histogram-based measure obtained during image recovery.](images/B978032385209800002X/f11-07-9780323852098.jpg)

**Fig. 7** Histogram-based measure obtained during image recovery.

The key observations during the experimental study are listed in the following:

*   The use of run-length encoding with Elias gamma encoding process ensures very good compression in the fingerprint data.
*   A new histogram measure is used in the proposed scheme to identify the correctly recovered block at the receiver side. This measure is working efficiently, and the experimental study claims that this measure is capable to distinguish the natural image block from the wrongly recovered decrypted block.
*   The comparative study of the proposed scheme is omitted since the RDH through encryption scheme to embed fingerprint details in face images is first introduced in this chapter.

## 6: Conclusion

In this chapter, we have proposed a secure framework that can be used for a two-level biometric authentication process where the cloud service providers may be responsible for the verification task. Sending biometric data, such as face images or fingerprints, from the client side to a cloud service provider through a network, is not safe. So the proposed scheme utilizes a RDH scheme through an encryption process to hide the compressed fingerprint data in the face image. The key advantage is that the final image that will be transmitted to the client will be in the form of an encrypted image and the fingerprint details are already hidden in it. The run-length encoding scheme along with the Elias gamma encoding procedure is also used in the proposed scheme for compression of fingerprint data. The proposed scheme can be used in the areas where we need to use secure multiple biometric verifications.

## References

# Chapter 12: An efficient and untraceable authentication protocol for cloud-based healthcare system

**Suryakanta Panda; Samrat Mondal** ^() Department of Computer Science and Engineering, Indian Institute of Technology Patna, Bihta, India

## Abstract

Telecare medical information system (TMIS) extends the healthcare services to remote locations where a patient can consult with a doctor without visiting the hospital in person. Security and privacy preservation of patient's medical data in TMIS is a major concern due to the insecure communication channel. Several protocols have been designed to ensure patient's security and privacy. However, most of these protocols have various security loopholes and not fit for practical use. To overcome these security loopholes, we have proposed a new security-enhanced protocol with less computational overhead for TMIS using biometric hash. The security analysis and performance analysis demonstrate that our protocol achieves all the required security properties and also more efficient than other related protocols.

### Keywords

TMIS; WBAN; Remote healthcare; Authentication; Biometric hashing

## 1: Introduction
