![](bbox=[0.22, 0.13, 0.78, 0.38])

Figure 16.13 Inverse transform.

Scaling coefficients are:

$$\alpha(k)=\begin{cases}\sqrt{\frac{1}{N}} & \text{if } k=0\\\sqrt{\frac{2}{N}} & \text{if } k\neq 0\end{cases}$$ $$\alpha(l)=\begin{cases}\sqrt{\frac{1}{N}} & \text{if } l=0\\\sqrt{\frac{2}{N}} & \text{if } l\neq 0\end{cases}$$ (4.7)

Here $f(m,n)$ is the input image with mXn size.

# 16.4.1.2 Example Model Work Flow

The proposed idea of the author is to divide the work into two sessions: first session deals with multiple image fusion and final session deals with watermarking of fused images and other patient records (like photo, OP information, ECG reports etc.) into single image. The author tries to explore the new way of combining multiple techniques, which could be useful and extendable for effective image processing. The following session explains the fusion and watermarking process respectively in Figures 16.14 through 16.16.