
Four more functions besides the `bosonic` and `fermion` exist in the three-state quantum particle environment. These have mixed symmetry; first, two particles can be symmetrized, and then two particles can be antisymmetrized. These particles are known as quark-flavor eigenstates. The `Y` description for the four quark states always has a top bar of two cells and a bottom bar of a single cell. In terms of the quark flavor, the generation of wave functions for baryons can be illustrated, leading to a 27-dimensional representation of `SU(3)`. Here, the `Clebsch-Gordon` series could be found consisting of the `SU(3)` irreducible representations. They can be described in terms of `Y` and `Weyl` diagrams and occur in angular momentum coupling ([Messiah, 1981](#Ch015_271-288_B9780443136979000291.xhtml#bib7)).

## 15.8 Bogoliubov transform

The `Bogoliubov` transform is an isomorphism for the `CCR` or the `CAR`. Specifically, the transforms provide conditions for which the creations and annihilation operations can be transformed into a new set of equivalence operations. Let the original creation and annihilation operations be `f^†` and `f`, respectively. The new operations are `a^†` and `a`. The `Bogoliubov` transform `T` is such that `(a^† a)′`=`T` `(f^† f)′`, where `T` is such that for `A`=

```
\\begin{matrix} {|0} & {1|} \\\\ {|1} & {0|} \\\\ \\end{matrix}
```

![Equation](Images/F000291si91.png)

`TAT′` = `A`.

![Equation](Images/F000291si92.png)

### Example 15.14

Let `T` be given below along with `T`, `T A`, as well as `T′`, in the following order:

```
\\begin{array}{llllll} {|i} & {0|} & {|0} & {i|} & {|i} & {0|} \\\\ {|0} & {{- i}|} & {|{- i}} & {0|} & {|0} & {{- i}|} \\\\ \\end{array}
```

![Equation](Images/F000291si93.png)

The product `T A T′`=`A`. As a consequence, in this case the new creation and annihilation operations are given from the original ones by `a^†`=i `f^†`, `a`=`−i` `f`.

## 15.9 Parafermionic and parabosonic spaces

These spaces are built on the premise that irreducible representations of the permutation group govern the transformation of wave functions. In particular, particle states transform under generalized symmetry. The states exist in between bosonic and fermionic states. Precise representations are given using Young diagrams. Quons are a theoretical particle believed to exhibit symmetries as well as antisymmetries. An algebra for working with quons involves operators from the bosonic as well as the fermionic Fock spaces. Specifically, the operator is a convex combination of the Lie bracket and the Poisson bracket. Indeed, for `r` in the interval \[−1, 1\], the operator involves both the annihilation `a` and creation operation `a^†` and is `(1+r)/2 [am, an^†]+(1−r)/2 {am, an^†}=dmn`, where `dmn`=0, unless `m=n`; then it equals one. The vacuum state is defined as in Fock space and `am|0>`=0 as before. For `r`=1, the bosonic Fock space is described in the aforementioned formula. Similarly for `r`=−1, the fermionic Fock space operations are applicable. Irreducible representations of the symmetric group are weighted in describing the states for quons.

## 15.10 Segal–Bargmann–Fock operations

An application of holomorphic functions in quantum mechanics is in describing the phase space for a quantum particle moving in `R^(n)`. Here the Segal–Bargmann–Fock (`SBF`) space is employed ([Guillemin, 1984](#Ch015_271-288_B9780443136979000291.xhtml#bib5)). It is a Hilbert space, with an inner product developed so that creation `aj^†` and annihilation operators `ak` commute among themselves, and such that `aj^†` is the adjoint of `aj`. The inner product of two holomorphic functions `F` and `G` in `C^(n)` is for functions in `L²(C^(n))` and is `<F, G>`, which equals the integral, ∫(`F`(*z*) \* `G`(*z*)*e*^( − |*z*|²))*d**z*![Equation](Images/F000291si94.png) where `dz` is the 2n-dimensional Lebesgue measure on *C*^(*n*)![Equation](Images/F000291si95.png). The representation is a Gaussian-type integral.

Fock observed that conjugate coordinate operations in complex variables obey the commutation relations. Accordingly, the conjugate coordinate operations are a form of the Cauchy Riemann criteria for analyticity. These equations involve partial derivatives: `∂ /∂zj*`=1/2 (`∂/∂xj`+i`∂/∂yj`) and `∂/∂zj`=1/2 (`∂/∂xj`−i`∂ ∂/∂yj`). A holomorphic function can never be a function of `z*`, so the partial derivative of any analytic function `F` is such that `∂F/∂zj*`=0. Forgetting about Planck’s constant and identifying `zj` with multiplication-type operation and the partial derivative `∂/∂zk` with the momentum operation, then the commutators: [`zj`, `zk`]=[`∂/∂zj`, `∂/∂zk`]=0, and [`∂/d∂zj`, `zk`]=0 for `j` not equal to `k`, and one when they are equal. Here, `aj*` is the raising or creating operation, and `aj` is the lowering or annihilating operation with the domain of holomorphic polynomials, which is a dense subspace of `SBF`.

## 15.11 Many-body systems and the Landau many-body expansion

Second quantization provides the foundation for many-body quantum systems. Fock space provides a basic setting along with bosonic and fermionic creation and annihilation operations. Representations are given for one-body operators. These operators manipulate single particles in N-dimensional Hilbert space. Similarly, two-body operators are described, which illustrate the interaction between particles.

Landau presented an expansion involving the number of interacting particles produced by operators of various arity with interacting arguments. For operators of arity one, also called single-body or single-particle operators, they are denoted by `T1`. The operators of arity two whose operands interact with each other are called two-particle or two-body operators and are denoted by `T2`. The operators of arity three whose operands interact with each other are called three-particle or three-body operators and are denoted by `T3`. And so on.

The expansion is as follows: Sum, 

```
\\sum\\limits\\_{j}{{T1j} + {Sum}},{\\sum\\limits\\_{j < k}{{T2jk} + {Sum}},{\\sum\\limits\\_{j < k < m}{{T3jkm} + \\ldots}}
```

![Equation](Images/F000291si96.png)

In second quantization, this expansion involves the bosonic or fermionic creation operators `a^†`![Equation](Images/F000291si97.png) and `c^†`![Equation](Images/F000291si98.png), as well as the annihilation operators `a` and `c`, respectively. In this case, the expansion is as follows: Sum, 

```
\\sum\\limits\\_{j,k}{\\left. {{T1aj}^{\\dagger}{ak}} \\right) + {1/2}{({Sum}}},{\\sum\\limits\\_{j,k,m,n}{{{{T2aj}^{\\dagger}{ak}^{\\dagger}{an}{am}})} + \\ldots}}
```

![Equation](Images/F000291si99.png) This expansion was used for bosons, but the same expansion holds for fermions. The creation and annihilation operations are given next with applications to the one-body and two-body problem in second quantum.

## 15.12 Single-body operations

Single-particle or one-body operators are defined in N particle Fock space as summation, 

```
\\sum\\_{k = 1}^{N}{bk}
```

![Equation](Images/F000291si100.png), where `bk` is an operator acting on the kth particle state. Of principal importance is the number operator `nk`, which is the number of particles in location k. The quantity `nk`=`ak^†ak`; here it is given for bosons. Recall the eigenstate (`ak^†`)^(*k*) |vac> of the number operator has eigenvalue k, that is, `nk` (`ak^†`)^(*k*) |vac>=k (`ak^†`)^(*k*) |vac>. Moreover, the creation operator `aj^†` (|…, `nj`, …>)=( `nj+1`)^(1/2) (|…, `nj+1`, …>), and the annihilator operator is such that `aj` |…, `nj`, …>= `nj^(1/2)` |…, `nj−1`,…>. For the fermionic Fock space, the number operator is `nk`=`ck^†ck`. The creation operator this time is `cj^†`(|…, `nj`, …>)=(1−`nj`)^(1/2) (|…, 1−`nj`, …>), and annihilation operator is such that `cj` (|…, `nj`, …>)=( `nj`)^(1/2) (|…, 1−`nj`, …>). The large difference between bosonic and fermion operators is that the former is symmetric in the creation of two particles, and the latter is antisymmetric. That is, `aj^†ak^†|0>`=`ak^†aj^†|0>`=`|1j 1k>`, but `cj^†ck^†|0>`=`− ck^†cj^†|0>`=`|1j 1k>`=`− |1k 1j>`.
