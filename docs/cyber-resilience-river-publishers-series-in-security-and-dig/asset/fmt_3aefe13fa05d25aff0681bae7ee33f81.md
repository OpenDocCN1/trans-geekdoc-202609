
## Conclusion 1

When the transitions fired `T[2] = (t[1], t[3], t[2], t[4])` there is the `t[1] - t[2] - t[4]` process lockout by the `t[1] — t[3] — t[4]` process. Both processes intersect in the position `p[5]`. Therefore, we will clarify that the function or command `p[5]` firing is because of the process lockout by another process based on the persistence feature.

### The transition activity

Let us construct a table of the transition activity in the `Petri net` ([Table 1.4](#Ch02.xhtml#cap_lbl0071)).

**Table 1.4** The transition table for the `Petri net`

| Transitions/Activity Levels | U[0]Dead | U[1] Potentially Active | U[2] Fires S Times | U[3] Infinite |
| --- | --- | --- | --- | --- |
| t1 | | | * | | |
| t2 | | | * | | |
| t3 | | | * | | |
| t4 | * | * | | | |

## Conclusion 2

The transition `t[4]` has activity levels **0** and **1** that it there is a condition when the transition `t[4]` is a deadlock. The detection of the deadlock and looping commands is important for program fault detection but in the context of the above analysis the transition `t[4]` in interesting as it has a double activity that is a fault indicator.

### Net security

The net `N = (P, T, I, O, μ)` is not secure, as ∃ marking `μ = (0, 0, 0, 1, 2, 0)`, `μ(p[5]) = 2 > k = l`.

## Conclusion 3

`μ(p[5]) = 2`, that means there is no unambiguous control transfer for each action in the position `p[5]`. This fact proves the given statements about the fault presence and shows that the control transfer happens outside the program address space.

The `Petri net` analysis allowed concluding that the token left in the position `p[5]` signals about the condition fulfillment, the event of which does not happen in the given net. In other words, after the procedure is finished the far call is made that allows confirming that a fault causing the destructive malicious code call to reduce the secured infrastructure cyber resilience was detected [34, 132, 133].

As a result, the proposed detection method of the critically important information infrastructural digital bomb, when there is no documentation or program source code, allows solving the given problem.

The obvious advantages are the following. There is no need to look through the whole program code listing, while searching for the destructive digital bombs. The method allows detecting the program code fragments that contain faults, signaling about the hidden digital bomb or about potential danger of their future implementation. In comparison with the known methods based on the manual processing (the performance of which is measured in human/hours), as well as the profiling methods, the proposed method is characterized by a sufficient performance, a high validity and a high efficiency of the given problem-solving. Thus, the dozen millions of the disassembled code lines were processed in a few seconds.

The method disadvantages are its dependency on disassembling correctness and completeness that needs to additionally develop the corresponding subroutines to ensure the required disassembling quality (including those for the hidden calls documentation).

## The program fault detection method development

It was required to develop the relevant methods to recover the software specifications of the secured infrastructure under the unknown heterogeneous and mass cyber-attacks. Including those methods aimed at recovering the program correctness ([Figure 1.58](#Ch02.xhtml#cap_lbl0072)) based on the multi-model analysis of the structural, logic and operational software features [21, 34, 132, 133]. The research basis is the famous and original models and methods of the modern software engineering, the graph theory (reduced control graphs) ([Figure 1.59](#Ch02.xhtml#cap_lbl0073)), Yanov's schemes ([Figures 1.60](#Ch02.xhtml#cap_lbl0074) and [1.61](#Ch02.xhtml#cap_lbl0075)), the `Petri nets` ([Figure 1.62](#Ch02.xhtml#cap_lbl0076)), systemology, dimension and similarity theories ([Figure 1.63](#Ch02.xhtml#cap_lbl0077)).

![Figure 1.58 Program code fragments.](Images/fig00068.jpg)

**Figure 1.58** Program code fragments.

![Figure 1.59 The control program graph formation.](Images/fig00069.jpg)

**Figure 1.59** The control program graph formation.

![Figure 1.60 The control graph conversion to the Yanov's scheme.](Images/fig00070.jpg)

**Figure 1.60** The control graph conversion to the Yanov's scheme.

![Figure 1.61 The Yanov scheme canonization and a productive structure formation.](Images/fig00071.jpg)

**Figure 1.61** The Yanov scheme canonization and a productive structure formation.

![Figure 1.62 The Yanov's scheme transformation into the Petri net.](Images/fig00072.jpg)

**Figure 1.62** The `Yanov's scheme` transformation into the `Petri net`.

As a result, the one-to-one relation was reached between the mentioned program representations of the critically important information infrastructure [22, 34, 132, 133]. Also, the equivalence transformation mechanism allowing reduce of the structural redundancy and sufficiently decrease the analyzed program code volumes were found (Figure 1.63) [34, 132, 133]. It was possible to connect the formally detected faults to the physical program memory addresses and to rearrange their verification in the dynamic analysis.

### The research problem formulation

The recovery correction, in contrast to traditional technologies, uses the `original emulator`, which allows revealing and partially correcting disassembling errors, noting incorrect sections, as comments. Separate calculations violations were associated with the undocumented processor commands identification, for which an additional procedure for checking the correctness was provided [34, 133, [163](#Reference.xhtml#ref0166)].

The acyclic control program graph was formed in the program, free of the errant code.

![Figure 1.63 A digital bomb suspicion detection.](Images/fig00073.jpg)

**Figure 1.63** A digital bomb suspicion detection.

Then the problem of finding the minimum coverage and the formation of all the program routes was solved. The cyclomatic complexity evaluation of the obtained control graph was made to identify the possible obfuscation. The code sections with a complex structure were marked. Then the program logic model was formed as a graph-oriented `Yanov's scheme` (Figure 1.60).

The selected device has a set of equivalent conversion rules and a procedure for reducing the arbitrary schemes to a canonical form (Figure 1.62), which made possible the decreasing of the structural redundancy and test the potential program feasibility.

Afterwards, the transformation from the studied program `canonical scheme` to the productive form was carried out. This allowed to identify some classes of the computation logic violations, potentially looped sections and paths leading to the `dead` program code.

According to the productive scheme with the marked faults, an equivalent graph-oriented `Petri net` with naught check was synthesized (Figure 1.63). This program presentation allowed to examine the potential completeness of its calculations and formally identifying some operational faults in its formation [43, 44, 154].

Here the studied program operational faults of the secured infrastructure appeared, when an inhibitory arc had occurred. In order to identify it, it was required to obtain a linear equations system solution and to perform a feature analysis of reachability, security, persistence, and activity of positions and transitions, according to the transition equation.
