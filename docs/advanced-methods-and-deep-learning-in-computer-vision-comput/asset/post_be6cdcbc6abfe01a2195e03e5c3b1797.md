
Sun, J., Tappen, M.F., 2013. Separable Markov random field model and its applications in low level vision. IEEE Transactions on Image Processing 22 (1), 402–407.

Sun, Y., Liu, J., Kamilov, U., 2019a. Block coordinate regularization by denoising. In: Advances in Neural Information Processing Systems, pp. 380–390.

Sun, Y., Xu, S., Li, Y., Tian, L., Wohlberg, B., Kamilov, U.S., 2019b. Regularized Fourier ptychography using an online plug-and-play algorithm. In: IEEE International Conference on Acoustics, Speech and Signal Processing, pp. 7665–7669.

Tappen, M.F., 2007. Utilizing variational optimization to learn Markov random fields. In: IEEE Conference on Computer Vision and Pattern Recognition, pp. 1–8.

Teodoro, A.M., Bioucas-Dias, J.M., Figueiredo, M.A., 2016. Image restoration and reconstruction using variable splitting and class-adapted image priors. In: IEEE International Conference on Image Processing, pp. 3518–3522.

Timofte, R., Agustsson, E., Van Gool, L., Yang, M.H., Zhang, L., 2017. NTIRE 2017 challenge on single image super-resolution: methods and results. In: CVPRW, pp. 114–125.

Timofte, R., Rothe, R., Van Gool, L., 2016. Seven ways to improve example-based single image super resolution. In: IEEE Conference on Computer Vision and Pattern Recognition, pp. 1865–1873.

Tirer, T., Giryes, R., 2018. Image restoration by iterative denoising and backward projections. IEEE Transactions on Image Processing 28 (3), 1220–1234.

Tirer, T., Giryes, R., 2019. Super-resolution via image-adapted denoising CNNs: incorporating external and internal learning. IEEE Signal Processing Letters 26 (7), 1080–1084.

Venkatakrishnan, S.V., Bouman, C.A., Wohlberg, B., 2013. Plug-and-play priors for model based reconstruction. In: IEEE Global Conference on Signal and Information Processing, pp. 945–948.

Venkatesh, G., Naresh, Y., Little, S., O'Connor, N.E., 2018. A deep residual architecture for skin lesion segmentation. In: Context-Aware Operating Theaters, Computer Assisted Robotic Endoscopy, Clinical Image-Based Procedures, and Skin Image Analysis. Springer, pp. 277–284.

Wang, X., Yu, K., Wu, S., Gu, J., Liu, Y., Dong, C., Qiao, Y., Loy, C.C., 2018. ESRGAN: enhanced super-resolution generative adversarial networks. In: The European Conference on Computer Vision Workshops.

Xu, L., Ren, J.S., Liu, C., Jia, J., 2014. Deep convolutional neural network for image deconvolution. In: Advances in Neural Information Processing Systems, pp. 1790–1798.

Yair, N., Michaeli, T., 2018. Multi-scale weighted nuclear norm image restoration. In: IEEE Conference on Computer Vision and Pattern Recognition, pp. 3165–3174.

Zamir, S.W., Arora, A., Khan, S., Hayat, M., Khan, F.S., Yang, M.H., Shao, L., 2020. CycleISP: real image restoration via improved data synthesis. IEEE Conference on Computer Vision and Pattern Recognition.

Zhang, J., Ghanem, B., 2018. ISTA-Net: interpretable optimization-inspired deep network for image compressive sensing. In: IEEE Conference on Computer Vision and Pattern Recognition, pp. 1828–1837.

Zhang, K., Zhou, X., Zhang, H., Zuo, W., 2015. Revisiting single image super-resolution under Internet environment: blur kernels and reconstruction algorithms. In: Pacific Rim Conference on Multimedia, pp. 677–687.

Zhang, K., Zuo, W., Chen, Y., Meng, D., Zhang, L., 2017a. Beyond a Gaussian denoiser: residual learning of deep CNN for image denoising. IEEE Transactions on Image Processing, 3142–3155.

Zhang, K., Zuo, W., Gu, S., Zhang, L., 2017b. Learning deep CNN denoiser prior for image restoration. In: IEEE Conference on Computer Vision and Pattern Recognition, pp. 3929–3938.

Zhang, K., Zuo, W., Zhang, L., 2018a. FFDNet: toward a fast and flexible solution for CNN-based image denoising. IEEE Transactions on Image Processing 27 (9), 4608–4622.

Zhang, K., Zuo, W., Zhang, L., 2018b. Learning a single convolutional super-resolution network for multiple degradations. In: IEEE Conference on Computer Vision and Pattern Recognition, pp. 3262–3271.

Zhang, L., Wu, X., Buades, A., Li, X., 2011. Color demosaicking by local directional interpolation and nonlocal adaptive thresholding. Journal of Electronic Imaging 20 (2), 1–15.

Zhang, Y., Li, K., Li, K., Zhong, B., Fu, Y., 2019. Residual non-local attention networks for image restoration. In: International Conference on Learning Representations.

Zhang, Z., Liu, Q., Wang, Y., 2018. Road extraction by deep residual U-Net. IEEE Geoscience and Remote Sensing Letters 15 (5), 749–753.

Zhao, N., Wei, Q., Basarab, A., Dobigeon, N., Kouamé, D., Tourneret, J.Y., 2016. Fast single image super-resolution using a new analytical solution for ℓ2-ℓ2 problems. IEEE Transactions on Image Processing 25 (8), 3683–3697.

Zoran, D., Weiss, Y., 2011. From learning models of natural image patches to whole image restoration. In: IEEE International Conference on Computer Vision, pp. 479–486.

图灵社区出品

O'REILLY®

## 奔跑吧，程序员

### 从零开始打造产品、技术和团队

[美]叶夫根尼·布里克曼 著 吴晓嘉 译

This page intentionally left blank

## 15 Visual adversarial attacks and defenses

Changjae Oh, Alessio Xompero, and Andrea Cavallaro

Centre for Intelligent Sensing, Queen Mary University of London, London, United Kingdom

### CHAPTER POINTS

- The chapter presents the problem definition of adversarial attacks for visual tasks using both images and videos as input.
- The chapter presents the properties of the adversarial attacks and the types of perturbations.
- The chapter presents the target models and datasets used in the attack scenarios.
- The chapter discusses adversarial attacks for image processing, image classification, semantic segmentation, object detection, object tracking, and video classification.
- The chapter also discusses defenses devised against the adversarial attacks.

### 15.1 Introduction

Deep neural networks (DNNs) have been shown to be successful in several vision tasks, such as image classification (Krizhevsky et al., 2012; He et al., 2016), object detection (Ren et al., 2017; Redmon and Farhadi, 2017), semantic segmentation (Long et al., 2015; Yu et al., 2017), optical flow estimation (Revaud et al., 2015; Ranjan and Black, 2017), and video classification (Carreira and Zisserman, 2017; Jiang et al., 2018; Ng et al., 2015). However, DNNs are sensitive to perturbations of the input data that produce the so-called adversarial examples that induce DNNs to erroneous predictions (Szegedy et al., 2014).

The study of data alterations designed to evade a classifier is not new: techniques that mislead classifiers have been discussed for over two decades and include attacks on fraud detection systems (Bolton et al., 2002), spam filters (Meyer and Whateley, 2004) and on specific classifiers, such as Support Vector Machines (Biggio et al., 2013). More recently, there has been a growing interest in adversarial examples for DNNs in visual tasks (Szegedy et al., 2014).

Adversarial examples in visual tasks are generated by modifying pixel values with carefully crafted additive noise that is imperceptible to the human eyes (Carlini and Wagner, 2017; Jiang et al., 2019); or by replacing (rectangular or circular) image regions (Brown et al., 2018; Ranjan et al., 2019) or the border of an image (Zajac et al., 2019). Adversarial examples help investigate and improve the robustness of DNN models (Tsipras et al., 2019; Allen-Zhu and Li, 2020; Engstrom et al., 2019; Santurkar et al., 2019) as well as protect private information in images (Li et al., 2019a; Sanchez-Matilla et al., 2020).

An adversarial attack can be targeted or untargeted. Targeted attacks modify an image or a video for the DNN model to predict a specified class label, such as an object type (Szegedy et al., 2014) or a predefined object trajectory in subsequent frames (Liang et al., 2020). Untargeted attacks modify a source image or video to be classified as any incorrect label other than the original one, or the video perturbations can generate incorrect bounding boxes to mislead a tracker (Liang et al., 2020). Finally, carefully modified stop signs can cause a false negative detection or an incorrect detection of another object type (Lu et al., 2017).

After the problem definition of visual adversarial attacks (Section 15.2), we discuss their main properties (Section 15.3) and the types of perturbation they generate (Section 15.4). Then we overview attack scenarios, models and datasets used to craft adversarial attacks (Section 15.5). Specifically, we cover adversarial attacks for image processing tasks (Section 15.6), image classification (Section 15.7), semantic segmentation and object detection (Section 15.8), object tracking (Section 15.9), and video classification (Section 15.10). Finally, we present strategies to defend DNN models from these attacks (Section 15.11) and conclude the chapter (Section 15.12).

### 15.2 Problem definition

Let x be an image or a video and y be a true label associated with x. The label can be a single class for image or video classification, or a region for optical flow, object detection or object tracking.

Let f(·) be a DNN model that maps x to the label y: y = f(x). An adversarial attack modifies x to produce an adversarial example x̂ that at test time misleads the model, such that f(x) ≠ f(x̂) (see Fig. 15.1). The adversarial example can be obtained by directly modifying the visual data with a perturbation δ such that x̂ = g(x, δ), where g(·) represents the process of adding the perturbation to x or replacing pixel values in x with those of δ.

The adversarial perturbation itself may be crafted using machine learning. In such a case, the attacker may design a loss function L(x, y) that is used to generate the perturbation of the original input with respect to the correct prediction (Goodfellow et al., 2015; Moosavi-Dezfooli et al., 2016; Jiang et al., 2019; Shamsabadi et al., 2020c; Liang et al., 2020). For example, the loss of an adversarial attack may maximize the classification error for a set of training images (Szegedy et al., 2014; Moosavi-Dezfooli et al., 2016; Hosseini and Poovendran, 2018) or may optimize the loss function with the additional objective of modifying the image with an imperceptible perturbation (Szegedy et al., 2014; Goodfellow et al., 2015; Moosavi-Dezfooli et al., 2016; Modas et al., 2019; Shamsabadi et al., 2020c).

Based on knowledge of the target model, f(·), and/or its predictions, y, available to an adversary, an attack can be categorized as white-box or black-box. In a white-box attack, the
