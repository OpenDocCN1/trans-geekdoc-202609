
values is determined. With a small amount of noise, the dN < 0.005 value can be used.

Since for 19 per cent < pN < 30 per cent, the value dN < 0.0634, but at higher pN values the noise removal algorithm is not effective. The upper boundary of the range values of the permissible error dN should be close to 0.07. These graphics confirms these values when used for noise control of the matrix 5x5. With software modelling of the processes of image preprocessing and image recognition based on PST the dN range from 0 to 0.2 is used.

## 6.3 Determination of Values Range of Acceptable Error Used in Comparison of Integral Coefficients

In the process of comparing the integral ratios on the stage of image recognition by the method of analysis of the functions of the area of intersection, the dk value of permissible error is used. The need to use this parameter is determined by the fact that in calculating the basic parameters of the function of the area of intersection or in the construction of their basic functions for simple shapes, certain data rounding off is done. It leads to the fact that the expected data are different from the real values. For all types of recognised images, the noise removal process is used. This fact also influences further calculations because some parts of useful information can be deleted. In addition, data losses occur as a result of processing the input information arrays.

The basis for determining the amount of allowable error dk is in the range of the integral coefficient values. The integral coefficients (k_φ) take the values from 0 to 0.5. Furthermore, efficient use of these parameters is caused by the opportunity to separate the general-class patterns (A) into several subclasses (A_i), in order to restrict the number of patterns for further detailed comparison of the function of the area of intersection. The number of subclasses (nA_i) is determined from the following formula:

```
nA_i = \frac{0.5}{2 \cdot dk} = \frac{1}{4 \cdot dk} \quad (6.10)
```

Separation of the pattern into subclasses is quite conditional and depends on the integral values of the coefficients k_φ. Graphically the selection of ranges of k_φ values is reflected in Fig. 6.2.

For maximum efficiency of the integral factors in the image recognition process, the number of subclasses nA_i should be maximally large. Accordingly, the dk value should approach zero. In this case, for a detailed comparison of the functions, the smallest number of patterns is transferred. According to (6.10) the value of allowable error dk cannot exceed 0.25. This statement is valid where there is only one class of

![](img/d6ed6c69a61b1252a9084096bb4904c6_106_0.png)

Fig. 6.2: Formation of ranges of subclasses of integral coefficients based on permissible accuracy dk

templates (nA_i = 1). With increase in the number of subclasses nA_i the required value of this parameter will only decrease.

With technical implementation of the pattern recognition system based on PST, the calculation roundings, loss of data and other information distortion are possible. These factors limit the values of this error. Due to the mentioned circumstances, the formula for real integral factors will change slightly.

```
k_{xN} = \frac{kNc \cdot \frac{S_0}{S_A} \cdot X_{max} + \int_{0}^{X_{max}} FAI(x)dx}{(S_0 + kNc)X_{max}}
```

where k_{xN} is the real integral coefficient for the x direction in the presence of noise in the image, kNc is the amount of noise elements that are not deleted and S_A is the total area of the receptor field.

Then the value is

```
dk \ge |k_{xN} - k_x|
```

After transformation, this formula takes the following form:

```
dk \ge \left| \frac{kNc}{S_A} \right| \left| \frac{S_A - S_0}{2S_0 + \frac{kNc}{S_A}S_A} \right| .
```

The data of normalised values of the number of elements that are not removed in the process of noise control using 3x3 matrix can be taken from Fig. 6.1a. The ratio of area of the receptor field to the area of the image will be called rS.

```
rS = \frac{S_A}{S_0} .
```

The graphic form of the permissible error $dk$ values depending on the $rS$ parameter values when $pN = 17$ per cent is shown in Fig. 6.3.

![](img/d6ed6c69a61b1252a9084096bb4904c6_107_0.png)

Fig. 6.3: The possible $dk$ values depending on the $rS$ parameter

In the process of software simulation for testing the $dk$ values ranging from 0 to 0.04 is used and which correspond to the calculated values for $pN < 30$ and $rS \le 4$. Value at $rS$ calculations is selected for organisation of cyclic shift in two orthogonal directions and the object dimensions in each of them shall be no more than half the size of the receptor field.

## 6.4 Determination of Range Values of Acceptable Error in Comparison of FAI on a Detailed Stage of the Analysis of Image Recognition

On the detailed stage of pattern recognition by the method of analysing the functions of the area of intersection, the acceptable error $dS$ is used. At this stage, a comparison of the actual results and standard functions crossing areas with a given accuracy $dS$ is performed. The necessity to use this parameter is caused by similar circumstances that require the application of allowable $dk$ error.

For the lower bound of the range of possible values, this parameter depends on the changes that appear in the image due to the influence of the noise removal process.

```
dS > \frac{|FAI(x)_N - FAI(x)|}{S_0}, \quad (6.15)
```

where $FAI(x)_N$ is the value of the function of the area of intersection of image, which was corrected by noise removal element process.

The calculated data of the allowable errors $dS$ for simple shapes with $pN = 30$ per cent in Table 6.2 are shown. The data are based on the maximum values of the $rS$ parameter, which was used in software simulation.

| Name of the simple figure | rS | dS |
| :--- | :--- | :--- |
| Triangle | ≈ 10 | ≈ 0.16 |
| Circle | ≈ 5 | ≈ 0.1 |
| Square/rectangle | ≈ 4 | ≈ 0.08 |

From the data table it follows that the value of the acceptable margin of error, which is used in the comparison functions of the area of intersection of the simple shapes with pN = 30 per cent, must be greater than 0.16. However, at lower noise levels, a given value may be smaller. In the software simulation process for testing, the dS value range from 0 to 0.8 is used for the possibility to investigate the recognition efficiency depending on the value of this parameter.

Values of permissible errors were calculated to approximate initial evaluation of these parameters when building software models of the image recognition processes through methods based on the parallel shift technology. Various studies on the efficiency of these methods have been carried out, using a software simulation.

## 6.5 Evaluating the Effectiveness of Image Recognition Process in Various Parameters of Input Information Using Calculated Values of Permissible Errors

To evaluate the effectiveness of the image recognition process with different parameters of input information, it is necessary to define the type of errors, the occurrence of which is possible in this process.

As the first kind of mistake, we shall consider the case when the figure is in the database of templates, but in the process of identification, is assigned to the class of images, consisting of more than one element, and in this class is included the figure that is being recognised. A typical example of an error of this kind is optional, when the parameters of permissible errors are selected incorrectly.

The second kind of error will be called in a situation when the figure is in the template database, but on the detailed step of identification it is assigned to the image class, which does not contain the given image. The main cause of error appearance of this kind is a high noise level. The negative influence of this noise cannot be deleted by the chosen method of noise removal.

The third kind of error occurs when there is a figure-based template, but is not found in the database.

On the basis of the calculated parameter of permissible errors, recognition of simple shapes was carried out to determine the effectiveness
