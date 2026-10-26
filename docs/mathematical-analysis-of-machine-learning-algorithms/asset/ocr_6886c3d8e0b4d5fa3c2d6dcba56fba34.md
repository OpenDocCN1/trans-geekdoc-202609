# **Algorithm 10.3** Gradient Boosting for $L_1$ Constrained Optimization

+   **Input:** $\mathcal{S}_n$, $\Psi$, $L(\cdot,\cdot)$, $\gamma$, $\{\eta_t > 0\}$
+   **Output:** $f^{(T)}(x)$
+   1 Let $f^{(0)}(x)=0$
+   2 **for** $t = 1,2,\dots,T$ **do**
+   3 Let $g_i = L_1(f^{(t-1)}(X_i),Y_i)$ $(i=1,\dots,n)$ be the functional gradients
+   4 Solve for $\theta_t = \arg\min_{\theta\in\Theta}\sum_{i=1}^n[\gamma\eta_t\psi(\theta,X_i)+g_i]^2$
+   5 Let $f^{(t)}(x) = (1-\eta_t)f^{(t-1)}(x)+\eta_t\psi(\theta_t,x)$
+   **Return:** $f^{(T)}(x)$

The following result shows that Algorithm 10.3 converges to the solution of $L_1$ regularization problem.

# **Theorem 10.31**

*Assume that $\sup_{\theta}\|\psi(\theta,\cdot)\|_{L_2(\mathcal{S}_n)} \le B$, and $L(f,y)$ is a $\gamma$-smooth convex function with respect to $f$. If we take $\eta_t = 2/(t+1)$ in Algorithm 10.3, then*

$\frac{1}{n}\sum_{i=1}^n L(f^{(t)}(X_i),Y_i) \le \inf_{f\in\mathrm{CONV}(\Psi)} \frac{1}{n}\sum_{i=1}^n L(f(X_i),Y_i) + \frac{10\gamma B^2}{T+1}.$

*Proof*  Consider

$f(x)=\sum_{j=1}^m u_j\psi(\tilde{\theta}_j,x)$

where $u_j \ge 0$, and $\sum_{j=1}^m u_j = 1$. We obtain from the definition of $\eta_t$ that for all $j = 1,\dots,m$,

$2\eta_t\sum_{i=1}^n g_i\psi(\theta_t,X_i)+\gamma\eta_t^2\sum_{i=1}^n\psi(\theta_t,X_i)^2 \le 2\eta_t\sum_{i=1}^n g_i\psi(\tilde{\theta}_j,X_i)+\gamma\eta_t^2\sum_{i=1}^n\psi(\tilde{\theta}_j,X_i)^2.$

Now multiplying the inequality by $u_j$ and then summing over $j$, we obtain

$2\eta_t\sum_{i=1}^n g_i\psi(\theta_t,X_i)+\gamma\eta_t^2\sum_{i=1}^n\psi(\theta_t,X_i)^2 \le 2\eta_t\sum_{i=1}^n g_i\sum_{j=1}^m u_j\psi(\tilde{\theta}_j,X_i)+\gamma\eta_t^2\sum_{j=1}^m u_j\sum_{i=1}^n\psi(\tilde{\theta}_j,X_i)^2.$

Therefore,

$\eta_t\sum_{i=1}^n g_i\psi(\theta_t,X_i) \le \eta_t\sum_{i=1}^n g_i f(X_i) + \frac{n\gamma}{2}\eta_t^2 B^2. \qquad (10.18)$