
![](img/9c1422d4c6a10143e1802787075307de_185_0.png)

FIGURE 10.2 Proposed algorithm for fractional order optical flow estimation.

## 10.4 EXTRACTION OF SMOKE MOTION ACTIVE REGION FROM COLOR MAP

Figure 10.3 illustrates the algorithm for the extraction of a smoke motion active region from a color map. The reference and target images are processed using fractional order optical flow estimation algorithm. This algorithm produces their corresponding fractional order optical flow field as a vector plot. In vector plot representation, each vector represents the pixel flow (motion) with respect to the reference images. To utilize this flow field in the training and testing of a CNN architecture, the vector plots are converted into color maps as described in [32]. These color maps contain the same dimensions as compared to the reference images. In color maps, different colors delineate various flow directions, and color saturation shows flow magnitudes. However, the blue channel of the color maps reflects more sensitivity toward upward motion. In general, smoke shows a tendency to diffuse in an upward direction [44], therefore the blue channel is extracted from the color maps. Hence a dynamic binary mask is developed using the blue channel. Since smoke also demonstrates black, gray and nearly white colors due to the variety of fuel and air supply [45], a static binary mask is also constructed based on the color information. Finally, these dynamic and static binary masks are fused to generate the

![](img/9c1422d4c6a10143e1802787075307de_186_0.png)

FIGURE 10.3 Proposed algorithm for segmenting the smoke motion active region from the estimated color map.

![](img/9c1422d4c6a10143e1802787075307de_186_1.png)

FIGURE 10.4 Design of the proposed CNN architecture for fire prediction using smoke.

resulting mask for segmenting the corresponding color map. Further, the architecture of the proposed CNN model for smoke detection is illustrated in Figure 10.4.

## 10.5 EXPERIMENTS, RESULTS AND DISCUSSION

### 10.5.1 Performance Evaluation Metrics

In binary classification, the discriminatory performance of a model is best described with the help of a confusion matrix [46]. This is a matrix of size 2×2, in which rows and columns represent the actual and predicted data, respectively. Here, the first row contains \( t_p \) and \( f_n \), while the second row contains \( f_p \) and \( t_n \). The evaluation metrics utilized in the performance analysis of the CNN model are often derived from the confusion matrix. This chapter considers the following metrics based on the requirement of the proposed work.

- 1. **Accuracy (Acc)**: Acc provides the proportion of correct predictions in the set of all predictions [47]. It is defined as

  \( CA = \frac{t_p + t_n}{t_p + f_p + f_n + t_n} \)

  This metric generally fails to provide a good description of discrimination, if one class has a very few samples while the other one has a very large number of samples.

- 2. **Recall (R)**: This gives the ratio of correctly classified positive samples over the set of all positive samples [46]. It is also known as sensitivity and is given as

  \( R = \frac{t_p}{t_p + f_n} \)

  It cannot be used to classify an overall proportion of true positives in the set of all the correctly predicted samples.

- 3. **Precision (P)**: It calculates the proportion of correctly classified positives in the set of all positively classified samples [46]. It is also called “positive predictive value” (PPV). It is written as

  \( P = \frac{t_p}{t_p + f_p} \)

  It does not provide any information regarding the true positive proportion in the class of positives.

- 4. **F1-Score (F1)**: It is defined as the harmonic mean of \( R \) and \( P \) [48]. The value of F1 can be small or large according to whether \( R \) and \( P \) are both small or large. It is denoted as

  \( F1 = \frac{t_p}{t_p + \frac{1}{2}(f_n + f_p)} \)

- 5. **Hamming Loss (H-Loss)**: This provides the proportion of false classified samples in the set of all predicted samples [49]. It is defined as

  $$H-loss = \frac{f_p + f_n}{t_p + f_p + f_n + t_n}$$

In addition to these metrics, the performance of the model is also tested using the AUC (area under curve). This AUC gives the area under the ROC curve [50]. Hence larger values of this area correspond to higher true positive rate (TPR). However, an AUC value greater than 50% is generally considered acceptable.

### 10.5.2 Experimental Discussion

The experiments were performed using the Google Colab and MATLAB® software [51] on a Windows 11 platform with 16 GB RAM. They were carried out over a dataset consisting of 324 and 228 reference images and their corresponding color maps for smoke and normal videos, respectively. In order to analyze the performance of the proposed framework, various metrics have been utilized. Also, the proposed framework is comprehensively compared against different existing models, which are discussed in tabular form, learning and ROC curves.

The first experiment discusses the estimated fractional order optical flow fields obtained by implementing the proposed variational model. The parameter values are set to $\sigma = 0.4, \beta = 0.1, \lambda = 200, \text{and } \alpha = 0.7$. The image frames (video) collected from [30, 31] are of different sizes; therefore, in optical flow estimation, these have been resized in $384 \times 384$ size. The few sample reference images for smoke and non-smoke videos, along with their corresponding optical flow fields, are demonstrated in Figure 10.5. The first and second rows in Figure 10.5 illustrate the reference images and corresponding optical flow fields for smoke videos, respectively, while the third and fourth rows represent the reference images and optical flow fields for non-smoke (normal) videos, respectively. Since smoke has a tendency to diffuse in the upward direction and a particular optical flow channel is more sensitive to upward motion, this characteristic of color map channels is clearly visible in the corresponding color maps of smoke. In the case of non-smoke, objects generally do not tend to move upward, which can be seen from their optical flows in Figure 10.5. Moreover, the estimated fractional order optical flow is highly insensitive toward the outliers such as illumination change present in the scenes. This shows the significance

![](img/9c1422d4c6a10143e1802787075307de_189_0.png)

FIGURE 10.5 Sample reference smoke-fire images (first row) and corresponding optical flow fields (second row), non-smoke images (third row), and corresponding optical flow fields (fourth row).

of the nonlinear character of the presented variational model and makes the color maps a helpful tool in classifying smoke and normal scenes. The obtained color maps manifest that the estimated flow fields are dense and preserve motion edge. Finally, the generated datasets is used in the training and testing of the proposed CNN model.

The second experiment comprehensively compares the proposed CNN framework against various existing models in terms of different metrics and the number of parameters in Tables 10.1–10.2. The training and testing of all the existing models in Tables 10.1–10.2 have been conducted over

| Model | CNN Architecture | Acc | R | P | F1 | H-loss |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **Proposed model** | **VGG16 and DenseNet121** | **1.00** | **1.00** | **1.00** | **1.00** | **0.00** |
| Majid et al. [52] | ResNet50 | 0.82 | 0.71 | 1.00 | 0.83 | 0.18 |
| Majid et al. [52] | VGG16 | 0.64 | 1.00 | 0.64 | 0.78 | 0.36 |
| Saeed et al. [53] | Adaboost-LBP | 1.00 | 1.00 | 1.00 | 1.00 | 0.00 |
| Muhammad et al. [54] | AlexNet | 0.64 | 1.00 | 0.64 | 0.78 | 0.36 |
| Khan et al. [55] | VGG16 | 0.64 | 1.00 | 0.64 | 0.78 | 0.36 |
| Wang et al. [56] | VGG16 | 0.98 | 1.00 | 0.98 | 0.99 | 0.02 |
| He et al. [57] | Residual learning | 0.95 | 0.95 | 0.97 | 0.96 | 0.05 |

| Model | CNN Architecture | Parameters |
| :--- | :--- | :--- |
| **Proposed CNN model** | **VGG16 and DenseNet121** | **10,553,346** |
| Majid et al. [52] | ResNet50 | 70,786 |
| Majid et al. [52] | VGG16 | 70,786 |
| Saeed et al. [53] | Adaboost-LBP | 171,110,274 |
| Muhammad et al. [54] | AlexNet | 171,110,274 |
| Khan et al. [55] | VGG16 | 72,142,146 |
| Wang et al. [56] | VGG16 | 8,237,442 |
| He et al. [57] | Residual learning | 4,194,690 |

the same reference image dataset. The proposed model used color maps as well as an image dataset. For comparing the proposed CNN model with Majid et al. [52], the attention layers of their model have been removed. These comparisons show that the proposed algorithm demonstrates better performance than the other existing models. It is observed that Table 10.1 depicts a satisfactory accuracy score of 1.00 for the proposed framework, while the model of Saeed et al. [53] also provides an accuracy score of 1.00 but requires more than 17 times the number of parameters as compared to the proposed model. This validates the applicability of the proposed framework.

In the last experiment, the performance of the proposed CNN model against various existing models is illustrated in Figures 10.6–10.8 in terms of learning and ROC curves. It can be seen that in case of learning curves for the proposed CNN model, the training and validation curves converge and coincide after only 4 epochs, while the other models either take more
