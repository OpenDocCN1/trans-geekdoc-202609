# ## 12.3 PROPOSED CARDIAC IMAGE-BASED AUTOMATIC HEART DISEASE DIAGNOSIS MODEL

Cardiac imaging plays an important role in diagnosing heart disease. The unavailability or shortage of radiologists and physicians in various countries, for a number of reasons, is a significant factor in barriers to early diagnosis of this high-mortality disease. Among the various efforts to develop end-support systems, computational intelligence is a growing trend in the field of clinical imaging for prognosis and diagnosis. This helps radiologists and clinicians to get relief from the heavy burden and reduce the delays in achieving timely diagnoses of patients. Therefore, in this study, automatic heart disease prognosis was proposed using a deep neural network. The proposed approach consists of four stages, namely pre-processing, feature extraction, feature selection, and classification. The cardiac image-based automatic heart disease diagnosis model is described in Figure 12.1.

# ### 12.3.1 Pre-processing

Consider the cardiac image Iij, which includes some noise. To remove the noise present in the input image, a median filter is applied. The median filter is typically used to lessen noise in an image. It is a non-linear filter that computes median of the pixel set that falls within the filter mask. Each pixel is addressed, and it is replaced by means of statistical median of its m×n neighborhood. Since the median value is computed from the neighboring pixel, it is more robust to outliers and does not create a new realistic pixel value, which would preserve edge

![](bbox=[0.12, 0.58, 0.88, 0.89])

FIGURE 12.1 Proposed cardiac image-based automatic heart disease diagnosis model.