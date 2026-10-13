
| 3 || *O*[3] || *Ok*[2] || Duration U(*P* > 1) || *t*[1] + *t*[2] || *t*[3] |

The second sub-step. In comparison with this structure, verification of the synthesized scheme of the program will be concluded.

The third sub-step is the reproduction of instances of `UMTO` by the number of operations in the specification, which corresponds to the number of rows in Table 2.10. Forming the required number of instances of the primitive, the individual parameters will be the variable start-up delay (variable `<StartDel>`) and late completion of the operation (variable `<DE>`). The arc multiplicity `<Duration>` is set by equal variable `T[k]`:

```
F < OCExc, ExcControl > = < Duration > = T_k, OCExc ∈ P_int, P_int ∈ P ExcCont ∈ T, S_k = < P, T, ... > (2.39)
```

The variables `<STARTDEL>` and `<DE>` are used if necessary and are represented by the corresponding multiplicity of arcs. For example, from Table 2.10 we get:

```
S = {S[1], S[2], S[3]}; S[1]: F < ExcEvCount, ExcCont > = t[1]; S[2]: F < ExcEvCount, ExcCont > = t[2]; S[3]: F < ExcEvCount, ExcCont > = t[3]; M(P[in]^(k)) = 0, k = 1...3. (2.40)
```

According to the results of the third sub-step, the scheme of the synthesized program will take the form of [Figure 2.26](#Ch03.xhtml#cap_lbl0210).

At the fourth and fifth substeps, a structure of pragmatic features of the calculations that determine the order of operations is formed. It is necessary to determine the transition from the elements of the tuple `R` to the input variable "Start" and "Stop" for each instance `UMTO` tuple `R^I`. The operation number is determined by the variable `k`. The value of the variable "Start" is determined by the result of checking the predicate `Pr(B[b]^(k))`:

![Figure 2.26 Scheme of the program after the third sub-step.](Images/fig00146.jpg)

[**Figure 2.26**](#Ch03.xhtml#bck_cap_lbl0210) Scheme of the program after the third sub-step.

```
M(start) { 1, if pr(B_b^(k)) = true; 0, if pr(B_b^(k)) = false } (2.41)
```

The value of the variable "Stop" is determined by the testing result of the `Pr(B[f]^(k))` predicate:

```
M(stop) { 1, if pr(B_f^(k)) = true; 0, if pr(B_f^(k)) = false } (2.42)
```

The input variables "CE", "ExcPause" and "ExcCont" and internal variables `<StartDel>` and `<DE>` are unique and do not require the determination of the elements of a tuple `R^I`.

The logical condition for the start of the `k`-th operation is described using the following relation:

```
B[pr[b]]: Pr(B[f]^(1)) × Pr(B[b]^(k)) → J[in]: P[out]^(1) × P[in]^(k) → N; P[in]^(k) = {CE, Start, Pause, Continuation} (2.43)
```

The ratio `B[pr[b]]` defines the ratio of the `l`-th and `k`-th operations. Ratio `B[pr[b]]` is converted to the incidence function `J[in]` between the output variables of the `l`-th and input variables of the k-th operation. This function will determine the start condition of the `k`-th operation. This is ensured by the presence of the `Start` variable in the set `P[in]^(k)`.

The logical condition for the termination of the `k`-th operation is described by the ratio:

```
B[pr[f]]: Pr(B[f]^(m)) × Pr(B[b]^(k)) → J[in]: P[out]^(m) × P[in]^(k) → N; P[in]^(k) = {CE, Stop, Pause, Continuation} (2.44)
```

Ratio `B[pr[f]]` determines the relationship of the `m`-th and `k`-th operations. Ratio `B[pr[f]]` is also converted to the incidence function `J[in]` between the output variables of the `m`-th and input variables of the `k`-th operations. But only this function will determine the end condition of the `k`-th operation. This is ensured by the presence of the variable "Stop" in the set `P[in]^(k)`.

The specific list of the used variables `P[in]`, `P[out]` ε `P` is determined by the type of the relationship `B[pr[b]]` and `B[pr[f]]`. The component `J[out]` of the `J` incident vector function of the previous operation is formed automatically, when the component `J[in]` of the `J` incidence vector function of the next operation is formed. For the considered example at this stage the scheme will take the following form ([Figure 2.27](#Ch03.xhtml#cap_lbl0216)):

The program diagram in Figure 2.27 corresponds to the following set of incidence functions:

```
J_1 = ( J_in^(1) = { J_in^(1) < K, Start > = 1 }; J_out^(1) = { J_in^(1) < IndFinDur, Start^(2) > = 1 } )
J_2 = ( J_in^(2) = J_in^(2){ J_in^(1) < IndFinDur^(1), Start > = 1 }; J_out^(2) = { J_out^(2) < IndFinDur, Start^(3) > = 1 } )
J_3 = ( J_in^(3) = J_in_1^(3){ < IndFinDur^(2), Start > = 1 }; J_out^(3) = { J_out1^(3) < IndFin, - > = 1; J_out2^(3) < IndFinDur, - > = 1 } ) (2.45)
```

![Figure 2.27 Scheme of the program after sub-step 5.](Images/fig00149.jpg)

[**Figure 2.27**](#Ch03.xhtml#bck_cap_lbl0216) Scheme of the program after sub-step 5.

Let us consider the incidence function `J[1]` for the `S[1]` operation. The input function `J[in]^(1)` contains a tuple `< K, Start >`, establishing a single arc between the variables K and "Start". This tuple is interpreted as follows: the condition for the start of `S[1]` operation is the fact that the signal "K" has arrived. The output function `J[out]^(1)` contains a tuple `< IndFinDur, Start >` establishing a single arc between the output variable "IndFinDur" of the current operation and "Start" of `S[2]` operation. This tuple is interpreted as follows: the condition for the beginning of the execution of `S[2]` operation is the fact that the execution of operation `S[1]` is completed.
