q = \frac{1}{\text{Max}_{1 \le i \le n} \sum_{j=1}^{n} x_{ij}} \quad (3.5)

G = q \times D \quad (3.6)

where M is the preliminary combined direct relation matrix n×n, and q is a group of dimensions that distinguishes by pairwise comparison to describe the significance of the dimensions.

**Step 8:** Compute the total relation matrix (T) for all dimensions by applying Eq. (3.7).

T = G \times (I - G)^{-1} \quad (3.7)

where I is the identity matrix, and the element t_{ij} symbolizes the unintended effects that element i has on j. Thus, T can designate the total relation matrix of each pair of system influences.

**Step 9:** Establish the influential relation map (IRM); the sum of rows and columns is obtained from the matrix T, expressed as R and C, respectively, in Eqs. (3.8) and (3.9). Then, we can compute the horizontal axis vector R+C, and the vertical axis vector R−C. the IRM will be obtained by computing the ordered pairs (R+C, R−C).

T = [t_{ij}]_{n×n}, i, j = 1, 2, ..., n.

R = [\sum_{i=1}^{n} t_{ij}]_{1×n} \quad (3.8)

C = [\sum_{j=1}^{n} t_{ij}]_{n×1} \quad (3.9)

where R and C indicate the total rows and columns of the total-influence matrix, respectively. R and C indicate the total sum of rows and columns of the total-influence matrix i^{th} dimension, respectively.

**Step 10:** Compute the weights of the main dimensions D1, D2, ..., Dn based on the R and C that resulting from expert opinions. Accordingly, R+C should be normalized. The value of R+C has been divided by the total of R+C values as exhibited in Eq. (3.10).

w = \frac{R + C}{\sum_{i=1}^{n} R + C} \quad (3.10)