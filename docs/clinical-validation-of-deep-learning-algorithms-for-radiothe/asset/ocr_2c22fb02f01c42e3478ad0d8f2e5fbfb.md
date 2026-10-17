![](bbox=[0.061, 0.16, 0.801, 0.611])

**Figure 4: Results from the end-user testing**  
(A) The volumetric dice score between clinical trial segmentations and each of de novo, expert-assisted (clinical segmentation provided), and AI-assisted (AI-generated segmentation provided) segmentations. (B) Answers to qualitative questions asked to experts during the end-user testing. (C) Time needed to complete the segmentation task. AI=artificial intelligence.

To assess changes in radiation delivered as a result of using AI-generated segmentations, we did a dosimetric analysis (appendix pp 45–46). We found non-significant differences between clinical and AI planning target volumes across two common dose metrics: V95 (p=0·37) and D95 (p=0·47; appendix p 47).

Model stability across two separate CT scans of the same patient were assessed using RIDER^24 (appendix p 48). AI versus radiologist on the first scan was non-significantly different from the same comparison on the second scan (VD, p=0·25; and SD, p=0·29; appendix p 49). Radiologists’ total tumour volume across the two scans was non-significantly different from that of the AI models (p=0·19; appendix p 50). In terms of model stability as a function of variation in seed point placement, median predictions showed high stability with an IQR of 0·02 for both VD and SD (appendix p 51). With regard to stability across CT timeframes, we found non-significant differences between 3D and 4D CT data (VD, assisted

model p=0·14, automated model p=0·33; appendix pp 36–38).

Model accuracy was measured on CT of a thorax phantom containing nodules of known volume^25 (appendix p 52). On average, models were found to underestimate nodule volume by 0·4 cm³, or 12% of known volume. Three published models also showed similar trends on the same data^26 (appendix p 53). Models were also found to significantly over-perform on contrast-enhanced images (VD p=0·042; SD p=0·0043; appendix p 66).

Finally, model failure modes were examined through expert review. These included missing thoracic nodal stations originally undersampled in the discovery data (eg, supraclavicular nodes; appendix p 67), over-segmentation into pericardium and collapsed lungs, and susceptibility to motion artifacts around the diaphragm (figure 3A).

Eight experts were asked to perform the segmentation task de novo, or rate and edit a provided segmentation