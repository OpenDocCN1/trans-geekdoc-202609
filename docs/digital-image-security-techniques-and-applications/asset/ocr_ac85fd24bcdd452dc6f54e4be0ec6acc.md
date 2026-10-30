# 3.6.5.2 Methodology

The process for generating codes using multivariate cryptography requires the use of mathematical polynomials over finite fields. These polynomials are then used to create an extremely complex code, which can only be decrypted when the correct combination of variables is provided. This makes it highly resistant to brute force attacks since even if hackers have access to the underlying equations, they would still need to correctly guess the right combinations to decrypt any encrypted data. In a sense, multivariate cryptography is also a kind of public key cryptography [50].

Systems of nonlinear polynomial equations in multiple variables, often quadratic equations over a finite field F = Fq with q elements, are the fundamental building blocks of multivariate cryptography. Refer to Eq. 3.12.

p^{(1)}(x_1,...,x_n)=\sum_{i=1}^{n}\sum_{j=1}^{m}p_{ij}^{(1)}\cdot x_i x_j + \sum_{i=1}^{n}p_i^{(1)}\cdot x_i + p_0^{(1)},

p^{(2)}(x_1,...,x_n)=\sum_{i=1}^{n}\sum_{j=1}^{n}p_{ij}^{(2)}\cdot x_i x_j + \sum_{i=1}^{n}p_i^{(2)}\cdot x_i + p_0^{(2)}

\vdots

p^{(n)}(x_1,...,x_n)=\sum_{i=1}^{n}\sum_{j=1}^{n}p_{ij}^{(n)}\cdot x_i x_j + \sum_{i=1}^{n}p_i^{(n)}\cdot x_i + p_0^{(n)}

(3.12)

The security of the multivariate cryptographic system lies in the difficulty of the following problem:

**Problem:** Given $p^{(1)}, p^{(2)}, ..., p^{(n)}$ as in Eq. 3.12 in the variable $x = (x_1, x_2, ..., x_n)$, find $x$ such that $p^{(1)} = 0, p^{(2)} = 0, ..., p^{(n)} = 0$ [50].

To further enhance security measures, multivariate cryptography also utilizes elements from chaos theory and random number generation techniques. By introducing randomness into the equation through these methods, hackers cannot predict what combination will yield a successful result even if they possess knowledge about the underlying mathematics behind it. This ensures that any attempt at breaking into multivariately encrypted data will prove futile in most cases due to the sheer complexity involved in guessing all possible combinations correctly before successfully unlocking any encrypted data files.

Due to its many advantages over traditional forms of encryption, multivariate cryptography has been adopted for use in many different industries ranging from banking and finance to telecommunications and government applications where heightened security measures are required. It is also increasingly being incorporated into everyday applications such as online