
For `Test B`, we employ a commonly used non-reference image quality assessment algorithm `NIQE` [[49](#chap10.xhtml#fsr49)] to assess the perceptual quality. A smaller `NIQE` score indicates better perceptual quality. Besides, we also conduct a user study to provide realistic feedback about subjective quality. We first randomly select 50 images from `Test B`, and then invite 10 participants with image enhancement expertise to rank the results of different methods from 1 to 5 where 1 is the worst quality and 5 is the best quality. This user study is repeated five times. The average values in terms of `NIQE` [[49](#chap10.xhtml#fsr49)] and user study are shown in [Table 2](#chap10.xhtml#tab2).

![](images/p248-1.jpg)

**Figure 6:** Visual comparisons on synthetic retinal images. From left to right are the inputs from `Test A`, the results of `CLAHE` [[5](#chap10.xhtml#fsr5)], `LIME` [[17](#chap10.xhtml#fsr17)], `SGF` [[4](#chap10.xhtml#fsr4)] and our `NuI-Go`. Red box indicates our results.

![](images/p249-1.jpg)

**Figure 7:** Visual comparisons on real retinal images. From left to right are the inputs from `Test B`, the results of `CLAHE` [[5](#chap10.xhtml#fsr5)], `LIME` [[17](#chap10.xhtml#fsr17)], `SGF` [[4](#chap10.xhtml#fsr4)] and our `NuI-Go`. Red box indicates our results.

**Table 1:** Quantitative evaluations on `Test A` in terms of `PSNR` (dB) and `SSIM`.

![](images/p249-2.jpg)

*Note:* For each case, the best result is in bold.

**Table 2.** The average non-reference `NIQE` scores and user study scores on `Test B`.

![](images/p250-1.jpg)

*Note:* For each case, the best result is in bold.

In [Table 2](#chap10.xhtml#tab2), our method achieves the best performance in terms of non-reference `NIQE` [[49](#chap10.xhtml#fsr49)] and subjective user study. Such results demonstrate our method can generalize to real retinal images and effectively improve the visual quality of degraded retinal images. Besides, it also indicates the reason-ability of our non-uniform illumination synthesis approach. Though our model is trained on synthetic training data, it is also useful for real retinal images.

### 4.3.2 Retinal vessel segmentation

To evaluate the performance of our method in practical applications, we use recent `CE-Net` [[50](#chap10.xhtml#fsr50)] that is trained on `DRIVE` dataset [[51](#chap10.xhtml#fsr51)] (20 images for training and 20 images for testing) as a basic retinal vessel segmentation model. We found that the existing vessel segmentation datasets do not contain the non-uniform or poor illumination retinal images. However, the non-uniform illumination retinal images are ubiquitous in the real world. Therefore, we degrade the testing set of `DRIVE` dataset [[51](#chap10.xhtml#fsr51)] and the `STARE` dataset [[52](#chap10.xhtml#fsr52)] by the approach mentioned before. The testing data did not appear in the training set. The first manual annotation in these two datasets is used as the ground truth for performance evaluation. We enhance these testing images by different methods and feed the results to the `CE-NET` [[50](#chap10.xhtml#fsr50)]. At last, we measure the average accuracy (`Acc`) and the area under receiver operation characteristic curve (`AUC`) by the formula mentioned in [[50](#chap10.xhtml#fsr50)]. First, we present several sample results before and after processing by our method and the corresponding segmentation results in [Fig. 8](#chap10.xhtml#fig8). Secondly, we report the `Acc` and `AUC` scores in [Table 3](#chap10.xhtml#tab3).

As shown in [Fig. 8](#chap10.xhtml#fig8), our method can effectively unveil the vessel under dark regions. As a result, the vessel of retinal images processed by our method can be easily segmented by the `CE-Net` [[50](#chap10.xhtml#fsr50)] that is trained by using well-lit retinal images. Thus, despite the retinal image segmentation algorithms not considering the non-uniform illumination issue in their designs and training procedures, our method could be used as an effective pre-processing step for further improving their performance.

**Table 3.** Quantitative evaluations on `DRIVE` dataset/`STARE` dataset in terms of `Acc` and `AUC`.

![](images/p251-1.jpg)

*Note:* For each case, the best result is in bold.

![](images/p251-2.jpg)

**Figure 8:** Visual retinal vessel segmentation results. (a) The input images from the degraded `DRIVE` dataset [[51](#chap10.xhtml#fsr51)] and `STARE` dataset [[52](#chap10.xhtml#fsr52)] and the corresponding segmentation results. (b) Our enhanced results and the corresponding segmentation results. The segmentation results are produced by the `CE-Net` [[50](#chap10.xhtml#fsr50)].

As presented in [Table 3](#chap10.xhtml#tab3), the results enhanced by our `NuI-Go` achieve better segmentation performance on the `DRIVE` [[51](#chap10.xhtml#fsr51)] and `STARE` [[52](#chap10.xhtml#fsr52)] datasets. Compared with the degraded images (inputs), the `Acc` increases from 0.9508/0.9369 to 0.9543/0.9417 and the `AUC` increases from 0.9329/0.7976 to 0.9756/0.9213, respectively. In addition, it is interesting that some enhancement algorithms decrease the performance of retinal vessel segmentation, which is undesired in practical applications. To demonstrate the robustness of our method on real retinal images, we provide several sample segmentation results for real retinal images in [Fig. 9](#chap10.xhtml#fig9). It is obvious that after enhancing by our method, some retinal vessels hidden in the dark are recovered and thus can be accurately segmented by the `CE-Net` [[50](#chap10.xhtml#fsr50)]. The results in [Fig. 9](#chap10.xhtml#fig9) further demonstrate the effectiveness and robustness of our method.

### 5. Conclusion

In this chapter, we mainly introduce the enhancement of retinal images and propose a deep learning-based retinal image non-uniform illumination removal method. In the proposed method, the non-uniform illumination is progressively removed via recursive residual learning, while the details and color of retinal images are recovered by the combination of local and nonlocal features. As a key component, we introduce non-local unit into the encoder–decoder network, which models the context effectively. Besides, we propose a non-uniform illumination of retinal image synthesis approach, which is useful for the supervised learning of deep networks. Experiments on synthetic and real-world retinal images show that the proposed method outperforms existing image enhancement methods. Additionally, experimental results suggest that our method can effectively improve retinal vessel segmentation. With the proposed non-unifom illumination removal method, the diagnosis of ophthalmologists and the performance of computer-aided analysis of retinal diseases can be improved. Morveover, the proposed rertinal image synthesis approach can call for the development of deep learning-based computer-aided diagnosis.

![](images/p253-1.jpg)

**Figure 9:** Visual retinal vessel segmentation results of real retinal images. (a) The input images from `Test B` and the corresponding segmentation results. (b) Our enhanced results and the corresponding segmentation results. The segmentation results are produced by the `CE-Net` [[50](#chap10.xhtml#fsr50)]. Red box indicates our results.

### References

[1](#chap10.xhtml#fs1). M. D. Abramoff, M. K. Garvin, and M. Sonka, “Retinal imaging and image analysis,” *IEEE Rev. Biomed. Eng*., vol. 3, pp. 169–208, 2010.

[2](#chap10.xhtml#fs2). A. Hani and H. A. Nugroho, “Retinal vasculature enhancement using independent component analysis,” *J. Biomed. Sci. Eng*., vol. 2, no. 7, pp. 543–549, 2009.

[3](#chap10.xhtml#fs3). M. Zhou, K. Jin, S. Wang, J. Ye, and D. Qiao, “Color retinal image enhancement based on luminosity and contrast adjustment,” *IEEE Trans. Biomed. Eng*., vol. 65, no. 3, pp. 521–527, 2018.
