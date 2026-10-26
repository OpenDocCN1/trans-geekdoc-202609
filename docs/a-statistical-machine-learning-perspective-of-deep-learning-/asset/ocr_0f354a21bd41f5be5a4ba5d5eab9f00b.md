# Convergence Guarantee

+   - Take-home message:
+     - Under full broadcasting, given a properly-chosen learning rate, all local worker parameters $W_p^c$ eventually converge to stationary points (i.e. local minima) of the objective function, despite the fact that SV transmission can be delayed by up to $s$ iterations.
+     - Under partial broadcasting, the algorithm converges to a $O(LG(P - Q))$ neighbourhood if $C \to \infty$.