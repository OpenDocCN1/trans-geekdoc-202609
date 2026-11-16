
FA outperformed the FA via Lévy flight algorithm, PSO and GA by maximizing the combination of entropy, energy and contrast as objective function. Artificial Bee Colony (ABC) algorithm based edge image enhancement model had been proposed by Benala et al. and ABC outperformed GA in this field (Benala, T. R. et al. (2009)). Chaotic sequence based ABC algorithm had also been applied for brightness preserving image enhancement domain (Dhal, K. G., Das, S. (2015)). The proposed ABC outperformed the traditional ABC and PSO by considering the efficiency of the used objective function. CS algorithms with Lévy flight and chaotic sequence had been employed in image enhancement field (Dhal, K. G., Quraishi, I. M., Das, S. (2017), Dhal, K. G., Sen, M., Das, S. (2017), Dhal, K. G., Das, S. (2017), Bhandaria, A. K. (2014)). A chaotic version of Bat algorithm was presented by the authors (Dhal, K. G., Quraishi, I. M., Das, S. (2015), Dhal, K. G., Quraishi, I. M., Das, S. (2015)) which outperformed the chaotic CS algorithm and chaotic version of FA in image enhancement field. The next section describes the proposed image enhancement method.

## PROPOSED BI-HISTOGRAM FUZZY CONTRAST STRETCHING (BHFCS) METHOD

This paper demonstrates a new parameterized Bi-Histogram Fuzzy Contrast Stretching model (BHFCS) for image enhancement which is discussed below:

- 1. Find the histogram of the corresponding image.
- 2. Divide the histogram based on threshold \(X_T\) which yields minimum brightness error between input and output images (Chen, S. D., Ramli, A. R. (2004), Chen, S. D., Ramli, A. R. (2003)). It is proved that this threshold helps to preserve the original brightness of the image (Dhal, K. G., Sen, S., Sarkar, K., Das, S. (2016), Dhal, K. G., Das, S. (2017a)).
- 3. If any pixel i.e. \(X_i \le X_T\) then \(X_i \in C_1\) and if \(X_i \ge X_T\) then \(X_i \in C_2\) where \(C_1, C_2\) are classes corresponding to background and foreground respectively. Therefore, the fuzzy membership for the pixels corresponding to the classes \(C_1\) and \(C_2\) have been computed as follows:

\(\mu_{c1}(X_i) = 1 - \frac{X_T - X_i}{X_T}, \mu_{c2}(X_i) = 1 - \frac{E - X_i}{E - X_T}\) (1)

Where, E ≤ 255 and it is set by optimization. \(\mu_{c1}\) and \(\mu_{c2}\) are fuzzy memberships for classes \(C_1\) and \(C_2\) respectively and membership values lie between

$$0 \le \begin{cases} \mu_{c1}(X_i) \\ \mu_{c2}(X_i) \end{cases} \le 1$$

- 4. The enhanced pixel values for classes \(C_1\) i.e. \(X_{ie}^{c1}\) and \(C_2\) i.e. \(X_{ie}^{c2}\) have been computed as follows:
  - \(X_{ie}^{c1} = X_i + \mu_{c1}(X_i) \cdot K_1,\)
  - \(X_{ie}^{c2} = X_i \cdot \mu_{c2}(X_i) + (E - \mu_{c2}(X_i) \cdot K_2)\) (2)
  - if (\(X_{ie}^{c1}\) or \(X_{ie}^{c2} > 255\)) then normalization has been performed.
  - Here \(X_{ie}^{c1}\) and \(X_{ie}^{c2}\) are the enhanced pixel values which are crucially dependent on the parameters \(K_1\) and \(K_2\) which belong to [0, 255] and are optimized by modified DE algorithm.

- 5. Combine both \(X_{ie}^{c1}\) and \(X_{ie}^{c2}\) component and get the enhanced image.

Therefore, the proposed enhancement method clearly reveals that the proper enhancement significantly depends on the associated three parameters which are E, \(K_1\) and \(K_2\) with diverse ranges. The optimal values of these parameters are computed by employing one modified DE algorithm with the help of the combination of FD and QILV as objective function which is discussed in the next section.

## OBJECTIVE FUNCTION

This paper also concentrates on finding one proper objective function to preserve the original brightness of the image. In this study one novel objective function has been proposed to accomplish that necessity. The proposed objective function is the combination of Fractal Dimension (FD) (Al-Kadi, O., S., Watson, D. (2008)) and Quality Index based Local Variance (QILV) (Aja-Fern´andez, S. (2006)).

## Fractal Dimension (FD)

The fractal is based on the self-similarity and the fractal dimension is the quantitative expression of the inherent dimension of the images (Al-Kadi, O., S., Watson, D. (2008)). The basic method of deriving fractal dimension is box-counting method. Box counting is making the whole dimension by figuring out the points within determined box or grid. Mathematically, FD is computed using the following formula:

\( D = \frac{\log N_r}{\log \left( \frac{1}{r} \right)} \)

Where, D is the fractal dimension. Maximum and minimum intensity for each box (2×2) are obtained to sum their difference, which gives the N and r as follows:

\( r = \frac{s}{M} \text{ Where, } M= min (R, C) \)

where s denotes scale factor, R and C denote the number of rows and number of columns respectively when the grid size gets doubled, R and C reduces to half of its original value and above procedure is repeated iteratively until max(R, C) is greater than 2. Linear regression model uses to fit the line from plot log (N) vs. log (1/r) and the slope gives the FD as:

\( log N_r = D log \left( \frac{1}{r} \right) \)

## Quality Index Based on Local Variance (QILV)

QILV is used to measure the structural information of the image (Aja-Fern´andez, S. (2006)). A great amount of the structural information of an image is coded in its local variance distribution. Local variances features of an image can help to compare two images properly. The local variance of an image I is defined as \( Var \left( I_{i,j} \right) = E \left( \left( I_{i,j} - \overline{I_{i,j}} \right)^2 \right) \), being \( \overline{I_{i,j}} = E \left( I_{i,j} \right) \) the local mean of the image. It may be estimated using a weighted neighbourhood \( \eta_{i,j} \) pixel under analysis with respective weights \( \omega_p \) as:

\( Var \left( I_{i,j} \right) = \frac{ \sum_{p \in \eta_{i,j}} \omega_p \left( I_{i,j} - \overline{I_{i,j}} \right)^2 }{ \sum_{p \in \eta_{i,j}} \omega_p } ; \overline{I_{i,j}} = \frac{ \sum_{p \in \eta_{i,j}} \omega_p I_p }{ \sum_{p \in \eta_{i,j}} \omega_p } \quad (6)\)

The estimated local-variance of the image will be used as a quality measure of the structural similarity between two images. The mean of the local variance \(\mu_{V_I}\) is estimated as:

\(\mu_{V_I} = \frac{1}{MN} \sum_{i=1}^M \sum_{j=1}^N Var \left( I_{i,j} \right) \quad (7)\)

The (global) standard deviation of the local variance is defined as:

\(\sigma_{V_I} = \left( \frac{1}{MN-1} \sum_{i=1}^M \sum_{j=1}^N \left( Var \left( I_{i,j} \right) - \mu_{V_I} \right)^2 \right)^{\frac{1}{2}} \quad (8)\)

Finally, the covariance between the variances of two images \(I\) and \(J\) is defined as:

\(\sigma_{V_I V_J} = \frac{1}{MN-1} \sum_{i=1}^M \sum_{j=1}^N \left( Var \left( I_{i,j} \right) - \mu_{V_I} \right) \left( Var \left( J_{i,j} \right) - \mu_{V_J} \right) \quad (9)\)

Quality Index based on Local Variance (QILV) between two images \(I\) and \(J\) as follows:

\( QILV \left( I, J \right) = \frac{ 2 \mu_{V_I} \mu_{V_J} }{ \mu_{V_I}^2 + \mu_{V_J}^2 } \cdot \frac{ 2 \sigma_{V_I} \sigma_{V_J} }{ \sigma_{V_I}^2 + \sigma_{V_J}^2 } \cdot \frac{ \sigma_{V_I V_J} }{ \sigma_{V_I} \sigma_{V_J} } \quad (10)\)

Where, \( 0 < QILV \le 1 \)

The first term of QILV equation carries out a comparison between the mean of the local variance distributions of both images. The second one compares the standard deviation of the local variances. The third term is the one to introduce spatial coherence. To avoid some computational problems with small values, some constants may be added to every term in equation.

Fractal Dimension (FD) measures the roughness of the image. It was reported that local variance distribution gives the information about the structure of the image (Dhal, K. G., Sen, M., Das, S. (2017)). If QILV increases then the structural information of the enhanced image is preserved. Therefore, In order to perform the proper enhancement, the combination of FD and QILV is taken as objective function.

The Objective Function is defined as:

$$Fit\left(E,K_{1}, K_{2}\right)=\left\{\exp\left(FD\right)+\exp\left(QILV\right)\right\}$$

Where, Fit(.) is the objective function. FD and QILV represent the fractal dimension and quality index based on local variance of the corresponding image respectively. exp is the exponential operator. Therefore, from the definition of the objective function it can be easily verified that if the proposed objective function is maximized then the FD and QILV of the corresponding image are maximized i.e. the structural information and original brightness of the images are preserved.

So, the optimization problem has been defined as:

$$\{E_{0}, K_{10}, K_{20}\} = arg[max_{E, K_{1}, K_{2}} \{ Fit\left(E, K_{1}, K_{2}\right) \}]$$

This maximization problem has been solved by employing the modified Chaotic DE which is discussed in the next section.

## CHAOTIC DIFFERENTIAL EVOLUTION (CDE)

In this study one new step size has been employed to control the mutation factor of the Differential Evolution. The methodology behind this step size has been discussed below

$$Step Size (SS_{i}^{t}) = \left| \frac{Fit\left(X_{gbest}^{t}\right) - Fit^{t}\left(X_{i}\right)}{max\left(Fit\left(X_{gbest}^{t}\right), Fit^{t}\left(X_{i}\right)\right)} \right|$$

Where, Fit\left(X_{gbest}^{t}\right) is the fitness value of global best solution up to generation number t. Fit^{t}\left(X_{i}\right) is the fitness value of i^{th} individual at generation number t. It is easily understood that (0 <= SS <= 1). It is also clear that SS performs the main
