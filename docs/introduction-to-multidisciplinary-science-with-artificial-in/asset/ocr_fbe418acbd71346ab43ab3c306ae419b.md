In quantum mechanics, for every observable M there exists a corresponding her-mitian operator. Knowledge of the physical state a implies a knowledge of the expectation value of every observable, according to the rule

< M > = < a | M | a > ,

< M > is the average or expected value of an observable for a system in state |a>. Although the result of a single measurement is probabilistic, we are usually interested in the average outcome, which gives us more information about the system and the observable.

Remember that the value of the measurement of an observable (e.g., matrices in (4.68)) is one of the observable eigenvalues. The probability of obtaining a particular eigenvalue is given by the modulus square of the inner product of the state vector of the system with the corresponding eigenvector. The state of the system immediately after the measurement is the normalized projection of the state prior to the measurement onto the eigenvector subspace. If B is an observable with eigenvalues λ_k^{(b)} and eigenvectors |b_k> [i.e., B |b_k> = λ_k^{(b)} ], given a system in the state |ψ>, the probability of obtaining λ_k^{(a)} as the outcome of the measurement of B is

p(b_k) = |<b_k|ψ>|^2 = <ψ|P_k|ψ> , (4.72)

where P_k = |b_k><b_k|.

So, in quantum mechanics, we mostly deal with vectors and linear operators on vectors. The vectors are represented by bras and kets. Hence the attraction of vectors in mathematical descriptions of quantum mechanics, which are probably the most convenient and efficient notations for vectors and operators on vectors. So, in contrast to the classical obscure view, at least from a mathematical point of view, quantum mechanism is not so obscure. It essentially uses a linear complex-valued vector space with scalar products, which is by definition a complex Hilbert space and encompasses linear transformations through matrices acting on vectors. Note that we use complex numbers in quantum mechanics to effectively deal with time and reversibility, especially the evolution of states with time.

In quantum mechanics pure states are unit vectors in a Hilbert space—that is, each direction corresponds to a single unique physical state. For example, after a spin measurement along the z-direction we know with certainty the state of the spin of the system along this direction. Such states are referred to as pure states.

# **Example: qubit system.**

Consider two vectors |u> = [1, 0]^T and |d> = [0, 1]^T representing the quantum bit, also known as the qubit. Vector |u> can be interpreted as a spin of electron pointing up and vector |d> as a spin of an electron pointing down. We can define an electron state as |a> = a_u |u> + a_d |d>, where <u|a>^2 = a_u a_u^* is the probability of finding the electron pointing up and <d|a>^2 = a_d a_d^* is the probability of finding the electron pointing down. Because the sum of probability must be 1, we have the following condition <a|a> = a_u a_u^* + a_d a_d^* = 1. We can verify that <u|a> = <d|u> = 1 and <u|d> = <d|u> = 0. So vectors u and d are orthogonal, as one may have expected. Notice that a_u = a_d = 1/√2 is a valid choice—the electron points horizontally in this case—but a_u = a_d = 1 is not because the sum of probabilities