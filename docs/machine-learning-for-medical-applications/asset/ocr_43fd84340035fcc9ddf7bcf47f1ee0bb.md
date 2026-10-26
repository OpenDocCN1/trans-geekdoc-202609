In this method primary features have to be extracted and heuristic rules have to be applied.

Most segmentation techniques employ conventional methods in which features must be manually input, followed by the application of limited, predefined guidelines to delineate structures within the image. These approaches demand significant user input, which reduces their generality and limits effectiveness when applied to new datasets or varying clinical scenarios. Additionally, they require the expertise and time of trained professionals. As shown in Figure 7, the identification process in such cases is largely qualitative, meaning that outcomes can vary significantly depending on the observer, leading to inconsistent and non-reproducible results under different conditions or across different operators.

# 4.1.1 Sensitivity to noise and artifacts

Conventional approaches perform poorly due to noise and artifacts on the medical images. Methods of thresholding and edge detection are especially sensitive to changes in image quality and the presence of noise. The sensitivity learnt in this layer causes problems with segmentation especially in low-quality images with high level of noise.

# 4.1.2 Reduced flexibility to deal with complex hierarchy

Few of the classical approaches to segmentation can address the issue of complex structures that have highly variable resemblance to other tissues. Methods like region growing detection are accurate for nicely marginated objects but are not successful in satisfactorily segmenting structures that are overlapping with adjacent tissues. In complex and variegated segmentation problem-solving, these methods are drawbacks because of this limitation.

In many cases, there is reliance on fixed parameters that has already been done and proven before.

Many conventional segmentation methods rely on numerous strategic factors developed by models that constrain versatility and applicability. For example, in thresholding methods, the use of some thresholding values cannot suit works for any image at a given time. To address this, the parameters to be tuned and optimized often bring extra steps that would slow down the segmentation and compromise the reliability of the techniques.