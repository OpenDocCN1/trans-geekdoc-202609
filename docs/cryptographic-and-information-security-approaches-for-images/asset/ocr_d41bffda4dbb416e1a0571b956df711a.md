# Step 3: Generate the sparse measurements of the image by multiplying sparse coefficients with measurement matrix A.

$$E f_{M\times N}=A_{M\times N}\times x_{N\times N}\tag{8.2}$$

where $E f$ is the compressed and encrypted image in terms of sparse measurements and $A$ is the measurement matrix.

In a CS decryption process, the decryption of an image is taking place from its sparse measurement. The decryption process can be performed using CS recovery algorithms and a measurement matrix. These recovery algorithms are based on linear algebra properties and optimization techniques. There are various types of CS recovery algorithms: L norm minimization and greedy based approach [4–8].

Let $E f$ be the encrypted image after CS encryption, then the decryption of image $D f$ can be performed using CS recovery algorithm. The sparse coefficients of the image are in transform domain $\Psi$, the image is decrypted by solving below minimization problem.

$$\min\|f\|_1\ ,\ E f = A x\tag{8.3}$$

The necessary condition for an image decryption using sparse measurements is that it must satisfy restricted isometric property (RIP). The measurement matrix $A$ of size $M\times N$ obeys the RIP of order $K$ ($K<m$) if measurement matrix $A$ approximately preserves the squared magnitude of any $K$ sparse encrypted image $E f$ using Equation 8.4.

$\forall y$ for which

$\|y\|_0 \le k,$

$(1-\delta_K)\|E f\|^2 \le \|A E f\|^2 \le (1+\delta_K)\|E f\|^2$

$0 < \delta_k < 1$\tag{8.4}

The measurement matrix and transform basis matrices are used as secret keys in the CS based encryption process. The chosen criteria of these two matrices depend on various parameters. The measurement matrix must be random, symmetric in nature and easy to generate. The Gaussian distribution shown in Figure 8.4 satisfies all these properties. For transform basis matrix; it must be sparse, real and symmetric. The DFT, DCT, and DWT have sparse property. Therefore, these three transforms are mainly used in CS based encryption process.