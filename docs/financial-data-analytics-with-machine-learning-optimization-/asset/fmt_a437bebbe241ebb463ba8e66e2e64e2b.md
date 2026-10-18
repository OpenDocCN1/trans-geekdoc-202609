
### 31. Thorp, E.O. (2008)
The Kelly criterion in blackjack sports betting, and the stock market. In *Handbook of Asset and Liability Management* (pp. 385–428). North-Holland.

### 32. Tse, Y.K., and Tsui, A.K.C. (2002)
A multivariate generalized autoregressive conditional heteroscedasticity model with time-varying correlations. Journal of Business & Economic Statistics, 20(3), 351–362.

### 33. Van der Vaart, A.W., and Wellner, J.A. (1996)
Weak Convergence and Empirical Processes with Applications to Statistics. Springer.

### 34. Van der Vaart, A.W. (2000)
Asymptotic Statistics (Vol. 3). Cambridge University Press.

### 35. Varadhan, S.S. (2001)
*Probability Theory* (No. 7). American Mathematical Society.

### 36. Yam, S.C.P., Yung, S.P., and Zhou, W. (2009)
Two rationales behind the ‘buy-and-hold or sell-at-once’ strategy. Journal of Applied Probability, 46(3), 651–668.

### 37. Yam, S.C.P., Yung, S.P., and Zhou, W. (2012)
Optimal selling time in stock market over a finite time horizon. Acta Mathematicae Applicatae Sinica, English Series, 28(3), 557–570.

### 38. Yam, S.C.P., Yung, S.P., and Zhou, W. (2013)
A unified “Bang-Bang” principle with respect to R-invariant performance benchmarks. Theory of Probability & Its Applications, 57(2), 357–366.

### 39. Zhang, M. (2018)
Time series: Autoregressive models – AR, MA, ARMA, ARIMA. University of Pittsburgh.

## NOTES

1. [1](#c07.xhtml#R_c07-note-0001) *Hongkong and Shanghai Banking Corporation* (HSBC) is a British multinational universal bank founded in 1865 and has a ticker symbol of 0005 in Stock Exchange of Hong Kong (SEHK).

2. [2](#c07.xhtml#R_c07-note-0002) *China Light and Power* (CLP) Hong Kong Ltd is a Hong Kong electricity company founded in 1901 and has a ticker symbol of 0002 in Stock Exchange of Hong Kong (SEHK).

3. [3](#c07.xhtml#R_c07-note-0003) *Cheung Kong* (CK) is a Hong Kong multi-national conglomerate founded in 1972 and has a ticker symbol of 0001 in Stock Exchange of Hong Kong (SEHK).

4. [4](#c07.xhtml#R_c07-note-0004) Likewise, the same philosophy can also be seen for the sampling distribution of variance of a normal sample, namely ![sigma-summation Underscript i equals 1 Overscript n Endscripts StartFraction left-parenthesis normal x Subscript i Baseline minus normal x overbar right-parenthesis squared Over sigma squared EndFraction tilde chi Subscript n minus 1 Superscript 2](images/c07-i0156.png)<math display="inline" overflow="scroll"><msubsup><mrow><mo>&#8721;</mo></mrow><mrow><mi>i</mi><mo>=</mo><mn>1</mn></mrow><mrow><mi>n</mi></mrow></msubsup><mfrac><mrow><msup><mrow><mo stretchy="false">(</mo><msub><mi mathvariant="normal">x</mi><mi>i</mi></msub><mo>&#8722;</mo><mover accent="true"><mi mathvariant="normal">x</mi><mo>&#175;</mo></mover><mo stretchy="false">)</mo></mrow><mn>2</mn></msup></mrow><mrow><msup><mi>&#963;</mi><mn>2</mn></msup></mrow></mfrac><mo>&#8764;</mo><msubsup><mrow><mi>&#967;</mi></mrow><mrow><mi>n</mi><mo>&#8722;</mo><mn>1</mn></mrow><mrow><mn>2</mn></mrow></msubsup></math> (see [Section 1.4](#c01.xhtml#head-2-8)), while ![sigma-summation Underscript i equals 1 Overscript n Endscripts StartFraction left-parenthesis normal x Subscript i Baseline minus mu right-parenthesis squared Over sigma squared EndFraction tilde chi Subscript n Superscript 2](images/c07-i0157.png)<math display="inline" overflow="scroll"><msubsup><mrow><mo>&#8721;</mo></mrow><mrow><mi>i</mi><mo>=</mo><mn>1</mn></mrow><mrow><mi>n</mi></mrow></msubsup><mfrac><mrow><msup><mrow><mo stretchy="false">(</mo><msub><mi mathvariant="normal">x</mi><mi>i</mi></msub><mo>&#8722;</mo><mi>&#956;</mi><mo stretchy="false">)</mo></mrow><mn>2</mn></msup></mrow><mrow><msup><mi>&#963;</mi><mn>2</mn></msup></mrow></mfrac><mo>&#8764;</mo><msubsup><mrow><mi>&#967;</mi></mrow><mrow><mi>n</mi></mrow><mrow><mn>2</mn></mrow></msubsup></math>, due to the extra linear constraint that ![sigma-summation Underscript i equals 1 Overscript n Endscripts left-parenthesis normal x Subscript i Baseline minus normal x overbar right-parenthesis equals 0](images/c07-i0158.png)<math display="inline" overflow="scroll"><msubsup><mrow><mo>&#8721;</mo></mrow><mrow><mi>i</mi><mo>=</mo><mn>1</mn></mrow><mrow><mi>n</mi></mrow></msubsup><mo stretchy="false">(</mo><msub><mi mathvariant="normal">x</mi><mi>i</mi></msub><mo>&#8722;</mo><mover accent="true"><mi mathvariant="normal">x</mi><mo>&#175;</mo></mover><mo stretchy="false">)</mo><mo>=</mo><mn>0</mn></math> imposed in replacing the theoretical mean ![mu](images/c07-i0159.png)<math display="inline" overflow="scroll"><mrow><mi>&#956;</mi></mrow></math> by the sample mean ![normal x overbar](images/c07-i0160.png)<math display="inline" overflow="scroll"><mover accent="true"><mi mathvariant="normal">x</mi><mo>&#175;</mo></mover></math>.

5. [5](#c07.xhtml#R_c07-note-0005) We adopt the Nelder–Mead method since it is the only option in `constrOptim()` which does not require the specification of gradient function `grad`.

6. [6](#c07.xhtml#R_c07-note-0006) Different from ARIMA model diagnostics, the sample ACF ![r Subscript k](images/c07-i0275.png)<math display="inline" overflow="scroll"><msub><mi>r</mi><mi>k</mi></msub></math>'s of fitted residuals here are subject to a set of possibly non-linear constraints, say ![psi Subscript j Baseline left-parenthesis r 1 comma ellipsis comma r Subscript upper T Baseline right-parenthesis equals 0](images/c07-i0276.png)<math display="inline" overflow="scroll"><msub><mi>&#968;</mi><mi>j</mi></msub><mo stretchy="false">(</mo><msub><mi>r</mi><mn>1</mn></msub><mo>,</mo><mo>&#8230;</mo><mo>,</mo><msub><mi>r</mi><mi>T</mi></msub><mo stretchy="false">)</mo><mo>=</mo><mn>0</mn></math> for ![j equals 1 comma ellipsis comma upper J](images/c07-i0277.png)<math display="inline" overflow="scroll"><mi>j</mi><mo>=</mo><mn>1</mn><mo>,</mo><mo>&#8230;</mo><mo>,</mo><mi>J</mi></math>, where ![upper J equals p plus q plus 1](images/c07-i0278.png)<math display="inline" overflow="scroll"><mi>J</mi><mo>=</mo><mi>p</mi><mo>+</mo><mi>q</mi><mo>+</mo><mn>1</mn></math> is the number of estimated parameters in a GARCH(![p comma q](images/c07-i0279.png)<math display="inline" overflow="scroll"><mi>p</mi><mo>,</mo><mi>q</mi></math>) model. Nevertheless, ![r Subscript k](images/c07-i0280.png)<math display="inline" overflow="scroll"><msub><mi>r</mi><mi>k</mi></msub></math>'s are close to their respective true population values when the sample size ![n](images/c07-i0281.png)<math display="inline" overflow="scroll"><mrow><mi>n</mi></mrow></math> is large, then by Taylor expansion (a perturbation analytical approach, see [\[4](#c07.xhtml#c07-bib-0003), [33](#c07.xhtml#c07-bib-0031), [34\]](#c07.xhtml#c07-bib-0032)), these ![psi Subscript j](images/c07-i0282.png)<math display="inline" overflow="scroll"><msub><mi>&#968;</mi><mi>j</mi></msub></math>'s are dominated by their respective zeroth- and first-order terms, and hence we arrive at ![upper J](images/c07-i0283.png)<math display="inline" overflow="scroll"><mrow><mi>J</mi></mrow></math> approximate linear constraints similar to the ARIMA case. That is why the asymptotic distribution of the corresponding test statistic, when applied to fitted residuals, is again a chi-square distribution with ![upper K minus upper J](images/c07-i0284.png)<math display="inline" overflow="scroll"><mi>K</mi><mo>&#8722;</mo><mi>J</mi></math> degrees of freedom; readers may refer to \[[1](#c07.xhtml#c07-bib-1001), [5](#c07.xhtml#c07-bib-0004), [20](#c07.xhtml#c07-bib-0019), [21](#c07.xhtml#c07-bib-1019)\] for more discussions on this issue.
