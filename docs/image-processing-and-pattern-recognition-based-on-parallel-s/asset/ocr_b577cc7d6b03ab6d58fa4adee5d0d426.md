The graphic form of the permissible error $dk$ values depending on the $rS$ parameter values when $pN = 17$ per cent is shown in Fig. 6.3.

![](bbox=[0.25, 0.15, 0.75, 0.35])

Fig. 6.3: The possible $dk$ values depending on the $rS$ parameter

In the process of software simulation for testing the $dk$ values ranging from 0 to 0.04 is used and which correspond to the calculated values for $pN < 30$ and $rS \le 4$. Value at $rS$ calculations is selected for organisation of cyclic shift in two orthogonal directions and the object dimensions in each of them shall be no more than half the size of the receptor field.

# ## 6.4 Determination of Range Values of Acceptable Error in Comparison of FAI on a Detailed Stage of the Analysis of Image Recognition

On the detailed stage of pattern recognition by the method of analysing the functions of the area of intersection, the acceptable error $dS$ is used. At this stage, a comparison of the actual results and standard functions crossing areas with a given accuracy $dS$ is performed. The necessity to use this parameter is caused by similar circumstances that require the application of allowable $dk$ error.

For the lower bound of the range of possible values, this parameter depends on the changes that appear in the image due to the influence of the noise removal process.

```
\( dS > \frac{|FAI(x)_N - FAI(x)|}{S_0}, \quad (6.15) \)
```

where $FAI(x)_N$ is the value of the function of the area of intersection of image, which was corrected by noise removal element process.

The calculated data of the allowable errors $dS$ for simple shapes with $pN = 30$ per cent in Table 6.2 are shown. The data are based on the maximum values of the $rS$ parameter, which was used in software simulation.