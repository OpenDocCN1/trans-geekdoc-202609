
*   [Zheng X., Guo Y., Huang H., Li Y., He R.](#Ch007_169-221_S0169716123000020.xhtml#B-bb0945) `A survey of deep facial attribute analysis`. *Int. J. Comput. Vision.* 2020;128(8):2002–2034.

*   [Zietlow D., Lohaus M., Balakrishnan G., Kleindessner M., Locatello F., Scholkopf B., Russell C.](#Ch007_169-221_S0169716123000020.xhtml#B-bb0955) `Leveling down in computer vision: pareto inefficiencies in fair deep classifiers.` In: Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition; 2022:10410–10421.

# Chapter 8: Manipulating faces for identity theft via morphing and deepfake: Digital privacy

Akshay Agarwal^([a](#Ch008_223-241_S016971612200058X.xhtml#af0010)); Nalini Ratha^([b](#Ch008_223-241_S016971612200058X.xhtml#af0015),)[∗](#Ch008_223-241_S016971612200058X.xhtml#cr0010)    ^a `Department of Data Science and Engineering, IISER Bhopal, Bhopal, Madhya Pradesh, India`  

^b `Department of Computer Science and Engineering, University at Buffalo, Buffalo, NY, United States`  

^∗ Corresponding author: email address: [`nratha@buffalo.edu`](mailto:nratha@buffalo.edu)

## Abstract

Digital face images can be easily manipulated for obfuscating or impersonating an identity. Several techniques are used for face manipulation, both traditional computer vision based such as morphing, and modern deep learning based such as deepfake. Morphing and deepfake techniques became advanced enough in creating photorealistic face images. Due to that, these techniques pose a serious threat to identity theft and can significantly harm at a personal level such as the risk of reputation and money, and the national level such as interference in the election. In this chapter, we review (i) different stealthy ways of identity threat generation techniques, (ii) popular databases used in this research direction, and (iii) defense algorithms build to detect these manipulated images. We further provide key open challenges which need to be addressed to make the defense algorithms robust, generalized, and to handle the adaptive nature of the attacks.

### Keywords

`Deepfake`; `Identity swap`; `Digital threats`; `Vulnerability of deep face recognition`; `Privacy and security`

##  1: Introduction

Identification of the correct individual is crucial in several applications including automatic border access, secure digital payment, and communication of a correct message on social media platforms. One of the popular and extensively explored biometric mediums of identity verification is face recognition, due to its nonintrusive nature and easy interpretability of expression useful for communication. The other reason for such extensive exploration of the face modality is that it is not only linked to identity but also other attributes as well such as race, ethnicity, and gender. Similar to humans, who are good at identifying such attributes, deep learning algorithms have also shown tremendous success in that (`[Wang and Deng, 2021](#Ch008_223-241_S016971612200058X.xhtml#bb0320)`).

Due to the popularity and effectiveness of face recognition systems, in recent days, manipulation of face images has become prominent, and several techniques have evolved to easily achieve that goal (`[Majumdar et al., 2019](#Ch008_223-241_S016971612200058X.xhtml#bb0170)`, `2022`(`[Singh et al., 2020](#Ch008_223-241_S016971612200058X.xhtml#bb0290)`) and can fool the humans and machine learning algorithms (`[Köbis et al., 2021](#Ch008_223-241_S016971612200058X.xhtml#bb0120)`). A few notable names of the techniques which are popular in generating the identity manipulated images are (i) morphing, (ii) swapping, and (iii) deepfake. The impact of each method is severe and even so far no research has focused to tackle these different methods simultaneously. Moreover, the impact of these identity manipulation methods is not always the same among different ethnicity, race, or gender individuals (`[Trinh and Liu, 2021](#Ch008_223-241_S016971612200058X.xhtml#bb0300)`). For instance, deepfake threats are more prevalent in females as compared to males (`[Dunn, 2021](#Ch008_223-241_S016971612200058X.xhtml#bb0060)`; `[Vaas, 2019](#Ch008_223-241_S016971612200058X.xhtml#bb0305)`). We assert that since threats can come in any form; therefore, awareness about different possible aspects of threats is essential to develop effective security mechanisms not only to detect but also to impose a ban or even to mitigate the impact of manipulated videos (`[Editor, 2019](#Ch008_223-241_S016971612200058X.xhtml#bb0065)`; `[Flint, 2020](#Ch008_223-241_S016971612200058X.xhtml#bb0080)`; `[Hao, 2021](#Ch008_223-241_S016971612200058X.xhtml#bb0095)`).

The presence of vast identity manipulation methods complicates the fact of “seeing is believing.” While the use case of manipulation technology is not limited to yielding harm and can effectively be used for generating entertainment material or model performance improvement through data augmentation, it is heavily getting used for negative purposes. Therefore, by looking at the severity of the issue, several researchers have developed approaches for detecting these identity-aware alterations. For instance, recently, research works focused on detecting deepfakes including improving the performance of morphing and swapping detection have received desired attention (`[Agarwal et al., 2021b](#Ch008_223-241_S016971612200058X.xhtml#bb0030)`). `[Fig. 1](#Ch008_223-241_S016971612200058X.xhtml#f0010)` demonstrates the importance of addressing this arduous research problem. As can be seen, both face morphing and deepfake produce stealthy images of high quality which can fool face recognition and humans.^([³](#fn3))

![Fig. 1 Identity-manipulated images are generated using two completely different eras of methods. Can you identify the technique (morphing or deepfake) used in the generation of these images? The first and second column images are the source and target face images that are used for manipulated image generation.](images/S016971612200058X/f08-01-9780443184307.jpg)

[Fig. 1](#Ch008_223-241_S016971612200058X.xhtml#B-f0010) Identity-manipulated images are generated using two completely different eras of methods. Can you identify the technique (morphing or deepfake) used in the generation of these images? The first and second column images are the source and target face images that are used for manipulated image generation.

This chapter provides a comprehensive survey of different identity manipulation techniques ranging from generation techniques used for the creation of morphing, swapping, deepfake, existing datasets developed utilizing these methods, and defense algorithms to counter them. We also highlights the impact of different identity manipulation threats and demands that addressing each threat simultaneously is critical. We also provide a few open research challenges including the evolution of adaptive intelligent attacks and the gaps persistent due to the limitations of existing defense techniques such as generalizability and robustness.

##  2: Identity manipulation techniques
