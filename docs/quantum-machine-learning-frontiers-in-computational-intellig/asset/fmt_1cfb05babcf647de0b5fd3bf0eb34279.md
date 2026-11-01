
The objective function `f(x)` as well as the inequality and the equality constraints are often nonlinear, non-convex, non-differentiable, multimodal and of high dimension. Thus, optimization techniques, which are efficient by being deterministic, like gradient based methods and exhaustive search, are often rendered ineffective for solving such ill-defined problems [[57](#bodymatter-003.xhtml#b_9783110670707-003_ref_057)]. Calculus based methods typically perform local optimization by using search space domain information like local gradient [[58](#bodymatter-003.xhtml#b_9783110670707-003_ref_058)]. Enumerative Strategies suffer from the curse of dimensionality i.e. the runtime complexity increases exponential with the dimension of the problem [[59](#bodymatter-003.xhtml#b_9783110670707-003_ref_059)].

It has been shown in [Section 3.4](#bodymatter-003.xhtml#b_9783110670707-003_s_003_s_004) that Quantum global optimization algorithms can be used for solving finite search domain problems. The search domain of any real variables problem is infinite. In order to overcome this limitation of quantum algorithms, the real variables search space in [[60](#bodymatter-003.xhtml#b_9783110670707-003_ref_060)] has been discretized. That is a variable is represented by a finite number of qubits, which determines the resolution and the level of discretization. For example, the decision variables, `x[i]`, in continuous domain are bounded by `x[il]` and `x[iu]`. The search space for variable `x[i]` can be discretized by taking `n[i]` qubits, so that there will be `2^(n[i])` distinct values of `x[i]` which can be selected between the range of `[x[il], x[iu]]`. The maximum discretization error, `Δe[i]`, is as follows:
```
(3.14)*Δ**e*[*i*] = (*x*[*i**u*]−*x*[*i**l*])/2^((*n**i* + 1))
```
This discretization error is present even in computation performed with classical digital computers. The total number of qubits, `nq`, required to map the discretized solution space is as follows:
```
(3.15)*n**q* = ∑[*i*]*n*[*i*]
```
The larger the number of qubits more is the accuracy, however, it also increases the running time of the quantum algorithm. Therefore, there is a trade-off involved between accuracy and computation time. An output or auxiliary qubit is also required which evolves according to the result of the computation of the objective function implemented by a reversible circuit [[52](#bodymatter-003.xhtml#b_9783110670707-003_ref_052)].

## 3.6 AQC based quantum search

Adiabatic Quantum Computation is analog analogue of discrete gate-based quantum computing, which is a generic framework that depends on Hamiltonian and Adiabatic theorem [[31](#bodymatter-003.xhtml#b_9783110670707-003_ref_031)]. A Problem Hamiltonian (`H[fin]`) is designed for the problem being solved such that it is a time independent Hamiltonian, and the ground state of `H[fin]`, `|ψ[fin]⟩`, represents a solution of the problem. The quantum system is evolved by a time dependent Hamiltonian, `H(t)`. `H(0)` corresponds to a time independent Hamiltonian known as initial Hamiltonian (`H[ini]`), whose ground state is easy to construct. Hamiltonian `H(t)` is time-varying and governs the evolution of the system and it varies according to the bounds given by adiabatic theorem, from `H[ini]` to `H[fin]`, so that the quantum system stays near the ground state of the instantaneous Hamiltonian `H(t)` till it reaches `H[fin]`. Thus, Adiabatic Quantum Algorithm has following main steps:
1. Determine the number of qubits, `nq`, required to represent the problem in the quantum system.
2. Find an easily constructible initial ground state and construct its corresponding `H[ini]`.
3. Design the `H[fin]` according to the problem being solved.
4. Construct the time dependent Hamiltonian `H(t)`, which will govern the evolution of the system for time `T`:
```
*H*(*t*) = *H*[*i**n**i*] \* (1−*t*/*T*) + *H*[*f**i**n*] \* (*t*/*T*)
```
or,
```
(3.16)*Ĥ*(*s*) = *H*[*i**n**i*] \* (1−*s*) + *H*[*f**i**n*] \* (*s*)
```
where `s = t/T` and `s(0) = 0` and `s(T) = 1`.
5. Estimate total evolution time `T`.
6. Evolve the Quantum System according to Schrodinger’s Equation for time `T`:
```
(3.17)$i\\hslash\\frac{d|\\psi\\left( t \\right)\\rangle}{dt} = H\\left( t \\right)|\\psi\\left( t \\right)\\rangle$
```
where `ħ = 1`.
7. Perform Measurement on the Quantum system after time `T` to obtain the solution of the problem.

Search for a marked element in an unstructured database with `N[e]` elements was also attempted by Farhi et al. in [[31](#bodymatter-003.xhtml#b_9783110670707-003_ref_031)] by using global version of the Adiabatic Theorem for their quantum algorithm. This resulted in a running time of the order of `N` i.e. `O(N)`, which was no better than a classical algorithm. Roland and Cerf improved the performance of Adiabatic Quantum Algorithm for this problem by using local adiabatic evolution approach [[32](#bodymatter-003.xhtml#b_9783110670707-003_ref_032)]. Thus, Adiabatic version of Grover’s search also has the same complexity as that of Circuit model. This chapter employs local version of Adiabatic evolution proposed by Roland and Cerf in [[32](#bodymatter-003.xhtml#b_9783110670707-003_ref_032)] for Grover’s Search to design a quantum algorithm for solving optimization problems in continuous domain.

The algorithm starts with initial state as `|φ[0]⟩`, which is in equal superposition of all the basis states, `N[e]` (`j` represents index of elements in unsorted database):
```
(3.18)$\\left| \\phi\_{0} \\right.\\rangle = \\frac{1}{{\\sqrt{N}}\_{e}}\\sum\\limits\_{j = 0}^{Ne - 1}|j\\rangle$
```
The beginning Hamiltonian, `H[ini]`, of the system is chosen as:
```
(3.19)*H*[*i**n**i*] = *I*− |*ϕ*[0]⟩⟨*ϕ*[0]|
```
where `I` is the Identity matrix and `|φ[0]⟩` is its ground state with zero energy. Therefore, the `H[ini]`, for quantum search algorithm is independent of the problem. Let us assume that there exist a problem Hamiltonian `H[fin]`, which can be represented as follows:
```
(3.20)$H\_{fin} = I - \\sum\\limits\_{M \\in m\_{e}}\\left| {\\phi\_{M}\\rangle\\langle\\phi\_{M}} \\right|,$
```
where `m[e]` is the ensemble of solutions and `|φ[M]⟩` represents the ground state, and is a solution. `H[fin]` can be applied without explicitly knowing `|φ[M]⟩`, by using an oracle to tell whether the solution has been found or not. It is implemented as follows:
```
(3.21)*H*[*f**i**n*]|*ϕ*[*i*]⟩ = *f**p**b*(*ϕ*[*i*])|*ϕ*[*i*]⟩
```
where function `fpb(φ[i])` has been implemented as follows:
```
*I**f*(|*ϕ*[*i*]⟩ ∈ {|*ϕ*[*M*]⟩}) *f**p**b*(*ϕ*[*i*]) = 0
else
*f**p**b*(*ϕ*[*i*]) = 1
```
That is, if `|φ[i]⟩` is the marked state, then `fpb(φ[i])` is equal to zero, corresponding to the ground state, i.e. lowest energy and if `|φ[i]⟩` is not the marked state, then `fpb(φ[i])` is equal to one, i.e. having higher energy level than the ground state. The `fpb(φ[i])` can be reversibly implemented by using the same technique as described for oracles in [Section 3.3.1](#bodymatter-003.xhtml#b_9783110670707-003_s_003_s_003_s_001).

The time dependent Hamiltonian that evolves the system under initial Hamiltonian to final Hamiltonian is as follows:
```
(3.22)*H*(*t*) = (1 − *s*(*t*)) *H*[*i**n**i*] + *s*(*t*)*H*[*f**i**n*]
```
where `s(t)` is a continuous function with `s(0) = 0` and `s(T) = 1`. Let eigenstates of `H(t)` be `|ψ[k](t)⟩` such that:
```
(3.23)$\\begin{matrix} & {{fpb}\\left( q \\right){= 0;}} \\\\ & {{fpb}\\left( q \\right){= 1;}} \\\\ \\end{matrix}$
```
where `E[k](t)` are the corresponding eigenvalues and `k` labels the eigenstates (`k = 0` indicates the ground state).

The gap between the lowest two eigenvalues, `E[0]` and `E[1]`, is described by the following equation [[32](#bodymatter-003.xhtml#b_9783110670707-003_ref_032)]:
```
(3.24)$g\\left( s \\right) = \\sqrt{1 - 4\\left( {1 - \\frac{m\_{e}}{N\_{e}}} \\right)s\\left( t \\right)\\left( {1 - s\\left( t \\right)} \\right)}$ $g\_{min} = \\ \\sqrt{}\\left( {m\_{e}/N\_{e}} \\right){\\, and\\, occurs\\ at\\, s = 1/2}.$
```
