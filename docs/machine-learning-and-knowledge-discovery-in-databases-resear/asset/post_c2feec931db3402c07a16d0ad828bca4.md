
- 18. Krause, J., Stark, M., Deng, J., Fei-Fei, L.: 3D object representations for fine-grained categorization. In: 2013 IEEE International Conference on Computer Vision Workshops, pp. 554–561 (2013). https://doi.org/10.1109/ICCVW.2013.77

- 19. Lee, D., Song, S., Suh, J., Choi, J., Lee, S., Kim, H.J.: Read-only prompt optimization for vision-language few-shot learning. In: Proceedings of the IEEE/CVF International Conference on Computer Vision (ICCV), pp. 1401–1411 (2023)

- 20. Li, B., Weinberger, K.Q., Belongie, S., Koltun, V., Ranftl, R.: Language-driven semantic segmentation (2022)

- 21. Li, Z., Li, X., Fu, X., Zhang, X., Wang, W., Chen, S., Yang, J.: Promptkd: unsupervised prompt distillation for vision-language models. In: Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition, pp. 26617–26626 (2024)

- 22. Lu, J., Batra, D., Parikh, D., Lee, S.: Vilbert: Pretraining task-agnostic visiolinguistic representations for vision-and-language tasks (2019)

- 23. Maaz, M., Rasheed, H., Khan, S., Khan, F.S., Anwer, R.M., Yang, M.H.: Class-agnostic object detection with multi-modal transformer (2022)

- 24. Maji, S., Rahtu, E., Kannala, J., Blaschko, M., Vedaldi, A.: Fine-grained visual classification of aircraft (2013)

- 25. Nilsback, M.E., Zisserman, A.: Automated flower classification over a large number of classes. In: 2008 Sixth Indian Conference on Computer Vision, Graphics and Image Processing, pp. 722–729 (2008). https://doi.org/10.1109/ICVGIP.2008.47

- 26. Parkhi, O.M., Vedaldi, A., Zisserman, A., Jawahar, C.V.: Cats and dogs. 2012 IEEE Conference on Computer Vision and Pattern Recognition pp. 3498–3505 (2012). https://api.semanticscholar.org/CorpusID:383200

- 27. Qian, Q., Xu, Y., Hu, J.: Intra-modal proxy learning for zero-shot visual categorization with clip. In: Oh, A., Naumann, T., Globerson, A., Saenko, K., Hardt, M., Levine, S. (eds.) Advances in Neural Information Processing Systems, vol. 36, pp. 25461–25474. Curran Associates, Inc. (2023)

- 28. Radford, A., et al.: Learning transferable visual models from natural language supervision (2021)

- 29. Rao, Y., et al.: Denseclip: Language-guided dense prediction with context-aware prompting (2022)

- 30. Recht, B., Roelofs, R., Schmidt, L., Shankar, V.: Do imagenet classifiers generalize to imagenet? (2019)

- 31. Soomro, K., Zamir, A.R., Shah, M.: Ucf101: A dataset of 101 human actions classes from videos in the wild (2012)

- 32. Tan, H., Bansal, M.: Lxmert: Learning cross-modality encoder representations from transformers (2019)

- 33. Wang, H., Ge, S., Xing, E.P., Lipton, Z.C.: Learning robust global representations by penalizing local predictive power (2019)

- 34. Wang, Y., Jiang, X., Cheng, D., Li, D., Zhao, C.: Learning hierarchical prompt with structured linguistic knowledge for vision-language models. In: Proceedings of the AAAI Conference on Artificial Intelligence, vol. 38, pp. 5749–5757 (2024)

- 35. Xiao, J., Hays, J., Ehinger, K.A., Oliva, A., Torralba, A.: Sun database: Large-scale scene recognition from abbey to zoo. In: 2010 IEEE Computer Society Conference on Computer Vision and Pattern Recognition, pp. 3485–3492 (2010)

- 36. Yao, H., Zhang, R., Xu, C.: Visual-language prompt tuning with knowledge-guided context optimization. In: Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR), pp. 6757–6767 (June 2023)

- 37. Yao, H., Zhang, R., Xu, C.: Tcp:textual-based class-aware prompt tuning for visual-language model. In: Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR), pp. 23438–23448 (June 2024)

- 38. Yu, Z., Yu, J., Cui, Y., Tao, D., Tian, Q.: Deep modular co-attention networks for visual question answering (2019)

- 39. Zang, Y., Li, W., Zhou, K., Huang, C., Loy, C.C.: Open-Vocabulary DETR with Conditional Matching, pp. 106–122. Springer Nature Switzerland (2022)

- 40. Zhang, J., Wu, S., Gao, L., Shen, H.T., Song, J.: Dept: decoupled prompt tuning. In: Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR), pp. 12924–12933 (June 2024)

- 41. Zhang, R., et al.: Tip-adapter: Training-free clip-adapter for better vision-language modeling (2021)

- 42. Zhou, K., Yang, J., Loy, C.C., Liu, Z.: Conditional prompt learning for vision-language models (2022)

- 43. Zhou, K., Yang, J., Loy, C.C., Liu, Z.: Learning to prompt for vision-language models. Int. J. Comput. Vision 130(9), 2337–2348 (2022)

- 44. Zhu, B., Niu, J., Han, Y., Wu, Y., Zhang, H.: Prompt-aligned gradient for prompt tuning (2024)

## Quality-Preserving Extreme Image Compression: Using Interpretable Conditioning Inputs with Diffusion Models

Shayan Ali Hassan(⊗), Danish Humair, Ihsan Ayyub Qazi, and Zafar Ayyub Qazi

Department of Computer Science, Lahore University of Management Sciences, Lahore, Pakistan.
{25100165,25100183,ihsan.qazi,zafar.qazi}@lums.edu.pk

### Abstract

Diffusion models have revolutionized image synthesis, but their potential for image compression remains underexplored. We introduce PLIC (Pseudo-Lossy Image Compression), a compression framework leveraging diffusion models and conditioning inputs to achieve high compression ratios while maintaining strong perceptual similarity and superior image quality. Unlike traditional neural compressors using abstract latent representations, our approach uses interpretable conditioning inputs (text prompts, canny edges, color palettes) to guide diffusion-based image reconstruction. Grounded in rate-distortion-perception theory, PLIC prioritizes minimizing bitrate and distortions over pixel-perfect reconstruction, allowing diffusion models to fill in plausible details during decompression which still results in high perceptual similarity. Evaluating on 490 real-world images, we demonstrate superior compression ratios (0.004 bits per pixel and 0.197 bits per pixel on average) while maintaining excellent image quality (mean BRISQUE=23.36, mean CPBD=0.60) and high perceptual similarity. Our approach scales effectively with increasing image resolution, with compression advantages growing at the most common image resolutions. We analyze practical implications including benefits for internet affordability, archival storage, and deployment considerations. Our project code can be found at: https://github.com/PseudoLossy/PLIC.

### Keywords

Image Compression · Diffusion Models · Conditioning Inputs

### 1 Introduction

Image compression is widely used for reducing the data footprint of images while maintaining acceptable visual quality. Without image compression, many digital applications such as web browsing, video streaming, and cloud storage would not be possible at scale. Traditional lossless image compression algorithms, such as those used by PNG, can achieve compression ratios of up to 3:1 (66% compression), while lossy formats like JPEG and WebP can reach up to 20:1 (95% compression) [11]. However, at such high compression levels, image quality often degrades significantly due to severe compression artifacts and distortions.

With the rise in popularity of deep learning models during the last decade, neural network architectures have been extensively applied to image compression tasks, achieving state-of-the-art performance. Generally, neural image compressors involve extracting high-level features from an image using a network and transforming them into a latent space representation. This representation achieves compression by exploiting spatial and semantic redundancies to distill only the most important information. The latent space representation is then provided as input to another network in order to obtain a reconstruction of the original image. Leveraging image features in this manner to reconstruct images has been shown to produce images with fewer visual distortions and greater perceptual fidelity compared to algorithmic codecs [26].

| Compression Type | Compression | Perceptual Similarity | Image Quality |
|---|---|---|---|
| Traditional (e.g JPEG) | High | Medium | Low |
| Neural (e.g HiFiC) | Medium | High | Medium |
| Conditional Diffusion | High | Medium | High |

![](img/f56761e6196132d5b74909d98468408f_449_0.png)

Fig. 1. Overview of how using conditioning inputs in tandem with diffusion models to compress images (our methodology) differs from traditional codecs and neural image compressors. Blue regions indicate compression steps, while red regions indicate decompression steps, while the width of each region provides an estimate of the computational demands. Notice the symmetrical and asymmetrical computational demand of neural compressors and our method respectively. (Color figure online)

More recently, denoising probabilistic diffusion models such as Stable Diffusion have shown remarkable performance in generating high-quality, realistic images [9, 15]. Architectures such as ControlNet [43] use “conditioning inputs” to control diffusion model outputs by conditioning them to adhere to structural guides. These inputs inherently encode perceptually important information about an image, and unlike abstract latent space representations, conditioning inputs explicitly extract interpretable spatial information such as color, structure, and depth, suggesting their potential utility beyond mere generation control.
