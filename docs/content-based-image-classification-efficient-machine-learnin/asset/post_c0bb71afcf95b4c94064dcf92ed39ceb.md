
```
/* x=R, G and B */
```

- Individual color threshold for each color component is to be calculated. $T_{xlo}$ is considered to be the lower threshold, and $T_{xhi}$ is regarded as the higher threshold by altering the value of $n$ from 1 to 5.

$$T_{xlo}=T_x-n\lvert T_x-T_{overall}\rvert,\quad T_{xhi}=T_x+n\lvert T_x-T_{overall}\rvert$$

```
/* x=R, G and B */
```

- Compute ternary image maps.

$$T_{mx}(i,j)=\begin{cases}1 & \text{if } x(i,j)>T_{xhi}\\0 & \text{if } T_{xlo}\leq x(i,j)\leq T_{xhi}\\-1 & \text{if } x(i,j)<T_{xlo}\end{cases}$$

```
/* x=R, G and B */
```

- Generate image features $tUx$, $tMx$ and $tLx$ for ternary BTC.

$$tUx=\frac{1}{\sum_{i=1}^{m}\sum_{j=1}^{n}T_{mx}(i,j)\;\text{iff}\;T_{mx}(i,j)=1}*\sum_{i=1}^{m}\sum_{j=1}^{n}x(i,j),\;\text{iff }T_{mx}(i,j)=1$$

$$tMx=\frac{1}{\sum_{i=1}^{m}\sum_{j=1}^{n}T_{mx}(i,j)\;\text{iff}\;T_{mx}(i,j)=0}*\sum_{i=1}^{m}\sum_{j=1}^{n}x(i,j),\;\text{iff }T_{mx}(i,j)=0$$

$$tLx=\frac{1}{\sum_{i=1}^{m}\sum_{j=1}^{n}T_{mx}(i,j)\;\text{iff}\;T_{mx}(i,j)=-1}*\sum_{i=1}^{m}\sum_{j=1}^{n}x(i,j),\;\text{iff }T_{mx}(i,j)=-1$$

```
/* x=R, G and B */
```

The other technique, named DTTBTC, has computed the degree values of $n$ in a different way compared to the Static Thepade's Ternary BTC technique. Calculation of the absolute ratio of the threshold for each color component to the overall threshold value of luminance is performed to determine the value of $n$ as given in equation 4.5. The computation has resulted in three different values for three color components according to equation 4.12. The values are compared to each other for choosing the largest value out of the three [4]. The largest value is further considered as the degree value $n$ to be associated dynamically for threshold calculation.

$$n=\begin{cases}\dfrac{T_r}{T_{overall}}, & \text{iff } \lvert T_g\rvert < \lvert T_r\rvert > \lvert T_b\rvert \\ \dfrac{T_g}{T_{overall}}, & \text{iff } \lvert T_r\rvert < \lvert T_g\rvert > \lvert T_b\rvert \\ \dfrac{T_b}{T_{overall}}, & \text{iff } \lvert T_r\rvert < \lvert T_b\rvert > \lvert T_g\rvert\end{cases}\tag{4.5}$$

Comparison of the two feature extraction processes considering the Wang dataset as a testbed is given in Fig. 4.8 based on MR and F1-Score. The comparison shown in Fig. 4.8 shows that DTTBTC has outclassed STTBTC with minimized MR and maximized F1-Score.

## 4.12 Code Example (MATLAB)

```matlab
%Read an image
i=imread('path\\imagefile');
    %Separate the color components
r=i(:,:,1); %red component
[m n p]=size(r); %dimension of red component
g=i(:,:,2); %green component
[x y z]=size(g); %dimension of green component
b=i(:,:,3); %blue component
[j k l]=size(b); %dimension of blue component
    %calculation of mean threshold for STTBTC
Tavred=mean2(r);
Tavgrn=mean2(g);
Tavblu=mean2(b);
    %calculation of threshold for STTBTC
%calculating overall luminance threshold
Tav= (Tavred+Tavgrn+Tavblu)/3;
%calculating lower and higher threshold values for each color component
Tavrl= Tavred- n*(abs(Tavred-Tav));
Tavrh= Tavred+ n*(abs(Tavred-Tav));
%n = 1 to 5
Tavgl= Tavgrn- n*(abs(Tavgrn-Tav));
Tavgh= Tavgrn+ n*(abs(Tavgrn-Tav));
Tavbl= Tavblu- n*(abs(Tavblu-Tav));
Tavbh= Tavblu+ n*(abs(Tavblu-Tav));
    %calculation of threshold for DTTBTC
Trd=Tavred/Tav;
```

**TABLE 4.4**

**Classification Performances by Feature Extraction using Mean Threshold Selection for DTTBTC with Four Different Public Datasets using Four Different Classifiers**

| Datasets | Metrics | KNN | RIDOR | ANN | SVM |
|---|---:|---:|---:|---:|---:|
| Wang | Precision | 0.621 | 0.538 | 0.667 | 0.619 |
|  | Recall | 0.62 | 0.541 | 0.67 | 0.626 |
|  | MR | 0.075 | 0.08 | 0.072 | 0.078 |
|  | F1-Score | 0.621 | 0.538 | 0.666 | 0.616 |
| OT-Scene | Precision | 0.421 | 0.338 | 0.438 | 0.379 |
|  | Recall | 0.418 | 0.337 | 0.439 | 0.372 |
|  | MR | 0.092 | 0.097 | 0.09 | 0.094 |
|  | F1-Score | 0.411 | 0.338 | 0.437 | 0.349 |
| Corel | Precision | 0.509 | 0.535 | 0.451 | 0.475 |
|  | Recall | 0.503 | 0.542 | 0.45 | 0.48 |
|  | MR | 0.09 | 0.084 | 0.089 | 0.087 |
|  | F1-Score | 0.48 | 0.531 | 0.49 | 0.452 |
| Caltech | Precision | 0.444 | 0.49 | 0.534 | 0.432 |
|  | Recall | 0.535 | 0.485 | 0.576 | 0.517 |
|  | MR | 0.091 | 0.089 | 0.078 | 0.095 |
|  | F1-Score | 0.447 | 0.487 | 0.543 | 0.405 |

> [Observation: Wang dataset, OT-Scene dataset and Caltech dataset have highest classification rate with ANN Classifier; Corel dataset has highest classification rate with RIDOR Classifier.]

Hereafter, calculation of average values for diverse metrics is carried out to observe Precision, Recall, MR and F1-Score for classification with four different classifiers—namely, KNN, RIDOR, ANN and SVM—from four different public datasets with features extracted using DTTBTC (Table 4.4).

## 4.13 Feature Extraction Using Local Threshold Selection

This section discusses local threshold selection techniques with two popular methods—namely, Niblack’s local threshold selection and Sauvola’s local threshold selection.

Applications of the local threshold selection techniques are carried out on bit planes of test images and on the original images.

Luminance of images is often found to be uneven, causing major hindrance in selecting a single threshold for the entire image. However, an efficient solution is to segment the image into *m×n* divisions for local threshold selection corresponding to a particular division.

Both the techniques of local threshold selection mentioned in this section have considered both mean and standard deviation for computing the thresholds. This has taken care of the variance of the gray values in the image data.

In the case of Niblack’s threshold selection, determination of the threshold is based on the local mean $m(i,j)$ and standard deviation $\sigma(i,j)$. A window size of (25 × 25) is considered. The threshold is given by $T(i,j)=m(i,j)+k\cdot\sigma(i,j)$. Here, $k$ is a constant having a value between 0 and 1 and is considered to be 0.6 in the proposed method. The value of $k$ and the size of the sliding window determined the quality of binarization.

Sauvola's technique is an improvement over Niblack's method for local threshold selection and is useful for images with faded backgrounds.

Both the techniques are available in the form of *functions()* in the MATLAB library. They can be applied directly to the code example provided in this chapter for feature vector extraction using local threshold selection techniques.

## 4.14 Code Example (MATLAB)

```matlab
%Read an image
i=imread('path\\imagefile');
    %Separate the color components
r=i(:,:,1); %red component
[m n p]=size(r); %dimension of red component
g=i(:,:,2); %green component
[x y z]=size(g); %dimension of green component
b=i(:,:,3); %blue component
[j k l]=size(b); %dimension of blue component
    %Extracting bit planes (red component)
for a1=1:m
for a2=1:n
if bitget(uint8(r(a1,a2)),5)==1 || bitget(uint8(r(a1,a2)),6)==1 || bitget(uint8(r(a1,a2)),7)==1 || bitget(uint8(r(a1,a2)),8)==1
rt(a1,a2,:)=r(a1,a2);
end
end
end
BWr = NIBLACK(rt, [25 25], 0.6, 0, 10);
```

## 4.15 Coding Exercise

The previous code example is for generating local thresholds using Niblack’s technique. Refer to the example to complete the following assignments:

- Extract features from Green and Blue color components using Niblack’s technique.
- Extract features from Red, Green and Blue color components using Sauvola’s technique.

The demonstrations of application for these techniques are given in Figs. 4.9 and 4.10.

Hereafter, calculation of average values for diverse metrics is carried out to observe Precision, Recall, MR and F1-Score for classification with four different classifiers—namely, KNN, RIDOR, ANN and SVM—from four different public datasets with features extracted using Niblack’s and Sauvola’s local threshold selection (Tables 4.5 and 4.6).

## 4.16 Comparing the Discussed Techniques for Performance Evaluation

This chapter discusses six different techniques of feature extraction using binarization from the test images. Four different metrics of comparison are involved for performance evaluation of the techniques. The metrics are Precision, Recall, MR and F1-Score. The techniques are applied on four different datasets—namely, Wang dataset, OT-Scene dataset, Corel dataset and Caltech dataset. Classification is carried out with four different classifiers—namely, KNN Classifier, RIDOR Classifier, ANN Classifier and SVM Classifier.

The performance comparisons are given in Figs. 4.11–4.14.

The comparative results shown in Figs. 4.11–4.14 have recorded the highest classification performance for feature extraction by binarization with Sauvola's local threshold selection.

## 4.17 Comparison with Existing Techniques

Classification performance for feature extraction by binarization with Sauvola’s local threshold selection is compared to the benchmarked
