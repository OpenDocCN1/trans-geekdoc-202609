conditional generative adversarial networks (AC-GAN) and has generated more diverse and globally consistent images [14]. There is a technique that has tried to boost the accuracy of EEG data classification by using EEG recorded during both perception tasks and imagination tasks. With the help of the attention module and Sinc-EEGNet, it attempts to enhance the understandability of neural networks [15]. Transfer learning is the application of previously learned knowledge and abilities to solve closely related problem-solving cases. Deep neural network (DNN) algorithms, domain adaptation, subspace learning, and improved common spatial patterns (CSP) algorithms are the four frequently used methods in transfer learning for analyzing EEG signals. In the review proposed by Wan et al., the strengths, weaknesses, applications, and challenges of the mentioned transfer learning techniques are discussed [16]. Deep learning methods for EEG signal feature extraction help to detect brain diseases and different psycho-neuro disorders. These methods assist in better understanding human emotions. A review by Praveena et al. provides a broad perspective on the applications of deep learning architectures like recurrent neural networks (RNNs), CNNs, autoencoders, and others in the analysis of signals [17].

This work attempts to visualize the human imagination from EEG signals using deep Learning methods. To generate images, features from the EEG signals need to be extracted first. The extracted features are fed to the generator of the GAN. These features act as conditions on the generator to generate a corresponding image.

This work aims to provide improved implementation of:

+   1. Feature extractors for EEG signals.
+   2. Image classifiers.
+   3. GANs for generating images of digits and characters.

The rest of this chapter is organized across different sections. Section 11.2 discusses the literature review in detail, followed by a proposed methodology in Section 11.3. Results and discussions regarding the presented approach are analyzed in Section 11.4. At last, Section 11.5 discusses conclusions about the proposed approach.

# 11.2 LITERATURE REVIEW

Brain signal analysis and feature extraction are compelling topics in the biomedical research domain. Combining them with the recent developments in the deep learning field like CNNs and GANs, it is now feasible to generate realistic images using the features extracted from the brain signals.

Tirupattur et al. have encoded EEG signals with deep learning architecture and used them as conditioning to generate images. They have carried out experiments on three different domains of input, namely digits, characters, and objects, and demonstrated that their GAN architecture can generate images of a specific class conditioned on EEG patterns [18]. Shen et al. have demonstrated that combining multiple DNN layers enhances the quality and generalizability of generated images. They have also been able to reconstruct artificial shapes along with natural images with the use of a deep generative network (DGN) [19]. Jiao et al. have proposed a two-staged