
### 2.5.21.6 Measurement and Continued Fraction Algorithm

After applying the QFT to the output of the modular exponentiation step, we obtain a superposition of states. To extract useful information from this superposition, we need to measure the quantum state, obtaining a classical outcome. The measurement outcome is a specific value, denoted as `y`, which represents the result of the measurement in the Fourier basis. This measurement is a crucial step as it provides us with the information needed to determine the factors of the number `N`.

Next, we employ the continued fraction algorithm to analyze the measurement outcome. The goal is to obtain rational approximations that reveal the period of the measured value and, subsequently, the factors of `N`. The continued fraction algorithm iteratively constructs a sequence of fractions, each representing an approximation of the original measurement outcome `y` divided by the total number of possible outcomes, `M`. The sequence starts with the fraction $\\frac{y}{M}$ \[[28](#ch2.xhtml#ref2_28)\].

### 2.5.21.7 The Example Application

Alice and Bob are good friends who are collaborating to factorize a large number, `N`. Here’s how they work together:

1. Step 1: Preparation
Alice selects the number she wants to factorize, `N`. For this example, let’s assume `N` = 35.

2. Step 2: Quantum Circuit Preparation
Alice and Bob work together to design the quantum circuit required for Shor’s algorithm. They determine the modular exponentiation step, quantum Fourier transform, and measurement operations needed for the chosen value of `N`.

3. Step 3: Modular Exponentiation
Alice instructs Bob to perform the modular exponentiation step. They choose a random base, `a`, that is coprime to `N`. Let’s say they select `a` = 2. Bob implements the modular exponentiation circuit by applying the unitary operator `Uf`, which maps ∣`x`〉 ∣ `y`〉 to ∣`x`〉 ∣ (`a`^(`y`) mod `N`)〉. This involves performing modular multiplications, raising `a` to various powers modulo `N`.

For instance, if Bob measures the auxiliary register and obtains the outcome ∣`y`〉 = 3, he computes (`a`^(`y`) mod `N`) = (2³ mod 35) = 8 mod 35. Bob communicates this result, 8, back to Alice.

4. Step 4: Quantum Fourier Transform
Alice instructs Bob to apply the quantum Fourier transform (QFT) on the input register ∣`x`〉. The QFT transforms the state of the input register from the computational basis to the Fourier basis, allowing for efficient analysis of the periodicity introduced during the modular exponentiation step.

For example, if the measurement outcome after the QFT is ∣`x`〉 = 6, it represents a superposition of possible values, each associated with a different periodicity related to the factors of `N`.

5. Step 5: Measurement and Continued Fraction Algorithm
Alice instructs Bob to measure the output of the QFT. They obtain a measurement outcome, let’s say ∣`x`〉 = 6. Alice and Bob then apply the continued fraction algorithm to approximate the value of `y`/`M`, where `y` represents the measurement outcome and `M` is the total number of possible outcomes.

Using the continued fraction algorithm, they find that the rational approximation for `6`/`M` is 1/6. This approximation reveals the presence of a hidden periodicity in the measurement outcome, which is crucial for determining the factors of `N`.

6. Step 6: Factors Extraction
Alice and Bob work together to extract the factors of `N` using the information obtained from the continued fraction algorithm. In this case, the continued fraction approximation of 1/6 indicates a periodicity that corresponds to the factors 5 and 7. Bob communicates the factors back to Alice, who verifies them. They have successfully factorized the large number `N` = 35 into its prime factors: 5 and 7.

### 2.5.21.8 Summary

Shor’s algorithm is a groundbreaking quantum algorithm that revolutionizes the field of factorization and has far-reaching implications for cryptography and number theory. By leveraging the power of quantum computing, Shor’s algorithm offers an exponential speedup compared to classical algorithms, enabling efficient factorization of large numbers.

Shor’s algorithm has significant implications for cryptography. The security of widely used cryptographic protocols, such as RSA, relies on the difficulty of factorizing large numbers. Shor’s algorithm poses a significant threat to these cryptographic systems, as it can factorize large numbers efficiently. This has led to an increased interest in post-quantum cryptography, which focuses on developing new encryption schemes that are resistant to attacks from quantum computers. Shor’s algorithm has practical applications in other areas such as computational number theory and optimization. It can be used to solve problems that are intrinsically related to factorization, such as finding the period of a periodic function and solving certain types of Diophantine equations. While Shor’s algorithm offers groundbreaking capabilities, it is important to note its limitations. The main limitation is the requirement for a fully functional, error-corrected quantum computer to execute the algorithm efficiently. Building and maintaining such a quantum computer at a large scale is currently a significant technological challenge.

The time complexity of Shor’s algorithm can be expressed as `O((log N)³)`, where `N` is the number to be factorized. This time complexity is significantly better than the best-known classical algorithms, which have exponential time complexity. Shor’s algorithm offers an exponential speedup, enabling the efficient factorization of large numbers that would be infeasible with classical methods. The time complexity mentioned assumes a fully functional, error-corrected quantum computer. However, practical implementations of Shor’s algorithm on currently available quantum hardware face various challenges, including decoherence, noise, and limited qubit resources. As a result, the current implementations of Shor’s algorithm are still limited to relatively small numbers.

## 2.6 Conclusion
