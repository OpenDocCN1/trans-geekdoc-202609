
## 29.2 Classification of Biometrics

There are different types of biometric systems: physiological and behavioral biometrics. Physiological biometrics consist of physical features like fingerprint, iris, face, ear, palm etc. while behavioral represents speech, DNA, etc.

### 29.2.1 Human Identification

Researchers underlined the need of identification and various other factors that are collectively required for individualistic human identification in 1990s. Also, various other identification parameters such as codes, names, token-based and knowledge-based biometrics can be used for identification. As far as biometric identification is concerned, iris, palm, face and fingerprint based recognition methods can be used to ensure the security of systems. A broad classification is discussed in the following sections.

### 29.2.2 Face Based Identification

It has been observed that human identification based on a face is an effective security technique. It's an accurate method to identify an individual and offers significant benefits over traditional identification methods and other biometrics, like fingerprint. It is undoubtedly more reliable than fingerprint identification because it is harder to clone and not as easy as in the case of fingerprints. However, with this enhanced security, it cannot be denied that the complexity of a face-based identification system is higher than fingerprint. Researchers have discussed different issues associated with face identification-based security as a problem of rotation detection of multi view faces. Width first search tree, vector boosting algorithm and sparse granular features are the popular techniques used. Some methods based on empirical evaluation may be employed in case of face recognition for the designing of specific training and testing sets, such as experimental settings in Facial Recognition Technology (FERET) and Face Recognition Grand Challenge (FRGC).

### 29.2.3 Palm Identification

A palm print based authentication system uses the palm as a means of secure authentication. This technique may include cancellable biometric concept which is designed for transforming the palm image into a feature representation of lower dimensions. Cancellable biometric design can be done with the random number generation methods. Pseudo random data is being generated with wavelet based palm print features. Research done by Purdue University shows that majority of people appreciated the use of this secure method. Besides, the human hand can be divided into different parts associated with fingers and then the confidence value of each of them can be calculated. Then a support vector data description is reduced by putting it in place. The calculated confidence is then compared with the threshold value and, if it is higher than that, to maintain the symmetry, confidence of other fingers is also raised.

### 29.2.4 Iris Based Identification

Iris based identification can use different steps right from iris image acquisition, image enhancement, feature extraction and feature matching, which can be used for gender identification. Iris coding techniques like Discrete Cosine Transform (DCT), novel patch encoding methods have been devised by researchers for making iris based identification effective. Probability statistical analysis is used to predict equal error rates in worst case scenarios to model for matching and non-matching algorithms. Guo et al. discussed that if iris pattern is compromised that will lead to the breach of security provided by the iris-based security system. The concept of cancellable biometrics is useful in this case; transformation of the iris image is stored rather than storing the original image. Different techniques like gray-combo, bin-combo, gray-salt and bin-salt can be used to design the cancellable biometric, i.e. transformed image. Another method which is used in iris based security is the Bayesian method, which is used to deform pattern matching since the matching process depends on MAP estimation and the type of deformation. Correlation filter is used to recognize same pattern class and its design. Fast fourier transformation can be used to enhance the images and improve the quality of the iris templates.

### 29.2.5 Fingerprint Based Identification

Fingerprint identification is the most popular biometric among the researchers because of its easy to use characteristic. Fingerprint recognition has some positives like legibility, i.e. this is a biometric which is highly universal because mostly people have legible fingerprints. Having a high degree of reliability as it is unique in nature, fingerprints are formed at a very early stage of life and remain structurally unchanged during the whole life and can be measured accurately. Thus, fingerprint recognition is a widely used biometric and used as a secure means of communication. Fingerprint identification uses different steps like normalization, image enhancement, binarization, thinning, minutia extraction and minutia matching. High quality image acquisition is a pre-requisite for a high quality fingerprint identification system. In order to acquire high quality images, various quality improvement techniques like fourier transformation, fast fourier transformation, enhancement through gabor filters, mace filters and wavelet transformation, are among the most widely used methods [24]. Gabor filters are the ones which have optimal joint resolution in both frequency as well as spatial domain. Figure 29.1 represents different methods for human identification.

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_883_0.png)

Figure 29.1 Human identification approaches.

## 29.3 Advantages and Disadvantages of Biometrics

### 29.3.1 Advantages

- 1. Biometric based security provides unmatched security over other traditional methods like passwords, token based, knowledge based etc.
- 2. It's a way of unique identification. i.e. no two fingerprints can be the same.
- 3. There is no need to remember the detail of security data like in other traditional methods.
- 4. Security through biometrics is less prone to be breached by software or online hackers.
- 5. Easy to use and socially acceptable.

### 29.3.2 Challenges

- 1. Major drawback of using biometrics as a means of secure communication is that if it is stolen once it is compromised for forever since it is unchanged for life.
- 2. In case of fingerprints, it is not so hygienic to use it for scanning because of its proneness towards viruses/germs.
- 3. During a long span of time biometrics can change. For example, face gets aged and can carry wrinkles etc.
- 4. In case of face recognition, twins might have identical faces. Thus, it's very difficult to differentiate and identify them.

## 29.4 Uni-modal versus Multimodal Biometrics

Selection of biometric identification system is critically important before pre-deployment as to whether it should be uni-modal or multimodal system. There are positives and negatives associated with each of them; however, in cases where high accuracy and security is a primary concern, multimodal biometric is an obvious choice. These systems are the best suited solution for industries with high security and privacy. Multimodal provides higher security because two biometric credentials are used in order to authenticate, while in uni-modal systems it's only one credential. That is the reason why multimodal biometric identification has an edge over uni-modal identification and traditional authentication.

There are a few characteristics that support the deployment of multimodal biometrics like reliable authentication, high accuracy, high security, acceptance of user and vulnerability. Multimodal biometrics provide reliable authentication and it allows a higher degree of assurance of correct verification and accurate authentication. In multimodal biometrics, multiple biological characteristics are taken into consideration and each one adds additional evidence for authenticity of an individual. For example, gaits of two persons can be similar because of the same family/background because sometimes people from the same family may depict the similar behavior/patterns of movements and the security based upon gaits might not be as accurate as with multimodal or may lead to false recognition. In such a case, multimodal biometrics always has an edge over uni-modal since it can extract more information which is unique in nature, i.e. if gait and iris biometrics are used together, the recognition rate will increase because it is impossible that two people will have similar gait/iris characteristics.

Security is another critical parameter which gets improved with the use of multimodal biometric because multiple patterns are involved and a system can preserve higher threshold settings and a decision on the required security can be made. It depends on the degree of security required; if the security requirement is critical then two or more biometrics can be taken into consideration and if security is marginal then only one biometric is sufficient in order to identify an individual. For enhanced security, up to three biometric can be taken into consideration so that even if the identification system fails for some reason, another biometric can be used and chances of any error or probability of admitting an imposter can be reduced significantly.

Spoofing is another challenge for any security system. It is one of the biggest threats for biometric systems and can lead to a vulnerable situation. Spoofing is a result of breaking down the security and pretending to be someone else which leads to an unauthorized access and thus a breach of security. Researchers used an artificial biometric database and tested for its authentication vulnerability and exhibited that they got matched for more than 50% data. In order to avoid these scenarios, liveness detection is a good choice where blood flow, pulse and temperature can be taken into consideration in the case of a fingerprint as a biometric.
