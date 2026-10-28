# **Example 8.3.3 (Half-planes).** Let \(\mathcal{F}\) consist of the indicators of all closed half-planes in \(\mathbb{R}^2\). We claim that

$$\operatorname{vc}(\mathcal{F}) = 3.$$

To prove \(\operatorname{vc}(\mathcal{F}) \ge 3\), we need to find a three-point set \(\Lambda \subset \mathbb{R}^2\) that is shattered by \(\mathcal{F}\). Let \(\Lambda\) consist of three points in general position like in Figure 8.6. Each of the \(2^3=8\) binary labelings \(g:\Lambda\to\{0,1\}\) is a restriction of the indicator function of some half-plane. To see this, arrange the half-plane to contain exactly those points of \(\Lambda\) where \(g\) takes value 1. Thus, \(\Lambda\) is shattered.

![](bbox=[0.309, 0.306, 0.749, 0.379])

**Figure 8.6** The proof that VC(half-planes) = 3 in Example 8.3.3 consists of two steps. To show VC \(\ge 3\), we find a three-point set \(\Lambda\) on which every binary labeling \(g\) is linearly separable (left). To show VC \(<4\), we demonstrate that on any four-point set \(\Lambda\) there exists a binary labeling \(g\) that is not linearly separable (middle and right).

To prove \(\operatorname{vc}(\mathcal{F}) < 4\), we need to show that no four-point set can be shattered by \(\mathcal{F}\). There are two possible configurations of four-point sets \(\Lambda\) in general position, shown in Figure 8.6. (What if \(\Lambda\) is not in general position? Analyze this case.) In each of the two cases, there exists a binary labeling such that no half-plane can contain exactly the points labeled 1; see Figure 8.6. This means that always exists a binary labeling \(g:\Lambda\to\{0,1\}\) that is not a restriction of any indicator of a half-plane, and thus \(\Lambda\) is not shattered.

# **Example 8.3.4.** Let \(\Omega=\{1,2,3\}\). We can conveniently represent Boolean functions on \(\Omega\) as binary strings of length three. Consider the class

$$\mathcal{F}:=\{001,010,100,111\}.$$

The set \(\Lambda=\{1,3\}\) is shattered by \(\mathcal{F}\). Indeed, restricting the functions in \(\mathcal{F}\) onto \(\Lambda\) amounts to dropping the second digit, thus producing strings 00, 01, 10, 11. Thus, the restriction produces all possible binary strings of length two, or equivalently, all possible binary labelings \(g:\Lambda\to\{0,1\}\). Hence \(\Lambda\) is shattered by \(\mathcal{F}\), and thus \(\operatorname{vc}(\mathcal{F})\ge |\Lambda|=2\). On the other hand, the (only) three-point set \(\{1,2,3\}\) is not shattered by \(\mathcal{F}\), as this would require all eight binary digits of length three to appear in \(\mathcal{F}\), which is not true.

For more practice, find the VC dimension of pairs of intervals, circles, rectangles, squares, and polygons (Exercises 8.12–8.16), and also try Exercise 8.17 to extend Example 8.3.3 to higher dimensions like this: