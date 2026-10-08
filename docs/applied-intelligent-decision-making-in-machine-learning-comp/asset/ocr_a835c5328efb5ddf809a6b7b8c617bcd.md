# An Enhanced Image Dehaz Procedure Using CLAHE and a Guided Filter

# Algorithm 12.2 CLAHE

Input: $Input_{img}$
Output: $Enhanced_{img}$

+   1. Divide the original intensity image into $M$-overlapping contextual regions. The total number of image tiles is equal to $M 	imes N$.
2. Calculating the histogram of each contextual region according to gray levels in the array image.
3. Calculating the contrast adaptive histogram of the contextual region by the Clipped limit value as

```
$N_{average} = (Nx \times Ny) / N_{levels}$
N_{CLIP} = N_{clip} \times N_{gray}$
```

The average number of pixels redistributed is given by
$N_{avggray} = N_{total} / N_{levels}$

+   4. To clip the pixels procedure
if $H(i) > N_{CLIP}$ then
$H_{clip} = N_{CLIP}$
else
if $H(i) + N_{avggray} > N_{CLIP}$ then
$H_{clip} = N_{CLIP}$
else
$H_{clip} = N_{CLIP} + H(i)
end if
end procedure

+   5. Redistribute the remaining pixels until all have been distributed. The step of redistributed pixels is given by $N_{levels} / N_{remain}$
6. Calculate the new gray level assignment of pixels within a submatrix contextual region using interpolation.

where $\omega$ is the number of pixels in patch, $\mu_k$ and $\sigma_k^2$ are the mean and variance of $I$, $\varepsilon$ is the regularization parameter to avoid maximizing the value of $a_k$, and $p$ is the mean of $p$ in window $\omega_k$.
A linear model can be applied to every local window in the whole image. But a pixel is included in every window $\omega_i$ that has this pixel. An easy method is to find the mean of every possible value of pixel of the output image $q_i$ which can be shown as:

```
$q_i = \frac{1}{|omega|} \sum_{k \in \omega} a_k l_i + b_k \quad (12.6)$
```

```
$=\overline{a_i} l_i + \overline{b_i} \quad (12.7)$
```

where $\overline{a_i}$ and $\overline{b_i}$ are the mean in the patch of $a_k$ and $b_k$ respectively.