
## Grover's Adaptive Search
`GAS` corresponds to the weaker version of `Pure Adaptive Search` as it cannot be guaranteed that after application of `Grover Search`, an strictly better solution would be found. It can be argued that `Grover Search` can return an objective function value, which is less than the threshold and so it does not corresponds to `Pure Adaptive Search Framework`, but, in such a case, the inferior value would be discarded and the current threshold would be treated as the output of the algorithm for the particular iteration. Thus, the overall `GAS` corresponds to weaker version of `Pure Adaptive Search`.

### Rotation Count Sequence
An important design decision of `Grover's Adaptive Search` is determination of the rotation count sequence. It is possible to determine the optimal rotation count `r` for every iteration of the `GAS` provided the information regarding improving fraction `P` of the domain is available. Thus, if the optimal rotation count is used for every run of `Grover's Search`, then a better (improved) solution will almost certainly be found in every iteration of the `GAS`. However, in real world problems, the improving fraction `P` is often unknown. An estimate of the improving fraction `P` can always be made by using all the information available at the end of an iteration and considering the nature of the problem. That is a Bayesian approach can be applied by tracking the improving fraction at every iteration through the sequence of posterior distributions, which will be subsequently used for choosing rotation count at the particular iteration. However, this kind of approach might be very complicated and cumbersome [[56](#bodymatter-003.xhtml#b_9783110670707-003_ref_056)]. Thus, other methods have been devised to strike a balance between ease of implementation and optimality of rotation count selection, which includes method based on Boyer et al. [[48](#bodymatter-003.xhtml#b_9783110670707-003_ref_048)] used by Durr and Hoyer illustrated in [[50](#bodymatter-003.xhtml#b_9783110670707-003_ref_050)].

### Benefit-to-Cost Heuristic
Another method proposed by Baritompa et al. is based on maximizing the benefit to cost ratio denoted by parameter `b` in the heuristic [[52](#bodymatter-003.xhtml#b_9783110670707-003_ref_052)]. The benefit has been taken to be the expected decrease in the improving fraction of the domain, which is difficult to ascertain without knowing the nature of the problem being solved. The cost is dependent on the rotation count. The pseudo code for heuristic is as follows:
```
1. Initialize u[0](Ω) = Ω // u[0] is a polynomial
2. For i = 1, 2, …, do: // Generating rotation count r for ith iteration
   1. E[u_i] = 1 − ∫[0]¹ u[i](Ω) dΩ
   2. β = 0
   3. For r = 0, 1, … , until E[u_i]/(r+1) < 2β, do:
      1. v(Ω) = u_i(Ω) + Ω ∫_Ω^1 g_r(P)/P du_i(P) // g_r(P) = sin²((2r + 1) sin⁻¹√P)
      2. E[v] = 1 − ∫[0]¹ v(Ω) dΩ
      3. b = (E_ui - E_v)/(r + 1)
      4. If b > β, then
         1. ȓ = r
         2. β = b
         3. u[i+1](Ω) = v(Ω)
   4. Output ȓ
```
The sequence of rotation counts produced by the heuristic is independent of the particular optimization problem and is as follows for first 33 entries [[52](#bodymatter-003.xhtml#b_9783110670707-003_ref_052)]:
`0, 0, 0, 1, 1, 0, 1, 1, 2, 1, 2, 3, 1, 4, 5, 1, 6, 2, 7, 9, 11, 13, 16, 5, 20, 24, 28, 34, 2, 41, 49, 4, 60, …`.

### Dynamic Rotation Schedule
Recently, the above heuristic method has been further studied and improved by Liu and Koehler [[56](#bodymatter-003.xhtml#b_9783110670707-003_ref_056)]. One improvement has been to simplify the calculations involved in computing distributions by employing Chebyshev polynomials, which considerably reduced the computation time. The other improvement has been to convert the above heuristic into a dynamic one, which takes into account whether the Grover search in a particular iteration was successful or not. This has been made possible by using Bayes Law to update the distribution after one complete round of Grover Search depending on success or failure of finding a better solution. The heuristic for computing dynamic rotation schedule is as follows:
```
1. Initialize u[0](Ω) = Ω
2. For i = 1, 2, …, do: // Generating rotation count r for ith iteration
   1. E_ui = 1 - ∫_0^1 u_i(Ω) dΩ
   2. β = 0
   3. For r = 0, 1, … , until E[u_i]/(r+1) < 2β, do:
      1. b = ∫_0^1 P g_r(P) du_i(P)
      2. If b > β, then
         1. ȓ = r
         2. β = b
   4. Output ȓ
   5. If Search_outcome = Success
      u_{i+1}(Ω) = [∫_0^y g_r(P) du_i(P) + ∫_y^1 y/P g_r(P) du_i(P)] / ∫_0^1 g_r(P) du_c(P)
      Else
      u_{i+1}(yΩ) = [u_i(Ω) - ∫_0^y g_r(P) du_i(P)] / [1 - ∫_0^1 g_r(P) du_c(P)]
```
Liu and Koehler have reported that formal derivation of the expected time required by the proposals, made by Durr and Hoyer [[50](#bodymatter-003.xhtml#b_9783110670707-003_ref_050)] (based on Boyer et al. algorithm [[48](#bodymatter-003.xhtml#b_9783110670707-003_ref_048)]), Baritompa et al. [[52](#bodymatter-003.xhtml#b_9783110670707-003_ref_052)] and their own improved and dynamic version [[56](#bodymatter-003.xhtml#b_9783110670707-003_ref_056)] of quantum algorithms for global optimization, is hard to derive. This is because the basic subroutine employed for searching needs knowledge of the distribution function of the improving fraction. Therefore, numerical simulations have been used to compare the methods. However, such simulation studies are computationally very expensive as they require digital computer to simulate a quantum computer. Thus, the performance of such algorithms could be investigated on only problems of small size, which have not much practical significance.

This chapter identifies that basic problem in the above global optimization algorithms is due to the dependence of basic search subroutine on the improving fraction to determine the rotation count in a particular iteration. This problem can be solved by changing quantum computation model from quantum circuit model to Adiabatic Quantum Computation (`AQC`) model.

`AQC` provides a distinct advantage over quantum circuit model on Grover's Search i.e. it eliminates the problem of overshooting. This is possible because the solution is encoded as the ground state of the Problem Hamiltonian, therefore, even if the system is evolved for time period longer than required, the system remains in the ground state of the problem Hamiltonian. This feature of `AQC` makes it possible to formally derive the expected running time of Global Optimization Algorithm based on `AQC`.

## 3.5 Problem formulation
Optimization problems that are regularly solved in machine learning and engineering domain are mostly in continuous domain. Such problems are classified as unconstrained and constrained global optimization problems. The unconstrained global optimization problems (`UCOP`) in continuous variables are generally formulated as follows:
Optimize `f(x)` where `x` = (`x[1]`, `x[2]`, ...., `x[E]`) ε `R^(E)`,
(3.13)
```
\begin{matrix}
  & {Such\, that:} \\
  & {x_{il} < x_i < x_{iu};\, where} \\
  x_i{ is the} \\
  i^{th} {variable with} \, x_{il} \,{and} \, x_{iu} \\
  {as its lower and upper limits}. \\
\end{matrix}
```
