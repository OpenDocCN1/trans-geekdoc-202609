
The `SK` criteria for closeness in approximation are inversely related to an increase in the length of the approximating string of operators. The group commutator \[U, V\][*G*]\=UVU\*V\* is employed in the proof of `SK`. It is used in determining how close unitary operators are to the identity operator, `I`. The group commutator is related to the usual Lie bracket for `U`, `V` in `SU(2, C)`, as follows: \[U, V\]=0, then \[U, V\][*G*]\=I. This is true because \[U,V\]=0, which means that `UV=VU`; then in the group commutator, \[U, V\][*G*]\=UVU\*V\*, replacing `UV` by `VU` gives \[U, V\][*G*]\=VUU\*V\*, which is the identity.

Consequently, the group commutator is close to the identity when and only when the two operators commute. Repeated application of this commutator relationship enables ![ent](`Images/epsi_1013.png`)net approximations to be made to the identity element. Lastly by translation, the approximation can be seen to hold for any unitary operator in `SU(2, C)`. Most proofs of the `SK` theorem employ the shrinking lemma specifying better approximations of the identity using larger length strings. Smaller and smaller ![ent](`Images/epsi_1013.png`)net approximations are made to neighborhoods of the identity. The final step in the proof is using the bi-invariance of distance to translate the ![ent](`Images/epsi_1013.png`)nets to approximate other elements in `SU(2, C)`. In-depth details are provided in [Zarapico (2018](#Ch016_291-305_B9780443136979000060.xhtml#bib7)). For `S` in a `UQGS` with algebraic entries and ![ent](`Images/epsi_1013.png`) > 0, `n` can be chosen where `n=0(log^(*c*) (1/![ent](`Images/epsi_1013.png`)))`, with `c=1` ([Holevo, 2003](#Ch016_291-305_B9780443136979000060.xhtml#bib10); [Bourgian and Gamburd, 2001](#Ch016_291-305_B9780443136979000060.xhtml#bib1)).

## 16.9 Quantum Fourier transform and phase estimation

The quantum Fourier transform (`QFT`), denoted by `F`, sends vectors in a complex Hilbert space `C^(*N*)` back into `C^(*N*)`, where usually `N` is the positive integer `2^(*n*)`. Specifically, for ${|{x > = \\sum\_{j = 0}^{N - 1}x\_{j}}|}j >$![Equation](`Images/F000060si84.png`), the `QFT`, $F\\left( {|{x >}} \\right) = \\sum\_{j = 0}^{N - 1}y\_{j}{|j} >$![Equation](`Images/F000060si85.png`), where $y\_{j} = 1/N^{1/2}\\sum\_{k = 0}^{N - 1}{x\_{k}\\left( w\_{N} \\right)^{km}}$![Equation](`Images/F000060si86.png`), for m=0, 1, 2, …, N−1. Also, *w*[*N*] = *e*^((2*i**π*)/*N*)![Equation](`Images/F000060si87.png`). The inverse `QFT` is similarly defined. It too sends vectors in the complex Hilbert space *C*^(*N*)![Equation](`Images/F000060si88.png`) back into *C*^(*N*)![Equation](`Images/F000060si89.png`). In this case, $x\_{j} = 1/N^{1/2}\\sum\_{k = 0}^{N - 1}{y\_{k}\\left( w\_{N} \\right)^{- km}}$![Equation](`Images/F000060si90.png`), for m=0, 1, 2, …, N−1. The `QFT` as well as its inverse can be implemented as a unitary matrix, *U*[*N*]![Equation](`Images/F000060si91.png`) operating on quantum state vectors.

### Example 16.15

In the Hilbert space `C²`, the `QFT`, `F=H`, the Hadamard transform. This follows since *w*[*N*] = *e*^((2*i**π*)/*N*) = *w*[2] = *e*^((2*i**π*)/2) =  − 1![Equation](`Images/F000060si92.png`). Therefore, ${|{x > =}}\\sum\_{j = 0}^{1}x\_{j}{|j} > ,F\\left( {|{x >}} \\right) = \\sum\_{j = 0}^{1}{y\_{j}{|j}} >$![Equation](`Images/F000060si93.png`), where $y\_{j} = 1/2^{1/2}\\sum\_{k = 0}^{1}{x\_{k}\\left( w\_{2} \\right)^{km}}$![Equation](`Images/F000060si94.png`), for m=0, 1. *F*(|*x*\>) = 1/2^(1/2)\[*x*[0](*w*[2])⁰+*x*[1](*w*[2])⁰\]|0 >  + 1/2^(1/2)\[*x*[0](*w*[2])⁰+*x*[1](*w*[2])¹\]|1 >  = 1/2^(1/2)\[*x*[0]+*x*[1]\]|0 >  + 1/2^(1/2)\[*x*[0]−*x*[1]\]|1>![Equation](`Images/F000060si95.png`). So it follows that `F` (|x>)=`H` (x[0] x[1])′.#

### Example 16.16

In `C⁴`, let ${|{x > =}}\\sum\_{j = 0}^{N - 1}{x\_{j}{|j}} >$![Equation](`Images/F000060si96.png`) = 1/3(|0>+2*i*|2>−2|3>) = 1/3(|00>+2*i*|10>−2|11>)![Equation](`Images/F000060si97.png`). Notice that the norm‖|x>‖=1. The objective is to find the `QFT`, `F` (|x>). This will be computed using the unitary matrix *U*[4]![Equation](`Images/F000060si98.png`). Provided below is 2*U*[4]![Equation](`Images/F000060si99.png`), followed by the vector, 3|x> represented as a four-by-one column vector in *C*⁴![Equation](`Images/F000060si100.png`),

$\\begin{matrix} {|1} & 1 & 1 & {1|} \\\\ {|1} & i & {- 1} & {{- i}|} \\\\ {|1} & {- 1} & 1 & {{- 1}|} \\\\ {|1} & {- i} & {- 1} & {i|} \\\\ \\end{matrix}\\quad\\quad\\begin{matrix} {|1|} \\\\ {|0|} \\\\ {|{2i}|} \\\\ {{|{- 2}|}.} \\\\ \\end{matrix}$

![Equation](`Images/F000060si101.png`)

Multiplying out the four-by-four matrix 2*U*[4]![Equation](`Images/F000060si102.png`), time the four-by-one vector, 3|x>, in *C*⁴![Equation](`Images/F000060si103.png`), gives `F` (|x>)=1/6 (−1+2i 1 3+2i 1–4i)′. Note that the norm of `F` (|x>)=1. This had to be the case since a unitary mapping is always an isometry; thus it preserves the length of vectors.#

A quantum circuit to perform the `QFT` involves inputting each qubit and then using first a Hadamard matrix followed by a sequence of several controlled rotation matrices of the form:

$\\begin{matrix} {|1} & {0|} \\\\ {|0} & {e^{{2i\\pi}/{{(2^{k})}x\_{j}}}|} \\\\ \\end{matrix}$

![Equation](`Images/F000060si104.png`)

This is employed for each input qubit.

## 16.10 Uniform superposition and amplitude amplification

In quantum algorithms, an important application of the Hadamard gate is to utilize it on almost every input. Usually, the inputs are `n` in number and are all|0> qubits. In this case, the operation is called the diffusion operation. Say that a Hadamard operator is applied to every input in parallel, it is symbolized as $H^{@n}\\left( {|{0 >^{@n}}} \\right) = 1/2^{n/2}\\sum\_{x = 0}^{N - 1}{{|x} >}$![Equation](`Images/F000060si105.png`), where *N* = 2^(*n*)![Equation](`Images/F000060si106.png`), and the tensor product is symbolized by @. So the probability associated with any vector|x> within the uniform superposition is 1/2^(*n*)![Equation](`Images/F000060si107.png`). Since all amplitudes are the same, the average height of any|x> is also 1/2^(*n*)![Equation](`Images/F000060si108.png`).

### Example 16.17

Consider the two input system, $H^{@2}\\left( {|{0 >^{@2}}} \\right) = 1/2\\sum\_{x = 0}^{3}{{|x} >}$![Equation](`Images/F000060si109.png`). Mathematically, this follows because *H*|0 >  = 1/2^(1/2)(|0>+|1>) = | + >![Equation](`Images/F000060si110.png`), and since there are two Hadamard gates in parallel, the computation is *H*^(@2)(|0>^(@2))![Equation](`Images/F000060si111.png`). So forming the tensor product of |+> with itself, that is, gives |+> @|+>=1/2 \[|0 0>+|0 1>+|1 0>+|1 1>\]. Interpreting each ket,|x> in binary, provides the same result, namely $1/2\\sum\_{x = 0}^{3}{{|x} >}$![Equation](`Images/F000060si112.png`). A simple calculation shows that these vectors within the uniform superposition are each of unit length and mutually orthogonal to each other. The last property is best seen using the representation in *C*⁴![Equation](`Images/F000060si113.png`). In this case, each of these kets is represented by a four-by-one vector. Each vector contains all zero-valued tuples except for a single one in different locations.#
