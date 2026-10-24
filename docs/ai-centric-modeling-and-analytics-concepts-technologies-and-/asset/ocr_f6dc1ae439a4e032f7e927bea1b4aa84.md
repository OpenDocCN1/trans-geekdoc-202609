```
$$\begin{align}P_{\text {best}}(i, t) &= \operatorname{argmin}\left[\left[f\left(P_{i}(K)\right)\right], k=1, \ldots, t\right. \tag {13.1} \\G_{\text {best}}(t) &= \operatorname{argmin}\left[\left[f\left(P_{i}(K)\right)\right], i=1 \ldots N_{p}\right. \tag {13.2}\end{align}$$
```

where $i$ stands for the particle index, and $N_p$ is the overall particle count. Updates to particle position $P$ and velocity $V$ are calculated using Equations 13.3 and 13.4:

```
$$\begin{gather}V_{i}(t+1)=w V_{i}(t)+c 1 r 1\left(P_{\text {best }}(i, t)-P_{i}(t)\right)+c 2 r 2\left(G_{\text {best }}(t)-P_{i}(t)\right) \tag {13.3} \\P_{i}(t+1)=P_{i}(t)+V_{i}(t+1) \tag {13.4}\end{gather}$$
```

where $w$ is the inertia weight, $V$ is the speed, $r 1$ and $r 2$ are random variables with uni-form distributions in the range $[0,1]$, and $c 1$ and $c 2$ are “acceleration coefficients.”

The enhanced PSO pseudocode is described as follows:

+   • **Step 1.** Enter the raw material and the processing time data for the batik production process, then initialize the PSO settings.
+   • **Step 2.** Execute the program, and save it with the highest fitness value ($G_{\text {best }}$).
+   • **Step 3.** Update the velocity particles.
+   • **Step 4.** Update the particle’s location.
+   • **Step 5.** Slightly reduce the inertia weight () from 0.9 to 0.4.
+   • **Step 6.** Verify whether the position of the particle has been violated: if pos(j) > mp, then pos(j) = mp. If the particle position pos(j) = 1, otherwise.
+   • **Step 7.** If the velocity of particle vel(j) > mv, then vel(j) = mv, as a test for particle velocity violation. Alternatively, if the particle’s velocity is vel(j)- mv, then its pos(j) is equal to -mv.
+   • **Step 8.** Linearly reduce the weight of inertia () from 0.9 to 0.4. Until a cri-terion is attained, repeat steps 2–8.

The hybrid PSO technique is described in Code block 13.1.
Code block 13.1. Algorithm for hybird PSO technique.

```
```
G_best: The best position is found so far
1. start
2. Initialize the swarm randomly;
3. for i = 1 to N do
4. vi = a random vector within [LB, UB]^D;
5. vi = a random vector within [LB, UB]^D;
6. P_best_i = X_i;
7. end for
8. to find G_best;
9. t = 1;
10. while t <= T do
11. for i = 1 to N do
12. r1, r2 <- two independent vectors randomly generated from [0,1]^D;
```
```