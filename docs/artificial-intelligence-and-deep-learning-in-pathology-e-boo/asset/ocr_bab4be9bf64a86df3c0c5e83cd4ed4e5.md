![](bbox=[0.14, 0.12, 0.78, 0.35])

# FIGURE 9.3

Structural (A and B) and functional (D and E) immunofluorescent biomarkers in high-grade prostate cancer (20× objective lens), Gleason pattern 4, after unmixing. Panel F combines four biomarkers by showing the maximum value biomarker at each pixel, with AR (purple), Ki67 (yellow), DAPI (blue), and CK18 (gold). Compare with H&E stain of the same tissue in panel (C). (A), CK18; (B), DAPI; (C), H&E; (D), AR; (E), Ki67; (F), Max biomarker.

# Automated detection of tumor regions in whole-slide images

# Localization of diagnostically relevant regions of interest in whole-slide images

A digital whole-slide image (WSI) obtained from scanning glass slides often has more than a billion pixels in the highest resolution (40×). However, only small regions within the slide contain diagnostic information. The relevant region in the image is usually less than 50% of the digitized area. Additionally, artifacts such as ink, mounting medium air bubbles, tissue folds, crushed nuclei, and out-of-focus regions could potentially mislead feature extraction, segmentation, and detection algorithms.

A multiscale framework using high- and low-resolution imaging features was proposed in Ref. [40] to rapidly identify the high-power fields of interest in the WSIs. Bahlmann et al. [41] developed a classification method for discriminating between statistics of relevant versus irrelevant regions. They used visual descriptors that captured the distribution of color intensities observed for nuclei and cytoplasm. Moreover, Mercan et al. in Ref. [42] extracted regions of interest (ROIs) by tracking records of pathologists’ actions, such as zooming, panning and fixating. They developed a visual bag-of-words model based on color and texture features of the extracted regions to predict diagnostically relevant ROI in the WSIs. We developed an automatic technique for detecting diagnostically important ROIs within the WSIs using convolutional neural networks (CNN). We trained the CNN to identify