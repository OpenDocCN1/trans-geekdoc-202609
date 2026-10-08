# Video Classification

# Chapter 9

+   - Montreal Video Annotation Dataset (M-VAD) can be obtained from: https://mila.quebec/en/publications/public-datasets/m-vad/ and has 49,000 clips.
- YouTube2Text has 1,970 videos with 80,000 descriptions.

Yao et al. (https://www.cv-foundation.org/openaccess/content_icv_2015/papers/Yao_Describing_Videos_by_ICCV_2015_paper.pdf) proposed a method for captioning videos. A 3D convolutional network trained for action recognition is used to extract the local temporal features. An attention mechanism is used on the features to generate text using an RNN. The process is shown here:

![](bbox=[0.257, 0.313, 0.742, 0.538])

> Reproduced from Yao et al.

Donahue et al. (https://www.cv-foundation.org/openaccess/content_cvpr_2015/papers/Donahue_Long-Term_Recurrent_Convolutional_2015_CVPR_paper.pdf) proposed another method for video captioning or description, which uses LSTM with convolution features.