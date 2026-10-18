

我们也有相同的测试，使用 Python 编写，分别在 [方案 2.19](#c02.xhtml#c02-gra-00019) 中展示了 2005 年至 2007 年的数据，在 [方案 2.20](#c02.xhtml#c02-gra-00020) 中展示了 2018 年至 2020 年的数据。生成的图表分别在 [图 2.9](#c02.xhtml#c02-fig-0009) 和 [2.10](#c02.xhtml#c02-fig-0010) 中展示。

![](images/c02-gra-0028.png)![](images/c02-gra-0029.png)![](images/c02-gra-0030.png) ![图 2.9 2005 年至 2007 年三个股票市场指数的箱线图、均值图和 Tukey HSD 图（Python）。](images/c02f009.png)

[**图 2.9**](#c02.xhtml#R_c02-fig-0009) 2005 年至 2007 年三个股票市场指数的箱线图、均值图和 Tukey HSD 图（Python）。

 ![图 2.10 2018 年至 2020 年三个股票市场指数的箱线图、均值图和 Tukey HSD 图（Python）。](images/c02f010.png)

[**图 2.10**](#c02.xhtml#R_c02-fig-0010) 2018 年至 2020 年三个股票市场指数的箱线图、均值图和 Tukey HSD 图（Python）。

最后，在方案 2.21 和 2.22 中通过 `R`（分别在方案 2.23 和 2.24 中通过 Python），我们基于 ([2.2](#c02.xhtml#c02-disp-0008)) 复制了 `R` 中的 `tukey.test` 结果（分别在 Python 中的 `tukeyhsd`）。我们首先计算各个样本均值 ![mu Subscript SPX](images/c02-i0077.png)<math display="inline" overflow="scroll"><msub><mi>&#956;</mi><mtext>SPX</mtext></msub></math>、![mu Subscript FTSE](images/c02-i0078.png)<math display="inline" overflow="scroll"><msub><mi>&#956;</mi><mtext>FTSE</mtext></msub></math>、![mu Subscript HSI](images/c02-i0079.png)<math display="inline" overflow="scroll"><msub><mi>&#956;</mi><mtext>HSI</mtext></msub></math>、各个平方误差和 ![SSE Subscript SPX](images/c02-i0080.png)<math display="inline" overflow="scroll"><msub><mtext>SSE</mtext><mtext>SPX</mtext></msub></math>、![SSE Subscript FTSE](images/c02-i0081.png)<math display="inline" overflow="scroll"><msub><mtext>SSE</mtext><mtext>FTSE</mtext></msub></math>、![SSE Subscript HSI](images/c02-i0082.png)<math display="inline" overflow="scroll"><msub><mtext>SSE</mtext><mtext>HSI</mtext></msub></math>，以及总自由度（![upper N minus StartAbsoluteValue script upper C EndAbsoluteValue equals upper N Subscript SPX Baseline plus upper N Subscript FTSE Baseline plus upper N Subscript HSI Baseline minus 3 equals 2 comma 184](images/c02-i0083.png)<math display="inline" overflow="scroll"><mi>N</mi><mo>&#8722;</mo><mfenced open="|" close="|" separators=""><mrow><mi mathvariant="script">C</mi></mrow></mfenced><mo>=</mo><msub><mi>N</mi><mtext>SPX</mtext></msub><mo>+</mo><msub><mi>N</mi><mtext>FTSE</mtext></msub><mo>+</mo><msub><mi>N</mi><mtext>HSI</mtext></msub><mo>&#8722;</mo><mn>3</mn><mo>=</mo><mn>2</mn><mo>,</mo><mn>184</mn></math> 用于 2005 年至 2007 年期间，以及 ![upper N minus StartAbsoluteValue script upper C EndAbsoluteValue equals 2 comma 117](images/c02-i0084.png)<math display="inline" overflow="scroll"><mi>N</mi><mo>&#8722;</mo><mfenced open="|" close="|" separators=""><mrow><mi mathvariant="script">C</mi></mrow></mfenced><mo>=</mo><mn>2</mn><mo>,</mo><mn>117</mn></math> 用于 2018 年至 2020 年期间）。然后，我们计算组内均方误差，定义为 ![MSE Subscript within Baseline equals SSE Subscript within Baseline slash left-parenthesis upper N minus StartAbsoluteValue script upper C EndAbsoluteValue right-parenthesis equals left-parenthesis SSE Subscript SPX Baseline plus SSE Subscript FTSE Baseline plus SSE Subscript HSI Baseline right-parenthesis slash left-parenthesis upper N minus StartAbsoluteValue script upper C EndAbsoluteValue right-parenthesis](images/c02-i0085.png)<math display="inline" overflow="scroll"><msub><mtext>MSE</mtext><mtext>within</mtext></msub><mo stretchy="false">/</mo><mo stretchy="false">(</mo><mi>N</mi><mo>&#8722;</mo><mfenced open="|" close="|" separators=""><mrow><mi mathvariant="script">C</mi></mrow></mfenced><mo stretchy="false">)</mo><mo>=</mo><mo stretchy="false">(</mo><msub><mtext>SSE</mtext><mtext>SPX</mtext></msub><mo>+</mo><msub><mtext>SSE</mtext><mtext>FTSE</mtext></msub><mo>+</mo><msub><mtext>SSE</mtext><mtext>HSI</mtext></msub><mo stretchy="false">)</mo><mo stretchy="false">/</mo><mo stretchy="false">(</mo><mi>N</mi><mo>&#8722;</mo><mfenced open="|" close="|" separators=""><mrow><mi mathvariant="script">C</mi></mrow></mfenced><mo stretchy="false">)</mo></math>。在 `R` 和 Python 中，![MSE Subscript within](images/c02-i0086.png)<math display="inline" overflow="scroll"><msub><mtext>MSE</mtext><mtext>within</mtext></msub></math> 都记录在单因素方差分析的汇总表中；在 `R` 中，对于 [方案 2.17](#c02.xhtml#c02-gra-00017)（2005 年至 2007 年）（分别 [方案 2.18](#c02.xhtml#c02-gra-00018）用于 2018 年至 2020 年），它直接在 `Residuals` 的 `Mean Sq` 中给出；在 Python 中，对于 [方案 2.19](#c02.xhtml#c02-gra-00019)（2005 年至 2007 年）（分别 [方案 2.20](#c02.xhtml#c02-gra-00020）用于 2018 年至 2020 年），可以通过将 `Residual` 的 `sum_sq` 除以 `df` 来计算。`R` 中的 `ptukey()` 函数（分别 Python 中的 `psturng()` 函数）计算 Tukey HSD 检验的概率 ![double-struck upper P left-parenthesis q Subscript Tukey comma i j Baseline greater-than q right-parenthesis](images/c02-i0087.png)<math display="inline" overflow="scroll"><mi mathvariant="double-struck">P</mi><mo stretchy="false">(</mo><msub><mi>q</mi><mrow><mtext>Tukey</mtext><mo>,</mo><mi>i</mi><mi>j</mi></mrow></msub><mo>&#62;</mo><mi>q</mi><mo stretchy="false">)</mo></math>，给定 (i) 分位数值 `q`；(ii) `R` 中的组数 `nmeans`（分别 Python 中的 `r`）；以及 `R` 中的自由度 `df`（分别 Python 中的 `v`）。

![](images/c02-gra-0031.png)![](images/c02-gra-0032.png) ![](images/c02-gra-0033.png)![](images/c02-gra-0034.png) ![](images/c02-gra-0035.png)

注意，由 Python `statsmodels` 库提供的 `tukeyhsd` 和 `qsturng` 计算的 Tukey HSD 检验的 ![p](images/c02-i0088.png)<math display="inline" overflow="scroll"><mrow><mi>p</mi></mrow></math>\-p 值略有不同，无论哪个时间段（2005–2007 或 2018–2020）。数值差异是由于 `psturng` 中使用的求解器 `fminbound` 无法准确定位最小化器。因此，我们建议读者在实际操作中直接使用 Python 的 `tukeyhsd` 函数进行 Tukey HSD 检验。

## 参考文献

1.  1.  Berry, A.C. (1941). The accuracy of the Gaussian approximation to the sum of independent variates. Transactions of the American Mathematical Society, 49(1), 122–136.

2.  2.  Crawley, M.J. (2012). The R Book. Wiley.

3.  3.  Esseen, C.G. (1942). On the Liapunov limit error in the theory of probability. Arkiv för matematik, astronomi och fysik, 28, 1–19.

4.  4.  Kabacoff, R.I. (2022). R in Action: Data Analysis and Graphics with R (3rd ed.). Manning Publications Company.

5.  5.  Lutz, M. (2013). Learning Python: Powerful Object-Oriented Programming. O'Reilly Media, Inc.

6.  6.  McKinney, W. (2022). Python for Data Analysis (3rd ed.). O'Reilly Media, Inc.

7.  7.  Timm, N.H. (Ed.). (2002). Applied Multivariate Analysis. Springer.

8.  8.  Tukey, J.W. (1949). Comparing individual means in the analysis of variance. Biometrics, 5(2), 99–114.

9.  9.  Tukey, J.W. (1972). Some graphic and semigraphic displays. Statistical Papers in Honor of George W. Snedecor, 5, 293–316.

10.  10. Wong, W.K., Wright, J.A., Yam, S.C.P., and Yung, S.P. (2012). A mixed Sharpe ratio. Risk and Decision Analysis, 3(1–2), 37–65.

11.  11. Wright, J.A., Yam, S.C.P., and Yung, S.P. (2014). A test for the equality of multiple Sharpe ratios. The Journal of Risk, 16(4), 3.

## 注释

1.  [1](#c02.xhtml#R_c02-note-0001) Pixar Animation Studios，`The Walt Disney Company` 的子公司。公司网站：[https://www.pixar.com/](https://www.pixar.com/)。

