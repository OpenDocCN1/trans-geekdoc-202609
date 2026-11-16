super pixel based adaptive denoising and luminance adaptive contrast enhancement.
The technique based on adaptive sigmoid function [8] effectively eliminated noise
and improved the contrast of fundus images. The method proved to be efficient for
preprocessing color retinal images that are used in computer-aided clinical diagn-
osis. The method adaptive histogram equalization tuned with non-similar group-
ing curvelet [9] adopts a joint enhancement denoising method by including curvelet
features to preserve better edges. Halo ringing artifacts are prevented by adaptive
histogram enhancement method. The drawback was it could not address luminosity
related issues. Out of the three methods, contrast stretching (CS), histogram equal-
ization (HE) and contrast limited adaptive histogram equalization (CLAHE) meth-
ods prove that poor quality images are corrected and image denoising is performed
well on fundus images [10]. There are many works carried out in classification of
retinal images based on CNN [11–13]. The CNN classification framework helps to
classify images without the help of any preprocessing edge detection stages. The
VGG19 model is fine-tuned with retinal database, and the transfer learning approach
is employed [14]. Fundus image enhancement technique fusing original retinal image
and the image background information is presented in [15]. Deep CNN is developed
[16] and helps to analyze fundus images, and it has 18 convolution layers and 3 fully
connected layers. It proved to be accurate in diagnosing and grading diabetic reti-
nopathy. The technology helped ophthalmologists in early diagnosis and tracking
retinal diseases to some extent [17]. The restored and enhanced image after applying
the MR-DCNN algorithm gave good results in the case of retinal images from the
STARE dataset [18], and the comparison of our results with existing retinal image
enhancement techniques is clearly mentioned in this work.

# ## 11.3 PROPOSED METHOD

Noisy input is fed to our MR-DCNN model (Figure 11.1). The image with noise is
represented by the equation _y_=_n_+_x_, where _x_ denotes a clean input, _n_ is AWGN
with a standard deviation of σ and _y_ is the corrupted data. There are mainly four
blocks that serve as basic building blocks of the proposed method.

+   (1) FEB_CNN, 2 Feature extraction blocks
+   (2) EB_CNN, an Enhancement block
+   (3) CB_CNN, a Compression block
+   (4) RB_CNN, a Reconstruction block.

Sparse features are combined in FEBs; thereby diverse features can be extracted.
By incorporating sparsity, local and global features can be extracted. This helps to
handle corrupted noisy information efficiently.

EB_CNN combines the features of the two sub-networks, and by doing so it
increases the retrieved features. CB CNN lowers the computational cost. The recon-
struction block RB CNN recreates a clean quality image. Figure 11.1 displays the
proposed multi-resolution dual CNN for image denoising. This consists of 2, 16-layer
structures with 4 main blocks. Sparse blocks are beneficial as they enhance the effec-
tiveness and performance. FEB_CNN consists of two sub-networks: FEBnet1 and