
application in lung segmentation, providing accurate pixel-wise delineation of lung structures. Attention mechanisms, such as self-attention or channel attention, have further enhanced the capability of deep learning models to focus on relevant regions, discarding irrelevant information and thereby improving the precision of lung segmentation. The integration of these diverse models with their respective strengths contributes to the development of robust and efficient lung segmentation methods, addressing the various image resolutions and achieving high levels of accuracy in delineating lung boundaries.

The following sections of this chapter are structured as follows: Section 7.2 provides a brief overview of medical imaging modalities. Section 7.3 provides an overview of the classical approaches for lung segmentation in chest X-rays. Section 7.4 offers a summary of deep learning models for lung segmentation in both chest X-rays and CT scans. Section 7.5 enumerates several publicly accessible chest X-rays and CT scans. Different evaluation metrics used for assessing model performance are covered in Section 7.6. Last, Section 7.7 encapsulates the conclusive findings and prospective future directions derived from the systematic review.

## 7.2 Medical Imaging Modalities

In clinical settings, diverse medical imaging modalities play crucial roles by offering distinct information tailored to specific diagnostic needs. Among the prevalent modalities are “CT, MRI, PET, ultrasound imaging, and optical coherence tomography (OCT),” as depicted in Figure 7.1. However, in the context of lung segmentation, the focus is on utilizing two modalities – CT scans and X-rays. The selection of CT scans and X-rays is driven by their distinctive attributes and appropriateness for capturing pertinent details in lung imaging.

![](img/b1cb9f9389f496c3199cc2e1e74e4626_171_0.png)

Figure 7.1 Overview of diverse medical imaging techniques. Source: Beyer et al. (2020) /Springer Nature/CC BY 4.0.

## 7.3 Overview of Classical Approaches for Lung Segmentation in Chest X-rays

Traditional methods for LFS typically cover various techniques and approaches, which are discussed as follows.

### 7.3.1 Rule-Based Methods

Rule-based methods include techniques that rely on predefined rules or criteria to delineate and describe the borders and areas corresponding to the lungs. These rules are like step-by-step instructions applied in a specific order to accurately outline the lungs. The rules consider factors such as where the lungs are located, how bright or dark they appear, their texture, and shape, and how they relate to other body structures. These methods provide flexibility by allowing the application of rules in various sequences allowing adaptation to various situations. (Gados and Horvath n.d.) (Figure 7.2).

Intensity thresholding, edge detection, and knowledge-based rules are techniques utilized in rule-based segmentation.

Intensity thresholding categorizes each pixel into either non-lung or lung regions based on a predefined grayscale threshold. The key challenge lies in determining an optimal threshold value because a low setting may lead to unclear lung contour while a high value might merge or blur the boundary between the lung and non-lung regions. Cheng and Goldberg introduced one of the earliest methods in this category, (Cheng and Goldberg 1988) employing a distinct gray-level threshold value to individually segment the left and right lungs. In contrast, Armato et al. presented a method that combines iterative gray-level thresholding, (S. G. Armato et al. 1998) incorporating both global and local aspects, with contour smoothing using morphological operations and rolling-ball techniques. While iterative thresholding improves segmentation precision, it introduces computational overhead. Conversely, static threshold values may lead to suboptimal segmentation, especially in images with varying contrast.

![](img/b1cb9f9389f496c3199cc2e1e74e4626_172_0.png)

Figure 7.2 Diagrammatic Representation of Rule-Based Lung Segmentation Workflow. Source: Mittal et al. (2017) /John Wiley & Sons.

Edge detection-based lung segmentation is used to highlight the edges or contours of the lungs, allowing for accurate segmentation. It depends on variations in pixel intensity between lung and non-lung areas, capitalizing on sharp intensity changes near lung edges. Powell et al. originally used derivatives to identify rib cage boundaries, (Powell et al. 1988) a method subsequently enhanced by Xu et al. who applied the “second-order derivative” for contour identification to capture intricate details, (Xu and Doi 1995) albeit with a susceptibility to noise. Duryea et al. adopted a “heuristic technique” for edge tracing, (Duryea and Boone 1995) independently segmenting both lungs with an average processing duration of 0.84 seconds per image across 802 images. Li et al. further addressed challenges such as rib structure hindrance and false contours, (Li et al. 2001) achieving lung contours in 0.775 seconds per image by utilizing the first derivative. In the domain of intensity and edge-based segmentation, the challenges associated with deformed anatomical structures are addressed by methods incorporating prior understanding of texture, lung spatial, and shape characteristics. Luo et al. proposed a comprehensive approach that employs knowledge-based characteristics, (Luo et al. 2000) utilizing an object-oriented anatomical model, with robust initial contour construction and boundary detection using a snake model. Brown et al. also presented a similar method utilizing an anatomical model for both normal lung shapes and deformities. (Brown et al. 1998) While these approaches contribute to enhancing robustness in lung segmentation, they also face challenges in threshold determination, computational efficiency, and noise susceptibility in edge-based approaches. The choice of a rule-based technique depends on specific requirements and image characteristics.

### 7.3.2 Deformable Methods

These are the techniques that can adapt their shape and boundaries to accurately follow the complex and potentially irregular contours of the lungs. Unlike fixed models that rely on rigid templates or predefined shapes, deformable methods offer greater flexibility and can handle challenges like variability in lung shape and the presence of overlapped structures. Deformable models fall into two categories: “parametric and geometric.” (Figure 7.3).

![](img/b1cb9f9389f496c3199cc2e1e74e4626_173_0.png)

Figure 7.3 Deformable-based lung segmentation process. Source: Mittal et al. (2017) /John Wiley & Sons.

### 7.3.3 Parametric Methods

"Active Shape Model (ASM)" and "Active Appearance Model (AAM)", both belonging to parametric, use a limited set of parameters for lung segmentation in CXRs. These incorporate shape and appearance information to adapt to the variations in lung structures and textures.

In 1995, Cootes et al. introduced the “ASM” (Cootes et al. 1995), which was subsequently refined by other researchers. Wu et al. enhanced the performance of the ASM (Wu et al. 2015) by introducing weighted components and incorporating additional constraints. This modification yielded better accuracy compared to the standard ASM technique. The deformable model proposed by Shi et al. integrates shape statistics at both “patient-specific and population-based” (Shi et al. 2008) levels through hierarchical Principal Component Analysis (PCA). The aim was to employ statistical shape modeling for reliable lung segmentation across various anatomies, with the inclusion of scale-invariant feature transform (SIFT) to enhance accuracy. Iakovidis and Savelonas automated landmark extraction for lung segmentation, (Iakovidis and Savelonas 2009) offering an advantage in initial boundary detection but facing challenges in low-contrast images. Dawoud integrated shape information with intensity-based thresholding, (Dawoud 2011) demonstrating improved results compared to ASM. However, it necessitated the use of images with identical resolution for optimal performance. Zhang et al. (Zhang et al. 2014) suggested a comparable approach that combines intensity information and shape priors for lung segmentation. Both studies employed the JSRT dataset for the training and evaluation of their models. The limitation of ASM lies in its exclusive focus on the object’s shape, neglecting factors such as texture and color variations. To resolve this, AAM was introduced, extending ASM to consider both shape and appearance. While AAM is more powerful, it also requires more computational effort. Li et al. (Li et al. 2016) introduced an innovative approach that integrates both shape and appearance models to enhance the segmentation of lung fields. Their approach incorporated a multi-scale and multi-step-size strategy, contributing to improved accuracy. Additionally, Shao et al. proposed the AAM method using learning-based landmark detection and a hierarchical framework, (Shao et al. 2014) ensuring a thorough and strong segmentation process.

### 7.3.4 Geometric Deformable Models

Deformable models based on geometry, such as the theory of curve evolution and the level set approach, were proposed by Caselles et al. to ensure smooth evolution and effective handling of topology changes, (Caselles et al. 1993) providing advantages in capturing complex lung shapes, while being independent of parameters. Employing the prior shape information, Annangi et al. used an active contour
