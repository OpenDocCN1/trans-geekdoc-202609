
data differ from each other by not more than two orders of magnitude, it is preferable to use a simple parameter of the noise percentage. We will show the relationship of the parameters PSNR and pN.

PSNR = 20lg\left(\frac{MAXi}{\sqrt{MSE}}\right), \quad (6.1)

where MAXi is the maximum value received by the pixel image. For a binary image MAXi = 1.

The mean square error of the MSE, expressed in terms of the percentage of noise, will be as follows:

MSE = \left(\frac{pN}{100}\right)^2 \quad (6.2)

These formulas allow us to determine the relationship of the parameters PSNR and pN.

PSNR = 20lg\left(\frac{100}{pN}\right). \quad (6.3)

Some values of conformity of these parameters are shown in Table 6.1.

| pN, per cent | PSNR, dB |
|---|---|
| 1 | 40,00 |
| 5 | 26,02 |
| 10 | 20,00 |
| 20 | 13,98 |
| 30 | 10,46 |
| 40 | 7,96 |
| 50 | 6,02 |
| 60 | 4,44 |
| 70 | 3,10 |
| 80 | 1,94 |
| 90 | 0,92 |
| 100 | 0,00 |

We define an algorithm of filling the receptor field by the noise elements.

Let there be a matrix A of size i × j, which consists of elements a_{ij}, where a_{ij} ∈ [0; 1]. Then, if a_{ij} = 0 and the value of random function (100) = 1, a_{ij} = 1. If a_{ij} = 1, the value of random function (100) = 1, a_{ij} = 0. In this case, the noise components have inverted value of the input binary image. The input image matrix is filled approximately by one per cent of the noise components. The number of possible noise per cent (pN) for each element is the probability that it is noise. This procedure must be repeated pN times to achieve the desired result. Thus, pN = 100 per cent is filled by the unit cells of half pixels of the binary matrix, which consists of zero elements. This occurs due to the fact that in the process of inversion there can be nullled elements, which previously were assigned a 1 value. However, this property does not affect the image recognition process for those values of noise where the noise removal methods are effective.

Thus, it will be obtained for the number of noise image elements kN, depending on the percentage of noise.

kN = S_A · \frac{pN}{100}. \quad (6.4)

S_A is the total area of the receptor field. Since in the programming model its dimensions were taken as 500 × 500 pixels, then S_A = 250000.

An indicator of the efficiency of the method of removing noise will have a certain amount of noise components (kNc), that have remained in the receptor field due to implementation of noise removal process. This amount should be such that its influence in the analysis of the FAI will be offset by the use of permissible error dN. It should be noted that the efficiency of noise removal process in this research is the ability to delete the 1 element into initially empty matrix.

To analyse efficiency of the given method, the amount of noise elements kN determined and the number of non-deleted noise elements kNc was carried out for all the possible noise per cent pN, where pN ∈ [1..100]. The studies were conducted for each of the three specified methods for combating noise. The procedure of this research is as follows:

- 1. Each value of the noise per cent produced is filled with the empty image by noise interference.
- 2. The amount of noise elements is calculated as kN = \sum_{n=1}^{i} \sum_{m=1}^{j} a_{n,m}.
- 3. The noise removal procedure is performed.
- 4. The amount of the remaining noise elements is calculated as kNc = \sum_{n=1}^{i} \sum_{m=1}^{j} a_{n,m}.

The determination of hundred kN and kNc for hundred pN was carried out.

For each i-th pN_i value of average values kN_i and kNc_i is determined. In order to generalise the data, it is necessary to carry out the normalisation of the obtained mean values of the number of noise components (kN and kNc) by dividing into the value of the total area of the receptor field. Thus, the indicators independent of the specific predetermined area will be obtained S_A.

kN_i = \frac{\sum_{j=1}^{100} kN_j}{100} \quad (6.5)

kNc_i = \frac{\sum_{j=1}^{100} kNc_j}{100} \quad (6.6)

Value of the coefficient of efficiency is calculated by the following formula:

eN = \frac{kN - kNc}{kN} \quad (6.7)

Generalised data of research on the effectiveness of the noise removal process is shown in Fig. 6.1.

As seen in Fig. 6.1, the efficiency factor (eN) of each noise removal method varies depending on the percentage of noise interference pN.

When using the matrix 3×3 to combat noise, the following results will be obtained. As shown in the chart, four ranges of noise values can be selected. The first is the kNc value which is equal to zero (pN ∈ [0..6]). The method of noise removal is most effective (eN = 1). Noise items are fully removed in the process of noise control. Second is the kNc value which is close to zero (pN ∈ [7..18]). The method of noise removal is most effective (eN ≈ 1). Here the noise has almost no effect on recognition, but the identification process requires additional adjustment through the use of the error dN. The third is a small kNc value (pN ∈ [19..30]). The method of noise removal is effective (eN > 0,85) but the recognition process is complicated. There are a large number of errors in identification. Fourth is a sharp increase in the value kNc (pN ∈ [31..100]). A noise removal method is not effective and recognition is not possible.

When used for noise control of the matrix chart is 5×5 size, the following results are obtained. As shown in the chart, the four ranges of noise values can be selected. The first is the kNc value which is equal to zero (pN ∈ [0..9]). The method of noise removal is most effective (eN = 1). Noise items are fully being removed in the process of noise control. The second is the kNc value which is small (pN ∈ [10..26]). The method of noise removal is effective (eN > 0.90), but the recognition process is difficult. There are a large number of errors in the identification process. The third shows a sharp increase in the value kNc (pN ∈ [27..53]). A noise removal method is not effective and recognition is not possible. Fourth is the efficiency ratio which is less than zero (pN ∈ [54..100]). The method of noise removal adds the noise elements in the receptor field. A noise removal method is not effective and neither is recognition not possible.

![](img/d6ed6c69a61b1252a9084096bb4904c6_103_0.png)
![](img/d6ed6c69a61b1252a9084096bb4904c6_103_1.png)
![](img/d6ed6c69a61b1252a9084096bb4904c6_103_2.png)

Fig. 6.1: Generalised data of research on the effectiveness of noise removal process by different ways

For removing the contour points method, the effectiveness coefficient calculated by the formula (6.7) will be close to one for the entire range of values pN. But unlike the methods of matrices application with the threshold value, also the method removes the contour points of the image. Large percent values of noise inclusion in noise control must be removed because too much useful information distorts the original object. Recognition becomes impossible. This method is effective for values pN ∈ [0..10].

The use of one or other method of struggle against noise does not affect the principles of image processing using parallel shift technology. Investigation of these methods to calculate the values of permissible errors parameters is necessary, which, in the analysis of the FAI is used. In future, the calculation of the values of these parameters and efficiency of object recognition will be carried out using noise control of matrix 3×3.

## 6.2 Determination of the Permissible Error Range of Values Used to Limit the Maximum Displacement Values

The possible presence of noise impurities in the receptor field during recognition of real images encourages the introduction of certain adjustments in the calculation process. Limitations of values of parameters of the maximum shifts is produced by application of the permissible error dN. We calculate the dN parameter depending on the number of kNc image elements that are not removed in the process of noise control. The average value of noise elements in number of real images, which can get into the shift region of the copy at each time point, is denoted as kNc0. With a uniform distribution of noise, this parameter has the following value:

kNc_0 = kNc · \frac{S_0}{S_A} \quad (6.8)

Image recognition is possible only if the value is less than the limiting values dN·S_v used in calculation of the maximum shear parameter. The use of this property is the third level of noise control. Thus, the dN value will be as follows:

dN ≥ \frac{kNc}{S_A} \quad (6.9)

Hence, the lower boundary of the dN values for each noise level corresponds to the normalised number of noise elements and are not deleted in the fight against noise as seen in Fig. 6.1a. So, when 7 per cent < pN < 18 per cent, the value dN < 0.0048. Thus, for noise levels with pN < 18 per cent, the upper boundary of the range of the permissible error dN
