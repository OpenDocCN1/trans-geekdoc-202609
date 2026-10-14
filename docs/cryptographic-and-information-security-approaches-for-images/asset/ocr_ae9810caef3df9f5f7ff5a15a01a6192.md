lens. The output is again multiplied with another RPM R2, followed by Fourier transformation. The output is a white stationary noise which serves as the ciphertext [1]. The ciphertext can be expressed mathematically as:

$$E(u,v)=\text{IFT}\{\text{FT}\{I(x,y)\exp[i n(x,y)]\}\exp[i b(\alpha,\beta)]\}\tag{5.19}$$

Here, $\exp[i n(x,y)]$ and $\exp[i b(\alpha,\beta)]$ are the RPMs R1 and R2, respectively. The functions $n(x,y)$ and $b(\alpha,\beta)$ are random value distributions lying in the interval $[0,2\pi]$.

DRPE has been a widely studied optical cryptosystem and its many variants have been reported. However, the encryption technique was shown to be vulnerable to the known plaintext attack [19]. In a known plaintext attack, the attacker knows the plaintext and the ciphertext and tries to retrieve the keys. This attack is based on the phase retrieval technique, and is described below:

Taking the Fourier transform of both the sides in Equation 5.19,

$$\psi(\alpha,\beta)=\{FT\{I(x,y)\exp[i n(x,y)]\}\exp[i b(\alpha,\beta)]\}\tag{5.20}$$

Now if the expression $I(x,y)\exp[i n(x,y)]$ is denoted by $G(x,y)$, then Equation 5.20 can be written as:

$$\psi(\alpha,\beta)=FT\{G(x,y)\}\exp[i b(\alpha,\beta)]\tag{5.21}$$

Again, considering $FT\{G(x,y)\}=G(\alpha,\beta)$,

$$\psi(\alpha,\beta)=G(\alpha,\beta)\exp[i b(\alpha,\beta)]\tag{5.22}$$

Taking modulus of both the sides,

$$|\psi(\alpha,\beta)|=|G(\alpha,\beta)|\tag{5.23}$$

Equation 5.23 is the key equation that helps construct known plaintext attacks on the DRPE system. It implies that the Fourier transform of the ciphertext can be used to evaluate the amplitude of the complex quantity in the first Fourier domain of the $4f$-system of the DRPE. This information can help retrieve the RPM R1. If the first Fourier transformation process (shown in the dashed box in Figure 5.5) is considered, then the quantities known to the attacker are the object domain amplitude $I(x,y)$ and the Fourier domain amplitude $|G(\alpha,\beta)|$ $(=|\psi(\alpha,\beta)|)$. This is equivalent to the GSA described in Section 5.2.1. Hence $\exp[i n(x,y)]$ can be evaluated using the GSA in the first Fourier transformation process of the DRPE.