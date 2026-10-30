
Copy Move Forgery Dataset [8]: It consists of medium-sized images (almost the entirety of them have dimensions 1000×700 or 700×1000 pixels), and it is subdivided into several groups (D0, D1, D2). D0 includes 50 non-compressed images with copy moves relying on translation. D1 and D2 account for 20 non-compressed images depicting simple scenes (i.e., one object and a simple background) rather than complex scenes. The authors were primarily interested in studying the robustness against some specific attacks. Indeed, several images were altered using scaling, translation, rotation, and a mixed combination of the three to check on the CMFD methods’ robustness. It should be noted that CMFD accounts for a wide range of attacks: 1) 50-degree rotations centered around zero degrees with steps of 5°; 30-degree rotations around 12 different angles in the full 360° range; 1-degree rotation around 11 different angles in [−5°, 5°] range. Scaling factors also feature CMFD in the range [0.25, 2]. MICC Dataset [49]: Amerini et al. presented MICC in 2011. The dataset includes several subsets accounting for different image forgeries. MICC-F220 consists of 220 images equally grouped into original and forged categories. MICC-F2000 is composed of 700 tampered and 1300 original pictures. MICC-F8multi includes 8 tampered images with realistic multiple cloning. MICC-F600 is a collection of 440 original images, 160 tampered images, and 160 ground-truth images. Concerning MICC, it should be noted that the authors of MICC ran the following tampering transformations: rotations in the range [0°, 90°] and scaling in the range [0.5, 1.6].

## 12.2.5 Research challenges

This section overviews research questions and challenges involved in CMFD. The scientific literature features CMFD techniques accounting for diverse approaches, spanning low-level image properties through deep learning methods. Although recent progress in artificial intelligence highlights outstanding performances achieved by deep learning methods in CMFD, it is worth dissecting the results and the tampering transformations to analyze performances according to the following questions: Does DL address CMFD better than all other approaches as a whole? Are performances consistent over diverse datasets? Are there features or methodologies proving more robust against specific tampering transformations? Two publicly and highly cited datasets (MICC and CMFD) are employed to run comparisons to answer the research questions above.

## 12.3 DISCUSSION

It has been some time since the first papers on image forensics were presented. Here, some discussions about the methods’ effectiveness are drawn. This section offers a specific case study by comparing some methods belonging to the three approaches. F1 scores for some state-of-the-art methods are compared over the datasets: CMFD and MICC (F2000, F220, F600). The F1-score (equation 1) is a meaningful metric for precision and recall. It is widely employed in evaluating methods’ performances in the scientific literature. F1-score, Precision, and Recall are defined below in equations 12.2–12.3. Noticeably, F1, Precision, and Recall refer to TP (True Positive), FP (False Positive), and FN (False Negative). Zooming in on the comparison methods, a deep learning method based on VGG-16 [53], a machine learning combining clustering and SIFT keypoint [36], a feature point-based technique [55], and a hand-crafted hybrid method [56] are compared using the F1 score (see equation below). For clarity’s sake, it should be noted that Chen et al. [36] method is referred to as ‘Keypoint-based method’; Rodriguez et al.’s [53] as ‘VGG-16 based method’; Yu et al.’s [55] as ‘Hand-crafted feature point’; and Tinnathi et al.’s [56] is referred to as ‘Hand-crafted hybrid method.’ As shown in Figure 12.3, Keypoint-based method overcomes the VGG-16-based method [53] on the CMFD dataset. Conversely, the same deep learning approach outperforms two other state-of-the-art methods on the MICC dataset by at least 4% in the F1 score (see Figure 12.3). The effectiveness of the keypoints’ descriptors is assessed through the comparison in Figure 12.5. Although both methods perform well on the CMFD dataset, keypoint descriptors plus clustering outperforms a deep learning approach. One of the possible reasons resides within the CMFD dataset, which pushes the bar of image alterations using combinations of scaling, translation, and rotation. With SIFT keypoints invariant

![](img/6e4271af21d9a195003ab8711aa79d27_270_0.png)

Figure 12.3 Some common steps involved in machine-learning methods for CMFD.

![](img/6e4271af21d9a195003ab8711aa79d27_271_0.png)

Figure 12.4 Some common steps involved in Deep Learning for CMFD.

![](img/6e4271af21d9a195003ab8711aa79d27_271_1.png)

Figure 12.5 F1-score over the CMFD dataset for two state-of-the-art methods is depicted above.

$F_1 = 2 \times \frac{\text{Precision} \times \text{Recall}}{\text{Precision} + \text{Recall}} = \frac{\text{TP}}{\text{TP} + \frac{1}{2}(\text{FP} + \text{FN})}$ (12.1)

$\text{Precision} = \frac{\text{TP}}{\text{TP} + \text{FP}}$ (12.2)

![](img/6e4271af21d9a195003ab8711aa79d27_272_0.png)

Figure 12.6 F1-score over the MICC dataset for three state-of-the-art methods is depicted in the diagram above.

Recall = TP / (TP + FN) (12.3)

At the same time, VGG-16-based Method proved more robust against image tampering in MICC when compared to ‘Hand-Crafted Feature Point’ and ‘Hand-Crafted Hybrid Method.’ MICC accounts for a larger number of images than CMFD. That could explain why ‘VGG-16-based Method’ overcomes the comparison methods. It might have inferred enough knowledge from original and forged images and thus be more suitable for the final goal.

## 12.4 CONCLUSION

The primary purpose of this chapter is to let readers approach copy-move forgery detection with a bottom-up strategy. Readers are first given an introductory section with background and context on the topic. Section 12.2 provides insights into the most common methods for CMFD: low-level image feature-based, machine learning, and deep learning methods. Each approach is characterized by different steps, as depicted in Figures 12.1–12.3. Noticeably, the deep learning pipeline does not include image feature extraction, as it is embedded within the convolutional layers. Section 12.3 outlines high-level and technical considerations about the methods’ performances on publicly available datasets, such as MICC and CMFD, described in Section 12.2.4. Research questions are introduced in Section 12.2.5 to highlight the current challenges in the field and prompt readers to key factors concerning artificial intelligence-based methods and image processing techniques. In particular, a comparison between SOTA approaches is carried out by looking into F1-score and two publicly available datasets, such as MICC and CMFD (as in Figures 12.4 and 12.5). As can be noticed in Section 12.4, discussions and considerations have been drawn on the employment of diverse approaches consisting of different pipelines. For instance, low-level image feature methods can perform well, especially if they rely on robust descriptors such as SIFT and SURF (Figure 12.5) and when tampering transformations go beyond a certain scaling or rotating factor (as in the CMFD dataset). On the other hand, deep learning approaches reportedly outperform hand-crafted features and machine learning techniques over MICC. As well as in CMFD, the MICC dataset houses scaling, translation, and rotation in their forged images, except for geometrical transformation values being lower than in CMFD. The experimental results from the three SOTA methods suggest that keypoint descriptors might outperform some deep learning methods if tampered regions undergo scaling or rotation beyond certain threshold values.

## REFERENCES

- [1] Liad Kaufman, Dani Lischinski, and Michael Werman. Content-aware automatic photo enhancement. In *Computer Graphics Forum*, volume 31, pages 2528–2540. Wiley Online Library, 2012.
- [2] Aparna Bharati, Mayank Vatsa, Richa Singh, Kevin W Bowyer, and Xin Tong. Demography-based facial retouching detection using subclass supervised sparse autoencoder. In *2017 IEEE International Joint Conference on Biometrics (IJCB)*, pages 474–482, 2017.
- [3] Arfa Binti Zainal Abidin, Hairudin Bin Abdul Majid, Azurah Binti A Samah, and Haslina Binti Hashim. Copy-move image forgery detection using deep learning methods: a review. In *2019 6th International Conference on Research and Innovation in Information Systems (ICRIIS)*, pages 1–6. IEEE, 2019.
- [4] Surbhi Gupta, Neeraj Mohan, and Priyanka Kaushal. Passive image forensics using universal techniques: A review. *Artificial Intelligence Review*, 55:1629–1679, 2022.
- [5] Nor Bakiah Abd Warif, Mohd Yamani Idna Idris, Ainuddin Wahid Abdul Wahab, Nor-Syahidatul N Ismail, and Rosli Salleh. A comprehensive evaluation procedure for copy-move forgery detection methods: Results from a systematic review. *Multimedia Tools and Applications*, 81(11):15171–15203, 2022.
- [6] Ruyong Ren, Shaozhang Niu, Junfeng Jin, Jiwei Zhang, Hua Ren, and Xiaojie Zhao. Multi-scale attention context-aware network for detection and localization of image splicing. *Applied Intelligence*, 53: 1–20, 2023.
- [7] Amit Doegar, Maitreyee Dutta, and Gaurav Kumar. A review of passive image cloning detection approaches. In *Proceedings of 2nd International Conference on Communication, Computing and Networking: ICCCN 2018*, NITTTR Chandigarh, India, pages 469–478. Springer, 2019.
