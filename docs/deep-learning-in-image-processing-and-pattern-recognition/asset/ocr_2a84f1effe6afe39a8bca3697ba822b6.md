are indistinguishable from each other due to their proximity to each other and in cases of lengthy text. It is also difficult to recover text using our model for cases where the images have complex backgrounds and text parts are cut off in the image and have occlusions. The cases where unique fonts are used also pose difficulties to the model, and this is because the font patterns are not in the dataset and can be improved by extending the dataset.

![](bbox=[0.17, 0.2, 0.82, 0.37])

# 5. Conclusions and Discussions

In this paper, we proposed a Multi-task learning-based Text Super-resolution (MTSR) Network for scene text images. We adopt a multi-task architecture of SR and reconstruction, utilizing a transformer module called FST to recover text shape using complementary properties between the two tasks. Another transformer-based module, FET, was also used to capture sequential information for arbitrary directions by enhancing the feature map. Then, the feature maps output from each of these transformer modules was fused to improve the visual quality of text images of various shapes. Experimental results show that the proposed model achieves performance competitive with state-of-the-art methods on TextZoom. Furthermore, we proved the effectiveness of our model as a preprocessor not only for the STISR task but also for the STR benchmark.

However, our model does not achieve superior accuracy depending on the recognition method and test set, as shown in Table 4. One possible reason is that our learning methods, such as loss functions and label settings, are not sufficiently specialized for text images. It is also possible that our model does not sufficiently benefit from MTL due to the target image of the reconstruction branch being very close to the target image of the SR branch. Therefore, to build more text-specific models, our future work includes re-definition loss functions and the target image for the reconstruction branch.

**Author Contributions**: Methodology, K.H., M.K. and H.F.; Software, K.H.; Data curation, K.H.; Funding acquisition, H.F. and M.K.; Writing—original draft, K.H.; Writing—review and editing, M.K., H.F. and A.S. All authors have read and agreed to the published version of the manuscript.

**Funding**: This study is funded by JSPS/JAPAN KAKENHI (Grants-in-Aid for Scientific Research) #J20K11955.

**Conflicts of Interest**: The authors declare no conflict of interest.

# Abbreviations

The following abbreviations are used in this manuscript:

+   *   SR Super-resolution
*   STR Scene Text Recognition
*   LR Low Resolution
*   SISR Single Image Super-Resolution
*   HR High Resolution
*   STISR Scene Text Image Super-Resolution