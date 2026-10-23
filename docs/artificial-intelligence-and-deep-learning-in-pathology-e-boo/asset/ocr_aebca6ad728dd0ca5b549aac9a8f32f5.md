# FIGURE 9.5

![](bbox=[0.23, 0.13, 0.81, 0.29])

Representation of colors in the tumor detector: invasive: red, DCIS: orange, benign: green, normal: blue, nontissue: gray. Tumor detection is only applied on the tissue region of Fig. 9.4. (A) Tumor detector output; (B) Zoomed region.

# Image segmentation

Deep learning as described above is capable of learning complex relationships in histopathology images and has successfully been applied to learning differences in large sets of images to separate or classify them as either containing or not containing tumor. This black box or top-down approach certainly has its merits particularly as a screening tool when the requirement is to detect areas of interest for a pathologist to pay special attention to. This approach, although arguably less clinically useful, has also been used to classify tumors into distinct patterns or grades [22]. Using deep learning approaches to classify images according to outcome though is a whole different endeavor, which will be discussed in more detail below, but at the highest level, is difficult because large enough development cohorts with outcome are not generally available at the necessary scale.

This is where traditional machine vision handcrafted features and deep learning have converged with machine learning modeling to create the real possibility of automated histopathology image-based grading. We have shown that a bottom-up approach—segmenting and characterizing histologic compartments morphologically combined with protein expression on multiplexed immunofluorescent images—yields handcrafted feature-based models that provide a significant advantage over conventional grading for risk stratifying patients [17]. This has never been done with H&E image-based models in large part due to the difficulties handcrafted features have in handling color variability and the lack of contrast between compartments. Leveraging deep learning’s ability to distinguish subtlety in large datasets, the next step in automated grading of H&E images is to apply a bottom-up approach, segmenting histologic compartments for direct characterization and feature engineering.

# Nuclear and epithelial segmentation in IF images

The goal of nuclear and epithelial segmentation is to delineate their borders in unmixed images (Fig. 9.6), accurately separating touching or overlapping objects and