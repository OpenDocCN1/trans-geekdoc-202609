Before we prove Theorem 6.5.1, note that the recovery error

$$\frac{1}{n}\|\hat{X} - X\|_F = \left(\frac{1}{n^2}\sum_{i,j=1}^n |\hat{X}_{ij} - X_{ij}|^2\right)^{1/2}.$$

represents the average error per entry (in the $L^2$ sense). If we choose the average number of observed entries $m$ so that

$$m \ge C' r n \log n$$

with large constant $C'$, then Theorem 6.5.1 guarantees that the average error is much smaller than $\|X\|_\infty$. So, *matrix completion is possible if the number of observed entries exceeds $rn$ by a logarithmic margin.*

*Proof* We first bound the recovery error in the operator norm, and then pass to the Frobenius norm using the low rank assumption.

# **Step 1: Bounding the error in the operator norm.** Using the triangle inequality, we can split the error as follows:

$$\|\hat{X} - X\| \le \|\hat{X} - p^{-1}Y\| + \|p^{-1}Y - X\|.$$

Since we have chosen $\hat{X}$ as a best rank $r$ approximation to $p^{-1}Y$, the second summand dominates, i.e. $\|\hat{X} - p^{-1}Y\| \le \|p^{-1}Y - X\|$, so we have

$$\|\hat{X} - X\| \le 2\|p^{-1}Y - X\| = \frac{2}{p}\|Y - pX\|. \tag{6.17}$$

Note that the matrix $\hat{X}$, which is tricky to handle, is gone the bound. Instead, we get $Y - pX$, which is easier to understand since its entries,

$$ (Y - pX)_{ij} = (\delta_{ij} - p)X_{ij}, $$

are independent, mean-zero random variables. Using Theorem 6.4.1 (more precisely, its non-symmetric version, see Exercise 6.28), we get

$$\mathbb{E}\|Y - pX\| \le C\sqrt{\log n}\left(\mathbb{E}\max_{i\le n}\|(Y - pX)_{i:}\|_2 + \mathbb{E}\max_{j\le n}\|(Y - pX)_{:j}\|_2\right). \tag{6.18}$$

To bound the norms of the rows of $Y - pX$, we write them as

$$\|(Y - pX)_{i:}\|_2^2 = \sum_{j=1}^n (\delta_{ij} - p)^2 X_{ij}^2 \le \sum_{j=1}^n (\delta_{ij} - p)^2 \cdot \|X\|_\infty^2,$$

and similarly for columns. These sums of independent random variables can be easily bounded using Bernstein (or Chernoff) inequality, which yields

$$\mathbb{E}\max_{i\in[n]}\sum_{j=1}^n (\delta_{ij} - p)^2 \lesssim p n.$$

(Do this calculation yourself in Exercise 6.30!) Combining with a similar bound for the columns and substituting into (6.18), we obtain

$$\mathbb{E}\|Y - pX\| \lesssim \sqrt{p n \log n}\,\|X\|_\infty.$$