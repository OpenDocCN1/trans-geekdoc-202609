# Correlation coefficient for numeric data

For numeric attributes, we can evaluate the correlation between two attributes, _A_ and _B_, by computing the **correlation coefficient** (also known as **Pearson's product moment coefficient**, named after its inventor, Karl Pearson). This is

\(r_{A,B} = \frac{\sum_{i=1}^n (a_i - \bar{A})(b_i - \bar{B})}{n \sigma_A \sigma_B} = \frac{\sum_{i=1}^n (a_i b_i) - n \bar{A} \bar{B}}{n \sigma_A \sigma_B},\) (2.9)

where _n_ is the number of tuples, _a<sub>i</sub>_ and _b<sub>i</sub>_ are the respective values of _A_ and _B_ in tuple _i_, \(\bar{A}\) and \(\bar{B}\) are the respective mean values of _A_ and _B_, \(\sigma_A\) and \(\sigma_B\) are the respective standard deviations of _A_ and _B_ (as defined in Section 2.2.2), and \(\Sigma(a_i b_i)\) is the sum of the _AB_ cross-product (i.e., for each tuple, the value for _A_ is multiplied by the value for _B_ in that tuple). Note that \(-1 \le r_{A,B} \le +1\). If _r<sub>A,B</sub>_ is greater than 0, then _A_ and _B_ are **positively correlated**, meaning that the values of _A_ increase as the values of _B_ increase. The higher the value, the stronger the correlation (i.e., the more each attribute implies the other). Hence, a higher value may indicate that _A_ (or _B_) may be removed as a redundancy.

If the resulting value is equal to 0, then _A_ and _B_ are **independent**, and there is no correlation between them. If the resulting value is less than 0, then _A_ and _B_ are **negatively correlated**, where the values of one attribute increase as the values of the other attribute decrease. This means that each attribute discourages the other. Scatter plots can also be used to view correlations between attributes (Section 2.2.3). For example, Fig. 2.8's scatter plots, respectively, show positively correlated data and negatively correlated data, whereas Fig. 2.9 displays uncorrelated data.

Note that correlation does not imply causality. That is, if _A_ and _B_ are correlated, this does not necessarily imply that _A_ causes _B_ or that _B_ causes _A_. For example, in analyzing a demographic database, we may find that attributes representing the number of hospitals and the number of car thefts in a region are correlated. This does not mean that one causes the other. Both are actually causally linked to a third attribute, namely, _population_.

# \(\chi^2\) correlation test for nominal data

For nominal data, a correlation relationship between two attributes, _A_ and _B_, can be discovered by a \(\chi^2\) (**chi-square**) test. Suppose _A_ has _c_ distinct values, namely, _a_<sub>1</sub>, _a_<sub>2</sub>, ... _a<sub>c</sub>_, and _B_ has _r_ distinct values, namely, _b_<sub>1</sub>, _b_<sub>2</sub>, ... _b<sub>r</sub>_. The data tuples described by _A_ and _B_ can be shown as a **contingency table**, with the _c_ values of _A_ making up the columns and the _r_ values of _B_ making up the rows. Let (_A<sub>i</sub>_, _B<sub>j</sub>_) denote the joint event that attribute _A_ takes on value _a<sub>i</sub>_ and attribute _B_ takes on value _b<sub>j</sub>_, that is, where (_A_ = _a<sub>i</sub>_, _B_ = _b<sub>j</sub>_). Each and every possible (_A<sub>i</sub>_, _B<sub>j</sub>_) joint event has its own cell (or slot) in the table. The \(\chi^2\) value (also known as the **Pearson** \(\chi^2\) **statistic**) is computed as

\(\chi^2 = \sum_{i=1}^c \sum_{j=1}^r \frac{(o_{ij} - e_{ij})^2}{e_{ij}},\) (2.10)

where _o<sub>ij</sub>_ is the **observed frequency** (i.e., actual count) of the joint event (_A<sub>i</sub>_, _B<sub>j</sub>_) and _e<sub>ij</sub>_ is the **expected frequency** of (_A<sub>i</sub>_, _B<sub>j</sub>_), which can be computed as

\(e_{ij} = \frac{count(A = a_i) \times count(B = b_j)}{n},\) (2.11)