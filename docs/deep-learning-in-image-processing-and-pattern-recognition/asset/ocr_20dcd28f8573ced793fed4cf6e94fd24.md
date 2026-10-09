This paper proposed an improved dual data augmentation (DDA) algorithm by combining the above two data augmentation methods, and its flow is presented in Figure 3.

![](bbox=[0.17, 0.14, 0.83, 0.5])

**Figure 3. Flow of the Dual Data Augmentation Algorithm.**

As shown in Figure 3, first, the Mongolian handwriting data are input into the model and then normalized. Second, a random value within [0, 1] is assigned by the system, and if the random value is greater than 0.4, only use the HWTDA method and output data; otherwise, the DDA method is adopted, that is, the input image data are randomly erased and then, the HWTDA is performed to output the final data augmentation result. In this method, data augmentation of an image is determined by a random value, which alleviates the problem that the similarity between the randomly erased image and the original image is too high. The method of random erasing first and then using horizontal wave transform can also give richer image occlusion noise, which helps improve data richness.

# 3. Improved Mongolian Handwriting Recognition Model: EGA Model

CRNN can realize end-to-end character recognition and is a landmark model in the development of character recognition. However, a large number of experimental results have shown that CRNN has low recognition accuracy when performing Mongolian handwriting recognition tasks; therefore, it is difficult to be used practically. So, this paper presents an ECA-Net-GRU-Attn (EGA) Model based on the characteristics of Mongolian handwriting.

# 3.1. *Training Process of the EGA Model*

Since the proposed EGA model is constructed by improving the CRNN, it follows the CRNN network structure and consists of an ECA-Net for feature extraction, a BiGRU encoder and a BiLSTM decoder for processing feature sequences, and an attention module to enhance sequence prediction performance.

The processing flow of an input image in the EGA model is shown in Figure 4.