traitorous lieutenant (G2) ( circled in Figure 7.1) tells lieutenant 1 (G1) that the command it has received from the commander (G0) is “Retreat”. In the second scenario, the commander (G0) issues an “Attack” to lieutenant 1 (G1), but a “Retreat” command to lieutenant 2 (G2). The two lieutenants (G1 and G2) inform each other the commands they have received.

![](bbox=[0.23, 0.24, 0.76, 0.51])

**Figure 7.1** Two scenarios that highlight why it is impossible to use 3 generals to solve the Byzantine generals problem.

In both scenarios, lieutenant 1 (G1) receives two conflicting commands. If a lieutenant defaults to “Retreat” in case of receiving conflicting commands, the final decision would happen to be consistent among loyal generals (G1 and G2) in scenario 2 because lieutenant 2 (G2) would also decide to retreat. However, in scenario 1, lieutenant 1 (G1) would decide to retreat, which is different from the command issued by the loyal commander, thereby violating the interactive consistency requirement.

Note that from the scenarios shown in Figure 7.1, it may appear that if all loyal lieutenants default to “Attack” in case of receiving conflicting commands, both G1 and G2 would reach consistent decision in scenario 2, and G1 would also reach a consistent decision (i.e., “Attack”) with the commander G0. Unfortunately, defaulting to “Attack” will not work if the loyal commander G0 issues a “Retreat” command instead of “Attack”.