There are various iterative phase retrievals algorithms with different rates of convergence and with different requirement of constraints. In this section, we discuss three major phase retrieval algorithms that have been widely used in optical cryptography.

# 5.2.1 Gerchberg-Saxton Algorithm (GSA)

The Gerchberg-Saxton algorithm (GSA) is the classical method for retrieving the phase when the amplitude information in the object domain f(x, y) and the Fourier domain (i.e., G(u, v)) is given [27]. The algorithm is initiated by assigning a random distribution φ₀(u,v) lying between the interval [−π, π] as the phase distribution in the Fourier domain. The subscript 0 in φ₀(u,v) represents the initial iteration where the iteration number k = 0. The basic steps involved in the kth iteration step of the process can be summarized as:

The random phase φₖ(u,v) is multiplied with the amplitude of the Fourier domain, G(u,v):

Aₖ = G(u,v) × φₖ(u,v)  (5.1)

Aₖ is then inverse Fourier transformed (IFT) to reach the object domain:

Fₖ' = IFT(Aₖ)  (5.2)

Substitute the amplitude of Fₖ' with the known amplitude of the object domain i.e. f(x, y). This gives the updated value of the object domain function.

Fₖ = f(x, y) × phase(Fₖ')  (5.3)

Fₖ is Fourier transformed (FT) and the phase of this Fourier transformed quantity is used to update φₖ(u,v) to get φₖ₊₁(u,v). This in turn is multiplied by the Fourier domain amplitude to get Aₖ₊₁:

Aₖ' = FT{Fₖ}  (5.4)

φₖ₊₁ = phase{Aₖ'}  (5.5)

Aₖ₊₁ = G(u,v) × φₖ₊₁(u,v)  (5.6)

The algorithm then proceeds with the above steps forming an iterative loop. The iterations continue till the error between the approximated Fourier amplitude of Aₖ'