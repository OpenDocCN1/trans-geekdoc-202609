
$$p\\left( x\\_{1},...,x\\_{k} \\right) = \\frac{n!}{x\\_{1}!x\\_{2}!...x\\_{k}{}\_{!}}\\pi\\_{1}^{x\\_{1}}\\pi\\_{2}^{x\\_{2}}...\\pi\\_{k}^{x\\_{k}}$$
(2.26)
where now `π`[1]^(`x`[1])`π`[2]^(`x`[2])...`π`[`k`]^(`x`[`k`]) are the different probabilities associated with individual events `x`[1], `x`[2],`x`[`k`]. That is, instead of having only two possibilities on the discrete variable (binomial), the variable now has several possibilities, each having their own respective probabilities, `π`[1], `π`[2], … `π`[`k`].

## 2.18 Poisson Distributions
The Poisson density is given by
$$p\\left( x/\\mu \\right) = \\frac{e^{- \\mu}\\mu^{x}}{x!}$$
(2.27)
where `e` is a constant and `x` is the number of events occurring in a fixed interval of time. The expectation (i.e., mean) of the Poisson density and that of its variance are both equal to `μ`. For further details on the Poisson density, see Casella and Berger ([2002](#ref.xhtml#re_CIT000055), p. 92).

## 2.19 Chi-Square Distributions
The chi-square density is given by
$$f\\left( x \\right) = \\frac{1}{2^{v/2}\\Gamma\\left( v/2 \\right)}x^{\\lbrack(v/2) - 1\\rbrack}e^{- x/2}$$
(2.28)
where `Γ` is the gamma function and `v` are the degrees of freedom of the density. The chi-square distribution of a random variable is equal to the sum of squares of `n` independent and normally distributed `z`\-scores (see [Fisher, 1922](#ref.xhtml#re_CIT000099) for details):
$$\\chi\_{n}^{2} = {\\sum\\limits\_{i = 1}^{n}z\_{i}^{2}} = {\\sum\\limits\_{i = 1}^{n}\\frac{\\left( x\_{i} - \\mu \\right)^{2}}{\\sigma^{2}}}$$
A final thought on statistical distributions and densities. Not surprisingly, there are many more than we have highlighted here in our brief review. Most times, the type of problem you are modeling will quite naturally dictate or strongly suggest the density you should use to model the given phenomenon. The key is recognizing from the problem you are facing which statistical distribution might be most `appropriate`. Such insight can be difficult and often depends on relying on one’s experience or expertise in the given substantive area. It is not unusual, however, for an analyst to spend some time contemplating which density would be best in modeling this or that phenomenon, especially when the problem is difficult.

## 2.20 Expectation and Expected Value
When we talk about “expectation” in statistics, we are generally referring to the long-run average behavior of a random variable. Since we are dealing with a random variable, this idea necessarily invokes and implies the `probability` concept. The expected value of a function `g` is the sum (or 86integral) of that function multiplied by its corresponding probability, for a continuous random variable,
$$E\_{X}\\left\\lbrack g\\left( x \\right) \\right\\rbrack = {\\int\\limits\_{x}{g\\left( x \\right)p\\left( x \\right)dx}}$$
(2.29)
For a discrete random variable, the expectation is
$$E\_{X}\\left\\lbrack g\\left( x \\right) \\right\\rbrack = {\\sum\\limits\_{x}{g\\left( x \\right)p\\left( x \\right)}}$$
(2.30)
The expectation for a discrete variable is different from that of a continuous variable since, with a discrete one, we can assign individual probabilities to values of the variable and sum up products, `g`(`x`)`p`(`x`). With a continuous variable, products are technically also summed, but they require integral calculus to do the summation and not simply sigma as in the discrete case.
We can compute expected values of single random variables as above, but we can also compute expected values of elements of vectors and matrices as well. The expectation of a random matrix is the expectation of each of its random variables,
$$E\\left( X \\right) = \\left\\lbrack \\begin{array}{l} {E\\left( x\_{11} \\right)\\,\\,\\,\\,\\, E\\left( x\_{12} \\right)\\,\\,\\,\\,\\, \\cdot \\cdot \\cdot \\,\\,\\,\\,\\, E\\left( x\_{1}{}\_{p} \\right)} \\\\ {E\\left( x\_{21} \\right)\\,\\,\\,\\,\\, E\\left( x\_{22} \\right)\\,\\,\\,\\,\\, \\cdot \\cdot \\cdot \\,\\,\\,\\,\\, E\\left( x\_{2}{}\_{p} \\right)} \\\\ {\\,\\,\\,\\,\\,\\, \\cdot \\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\, \\cdot \\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\, \\cdot} \\\\ {E\\left( x\_{n1} \\right)\\,\\,\\,\\,\\, E\\left( x\_{n2} \\right)\\,\\,\\,\\,\\, \\cdot \\cdot \\cdot \\,\\,\\,\\,\\, E\\left( x\_{n}{}\_{p} \\right)} \\\\ \\end{array} \\right\\rbrack$$
(2.31)
Since `E`(`x`[11]) through to `E`(`x`[`n`][`p`]) is equal to `μ`[11] to `μ`[`n``p`], we can write:
$$E\\left( X \\right) = \\left\\lbrack \\begin{array}{l} {E\\left( x\_{11} \\right)\\,\\,\\,\\,\\, E\\left( x\_{12} \\right)\\,\\,\\,\\,\\, \\cdot \\cdot \\cdot \\,\\,\\,\\,\\, E\\left( x\_{1}{}\_{p} \\right)} \\\\ {E\\left( x\_{21} \\right)\\,\\,\\,\\,\\, E\\left( x\_{22} \\right)\\,\\,\\,\\,\\, \\cdot \\cdot \\cdot \\,\\,\\,\\,\\, E\\left( x\_{2}{}\_{p} \\right)} \\\\ {\\,\\,\\,\\,\\,\\, \\cdot \\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\, \\cdot \\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\, \\cdot} \\\\ {E\\left( x\_{n1} \\right)\\,\\,\\,\\,\\, E\\left( x\_{n2} \\right)\\,\\,\\,\\,\\, \\cdot \\cdot \\cdot \\,\\,\\,\\,\\, E\\left( x\_{n}{}\_{p} \\right)} \\\\ \\end{array} \\right\\rbrack = \\left\\lbrack \\begin{array}{l} {\\mu\_{11}\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\mu\_{12}\\,\\,\\,\\,\\, \\cdot \\cdot \\cdot \\,\\,\\,\\,\\,\\mu\_{1}{}\_{p}} \\\\ {\\mu\_{21}\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\mu\_{22}\\,\\,\\,\\,\\, \\cdot \\cdot \\cdot \\,\\,\\,\\,\\,\\mu\_{2}{}\_{p}} \\\\ {\\,\\,\\,\\, \\cdot \\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\, \\cdot \\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\, \\cdot} \\\\ {\\mu\_{n1}\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\mu\_{n2}\\,\\,\\,\\,\\, \\cdot \\cdot \\cdot \\,\\,\\,\\,\\,\\mu\_{n}{}\_{p}} \\\\ \\end{array} \\right\\rbrack$$
(2.32)

## 2.21 Measures of Central Tendency
Observing every data point in a data set, especially for large data sets, provides a weak summary of that data and we usually wish instead to summarize the data with one or two measures that, in some sense, “represent” the data. We emphasize “in some sense,” because no single measure could ever summarize any data `perfectly`. To understand what central tendency means with regard to a particular measure used, one must understand in some depth the measure, that is, the abstract “idea” of what central tendency might mean. Of course, if the data set consists of only say, 2–3 data points, then inspecting the data set `point by point` is well advised and it makes little sense in trying to reduce such data into a smaller set of summary statistics. Usually, however, our data sets are medium-sized to very large, and graphical or numerical summaries are required in getting to know our data.
Measures of central tendency are `data reduction measures`; they take a set of observations and reduce such data down to a single measure.87

### 2.21.1 The Arithmetic Mean (Average)
The arithmetic mean is without question the most popular measure of central tendency. The arithmetic mean is given by
$$\\overline{x} = \\frac{1}{n}{\\sum\\limits\_{n = 1}^{N}x\_{n}}$$
(2.33)
Note that the arithmetic average consists of summing all observations, and then dividing by how many numbers went into that sum. Hence, the mean is often regarded as the `center of gravity` in a distribution. Since it is the center of gravity, it is also true that the sum of deviations from the mean is equal to 0; that is,
$$\\left. {\\sum\\limits\_{i = 1}^{n}\\left( x\_{i} - \\overline{x} \\right.} \\right) = 0$$
(2.34)
The fact that deviations from the mean sum to zero is one reason why such deviations are typically squared (or absolute values taken under some circumstances) when producing the variance or standard deviation.
For a random variable, the mean is given by
`μ` = ∫[ − ∞]^( + ∞)`x``f`(`x`)`d``x`
