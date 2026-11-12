# 7.3 Overview of Classical Approaches for Lung Segmentation in Chest X-rays

Traditional methods for LFS typically cover various techniques and approaches, which are discussed as follows.

# 7.3.1 Rule-Based Methods

Rule-based methods include techniques that rely on predefined rules or criteria to delineate and describe the borders and areas corresponding to the lungs. These rules are like step-by-step instructions applied in a specific order to accurately outline the lungs. The rules consider factors such as where the lungs are located, how bright or dark they appear, their texture, and shape, and how they relate to other body structures. These methods provide flexibility by allowing the application of rules in various sequences allowing adaptation to various situations. (Gados and Horvath n.d.) (Figure 7.2).

Intensity thresholding, edge detection, and knowledge-based rules are techniques utilized in rule-based segmentation.

Intensity thresholding categorizes each pixel into either non-lung or lung regions based on a predefined grayscale threshold. The key challenge lies in determining an optimal threshold value because a low setting may lead to unclear lung contour while a high value might merge or blur the boundary between the lung and non-lung regions. Cheng and Goldberg introduced one of the earliest methods in this category, (Cheng and Goldberg 1988) employing a distinct gray-level threshold value to individually segment the left and right lungs. In contrast, Armato et al. presented a method that combines iterative gray-level thresholding, (S. G. Armato et al. 1998) incorporating both global and local aspects, with contour smoothing using morphological operations and rolling-ball techniques. While iterative thresholding improves segmentation precision, it introduces computational overhead. Conversely, static threshold values may lead to suboptimal segmentation, especially in images with varying contrast.

![](bbox=[0.107, 0.735, 0.906, 0.843])

Figure 7.2 Diagrammatic Representation of Rule-Based Lung Segmentation Workflow. Source: Mittal et al. (2017) /John Wiley & Sons.