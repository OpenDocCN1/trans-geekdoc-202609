
![](img/f4c3bcc9f5332d57a8ec85a75075f8da_155_0.png)

Figure 5.4 Flowchart showing the steps of MGSA to evaluate phase only mask of a given image.

In wavelength multiplexing. The phases are then summed and normalized to obtain a single phase only function, which is given by:

ψ_T = arg { [∑_{n=1}^N exp[i ψ_{λ_n}]] / [∑_{n=1}^N exp[i ψ_{λ_n}]] } (5.18)

ψ_T serves as the multiplexed ciphertext for N images. For retrieving a particular image, ψ_T is inverse Fresnel transformed using the corresponding wavelength value. Different artifacts can be applied to remove the cross talks in this multiplexing scheme [36].

## 5.4 Cryptanalysis

As majority of optical cryptosystems are constructed using optical transforms, phase retrieval becomes relevant in these cases to formulate attack algorithms. This section studies such iterative phase retrieval attack algorithms.

### 5.4.1 Cryptanalysis in DRPE

DRPE was one of the first proposed optical encryption schemes. As mentioned earlier, it consists of a typical 4f optical set-up where the input image I(x, y) is multiplied with an RPM R1 and subjected to Fourier transformation using a converging lens. The output is again multiplied with another RPM R2, followed by Fourier transformation. The output is a white stationary noise which serves as the ciphertext [1]. The ciphertext can be expressed mathematically as:

$$E(u,v)=\text{IFT}\{\text{FT}\{I(x,y)\exp[i η(x,y)]\}\exp[i b(\alpha,\beta)]\}\tag{5.19}$$

Here, $\exp[i η(x,y)]$ and $\exp[i b(\alpha,\beta)]$ are the RPMs R1 and R2, respectively. The functions $η(x,y)$ and $b(\alpha,\beta)$ are random value distributions lying in the interval $[0,2\pi]$.

DRPE has been a widely studied optical cryptosystem and its many variants have been reported. However, the encryption technique was shown to be vulnerable to the known plaintext attack [19]. In a known plaintext attack, the attacker knows the plaintext and the ciphertext and tries to retrieve the keys. This attack is based on the phase retrieval technique, and is described below:

Taking the Fourier transform of both the sides in Equation 5.19,

$$\psi(\alpha,\beta)=\{FT\{I(x,y)\exp[i η(x,y)]\}\exp[i b(\alpha,\beta)]\}\tag{5.20}$$

Now if the expression $I(x,y)\exp[i η(x,y)]$ is denoted by $G(x,y)$, then Equation 5.20 can be written as:

$$\psi(\alpha,\beta)=FT\{G(x,y)\}\exp[i b(\alpha,\beta)]\tag{5.21}$$

Again, considering $FT\{G(x,y)\}=G(\alpha,\beta)$,

$$\psi(\alpha,\beta)=G(\alpha,\beta)\exp[i b(\alpha,\beta)]\tag{5.22}$$

Taking modulus of both the sides,

$$|\psi(\alpha,\beta)|=|G(\alpha,\beta)|\tag{5.23}$$

Equation 5.23 is the key equation that helps construct known plaintext attacks on the DRPE system. It implies that the Fourier transform of the ciphertext can be used to evaluate the amplitude of the complex quantity in the first Fourier domain of the $4f$-system of the DRPE. This information can help retrieve the RPM R1. If the first Fourier transformation process (shown in the dashed box in Figure 5.5) is considered, then the quantities known to the attacker are the object domain amplitude $I(x,y)$ and the Fourier domain amplitude $|G(\alpha,\beta)|$ $(=|\psi(\alpha,\beta)|)$. This is equivalent to the GSA described in Section 5.2.1. Hence $\exp[i η(x,y)]$ can be evaluated using the GSA in the first Fourier transformation process of the DRPE.

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_157_0.png)

Figure 5.5 Block diagram showing the DRPE. The Fourier transformation in the dashed box is used to implement the GSA to evaluate the phase exp[iη(x,y)].

Once exp[iη(x,y)] is known, the conjugate of the other key, RPM R2 can also be evaluated by simple mathematical relation following from Equations 5.19 and 5.20. This conjugate is denoted by R2' and is given by:

$R2' = \exp[-i b(\alpha,\beta)] = \frac{\text{FT}\{I(x,y)R1\}}{\psi(\alpha,\beta)} \quad (5.24)$

Numerical simulations of the known plaintext attack on DRPE have been shown in Figure 5.6. The simulation platform is MATLAB® (R2015). Initially, two images, shown in Figure 5.6a and b, have been encrypted with the DRPE technique such that the two RPMs used in the process are same for both the cases. Figure 5.6c and d show the corresponding encrypted images. The keys are retrieved using the known plaintext attack on the encrypted image of Figure 5.6a. The retrieved keys are then used to decrypt the image in Figure 5.6b. It can be seen in Figure 5.6e that the retrieved keys can well decrypt the image in Figure 5.6b.

### 5.4.2 Cryptanalysis in the Asymmetric Cryptosystem

As the DRPE system was shown to be vulnerable to the chosen ciphertext and the known plaintext attacks owing to the linearity of the system. The linearity in the DRPE system arises because the encryption keys and the decryption keys are similar. To remove this linearity the phase truncation Fourier transform (PTFT) based cryptosystems were introduced which fall in the category asymmetric cryptosystems [38]. In these schemes, the encryption keys differ from the decryption keys. This section highlights the phase retrieval based attack systems, namely the specific attacks that are applicable to the PTFT based systems.

In the PTFT-based encryption, the input image I(x, y) is multiplied by an RPM (first encryption key) and subjected to the Fourier transform. The phase of the output is saved as the first private key, while the amplitude is again multiplied by another RPM (second encryption key), and is again Fourier transformed. The amplitude of the output serves as the ciphertext while the phase is reserved as the second private key. Mathematically, the entire encryption process can be summarized as:

$E(u,v) = \text{PT}\{\text{IFT}[\{\text{PT}[\text{FT}\{I(x,y) \times K_1(x,y)\}]\} \times K_2(m,n)]\} \quad (5.25)$

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_158_0.png)

(a)

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_158_1.png)

(b)

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_158_2.png)

(c)

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_158_3.png)

(d)

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_158_4.png)

(e)

Figure 5.6 Simulation results for the known plaintext attack on the DRPE (a) first input image, (b) second input image, (c, d) ciphertexts corresponding to the first and second images respectively, using same RPMs, and (e) image retrieved after applying the keys obtained from known plaintext attack on the first encrypted image.

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_159_0.png)

Figure 5.7 Schematic showing the encryption stages in PTFT-based cryptosystem.

Here, PT refers to phase truncation operation. Figure 5.7 shows the encryption schematic for PTFT-based cryptosystem.

Phase retrieval algorithms with different constraints have been used to formulate the specific attacks on these asymmetric cryptosystems [22–24]. In the specific attack, the attacker has the knowledge of one or more encryption keys, the ciphertext and the encryption principle. Knowing these quantities, the attack aims to retrieve the plaintext. As an example, one of the attack methods is discussed here [23].

Step 1: Initially, a random amplitude guess for the plaintext is initiated and is denoted by I_k (for the first guess k = 0). This amplitude guess is multiplied with the first key K1 and then Fourier transformed. The amplitude and the phase parts are separated as follows:

G_k(m,n) = PT{FT[I_k(x,y) × K1(x,y)]} (5.26)

P_k(m,n) = PR{FT[I_k(x,y) × K1(x,y)]} (5.27)

Here PR refers to phase reserve operation.

Step 2: The function G_k(m,n) is multiplied by the second key K2 and then inverse Fourier transformed. The amplitude and the phase of the output are given by:

C_k(u,v) = PT{IFT[G_k(m,n) × K2(m,n)]} (5.28)

B_k(u,v) = PR{IFT[G_k(m,n) × K2(m,n)]} (5.29)

Step 3: The amplitude of the output is updated with the ciphertext, while the phase is retained. The updated function is Fourier transformed followed by phase truncation.

G_k'(m,n) = PT{FT[E(u,v) × B_k(u,v)]} (5.30)
