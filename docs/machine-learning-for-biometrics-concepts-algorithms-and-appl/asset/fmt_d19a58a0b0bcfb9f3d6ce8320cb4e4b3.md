
![Fig. 1 A sample side face image with extracted ear and profile face images from UND-J2 dataset.](images/B9780323852098000031/f03-01-9780323852098.jpg)

Fig. 1 A sample side face image with extracted ear and profile face images from UND-J2 dataset.

## 3.1 Steerable pyramid transform

SPT [[^(53)](#fn53)]

![Fig. 2 Decomposition of an ear image using SPT with three scales and four orientations.](images/B9780323852098000031/f03-02-9780323852098.jpg)

Fig. 2 Decomposition of an ear image using SPT with three scales and four orientations.

## 3.2 Local texture descriptors

After SPT-based decomposition of ear and profile face images, local texture descriptors are more robust to extract discriminative information from subbands in uncontrolled conditions. In the literature [[^(54)](#fn54)]

## 4 Proposed multimodal biometric recognition

The proposed method consists of five stages: preprocessing, local feature extraction, multimodal fusion, and person recognition are explained in [Algorithm 1](#B9780323852098000031.xhtml#b0005) and the proposed pipeline is shown in [Fig. 3](#B9780323852098000031.xhtml#f0020).

### Algorithm 1

The proposed multimodal biometric recognition.

**Input:** Given training and test sets of segmented ear and profile face images

**Output:** Recognized identity

1. Apply the Gaussian filter to smooth each ear and profile face images using Eq. ([1](#B9780323852098000031.xhtml#fo0010)).
2. Employ steerable pyramid filter bank to generate multiscale and orientation subbands of training and test samples.
3. Apply block-based local texture descriptor to each subbands of training and test images.
4. Concatenate block-wise histograms to acquire training and test feature vector sets.
5. for each ear test feature vector do
6.       Compute matching scores using chi-square measure between test feature vector and all training feature vectors by Eq. ([2](#B9780323852098000031.xhtml#fo0015)).
7.       Determine recognized identity of ear test sample based on matching scores using kNN classifier.
8. end for
9. for each profile face test feature vector do
10.       Compute matching scores using chi-square measure between test feature vector and all training feature vectors by Eq. ([2](#B9780323852098000031.xhtml#fo0015)).
11.       Determine recognized identity of profile face test sample based on matching scores using kNN classifier.
12. end for
13. Calculate Accuracy and EER for ear and profile face biometrics modalities.
14. for each ear and profile face matching score do
15.       Compute fused matching scores using weighted sum rule of score-level fusion using Eq. ([5](#B9780323852098000031.xhtml#fo0030)).
16.       Determine recognized identity of each sample based on fused matching scores using kNN classifier
17. end for
18. Evaluate overall Accuracy (%) and EER (%) of the proposed recognition method.

![Fig. 3 Pipeline of the proposed method.](images/B9780323852098000031/f03-03-9780323852098.jpg)

Fig. 3 Pipeline of the proposed method.

## 4.1 Preprocessing

To smooth the noises present in the input side face images, Gaussian low-pass filter is employed. The convolution operation is performed between Gaussian kernel (`G`) and side face image (`I`) to obtain smoothed input image (`I'`) as follows:

```
I' = I * G(u, v, σ)
G(u, v, σ) = 1 / (√(2π) σ) * exp(- (u² - v²) / (2σ²))
```

![si2_e](images/B9780323852098000031/si2_e.png)  (1)

where `σ` is the standard deviation of Gaussian kernel.

## 4.2 Feature extraction using block-based SPT-BSIF descriptor

In this work, we employ three-scale and six-orientation steerable pyramid filter bank on ear and profile images, which decompose an image into 18 subbands of different scales and orientations. Then, all subbands are divided into a number of nonoverlapping blocks and being applied BSIF feature extractor to all blocks. The normalized histogram texture descriptors of all blocks are concatenated to form a (`SPT-BSIF`) feature vector. Finally, we obtained two normalized feature vectors `F[Ear]` and `F[PF]` for ear and profile face, respectively.

## 4.3 Matching and classification

Before performing classification, the matching scores of all probe samples are computed in two steps: (1) compare each probe image with all gallery images to generate a set of matching scores using chi-square measure as given in Eq. ([2](#B9780323852098000031.xhtml#fo0015)), and (2) kNN classifier has used to obtain single matching score for each probe sample.

```
χ(F₁, F₂) = Σₖ₌₁ᴺ (f₁,ₖ - f₂,ₖ)² / (f₁,ₖ + f₂,ₖ)
```

![si3_e](images/B9780323852098000031/si3_e.png)  (2)

In this chapter, we used the proposed method in a verification mode. In this case, the probe image is matched with the gallery images to verify the individual's claimed identity. Finally, matching scores of probe samples are used to compute false acceptance rate (`FAR`) and false rejection rate (`FRR`) to evaluate the recognition accuracy in (%) of the proposed method using Eq. ([3](#B9780323852098000031.xhtml#fo0020)). Another recognized performance measure is equal error rate (`EER`), which is the rate at which `FAR` and `FRR` are equal [[^(55)](#fn55)]

```
Accuracy = 100 - (FAR + FRR) / 2
```

![si4_e](images/B9780323852098000031/si4_e.png)  (3)

## 4.4 Multimodal fusion

In this work, both feature-level and score-level fusions have been examined to determine higher recognition performance of the proposed method.

## 4.5 Feature-level fusion

In feature-level fusion, ear feature `F[Ear]` and profile face feature `F[PF]` are consolidated into a single feature vector `F[Fused]` as follows:

```
F_Fused = F_Ear ∪ F_PF
```

![si5_e](images/B9780323852098000031/si5_e.png)  (4)

## 4.6 Score-level fusion

In score-level fusion, the matching score of ear `S[Ear]` and profile face `S[PF]` are individually calculated using chi-square distance measure and are fused based on Eq. ([5](#B9780323852098000031.xhtml#fo0030)) to obtain a fused score for recognizing individual using kNN classifier.

```
S_Fused = (A_Ear × S_Ear + A_PF × S_PF) / (A_Ear + A_PF)
```

![si6_e](images/B9780323852098000031/si6_e.png)  (5)

where `A[Ear]` and `A[PF]` are the recognition accuracy of ear and profile face modalities, respectively.

## 5 Experiments and results

In this section, we present various experiments to demonstrate the effectiveness of the proposed method. First, we discuss UND-E and UND-J2 datasets used in the experiments and experimental setup to tune the different parameters of steerable pyramid filter bank and local feature extractors, namely, `LDP`, `LPQ`, and `BSIF`. Second, we perform experiments for feature-level fusion and score-level fusion of ear and profile face feature sets. Third, we compare the recognition accuracy of the proposed method with existing methods, which have been implemented on UND-E and UND-J2 datasets.

## 5.1 Datasets

UND-E [[^(56)](#fn56)]

UND-J2 [[^(57)](#fn57)]

![Fig. 4 Dataset sample images of some subjects' ear and profile face from UND-E (first row) and UND-J2 (second row).](images/B9780323852098000031/f03-04-9780323852098.jpg)
