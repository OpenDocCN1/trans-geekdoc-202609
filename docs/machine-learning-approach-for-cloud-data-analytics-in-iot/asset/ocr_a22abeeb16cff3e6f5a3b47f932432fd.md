Where

$U^{Rank}(X_{i}) = \begin{cases} AET(X_{i}) + \max _{X \in \operatorname{SUC}(X_{i})} \left(CT_{i, j} + U^{Rank}(X_{j})\right) \text { if } X_{i} \neq X_{\text {exit }} \\ AET\left(X_{\text {exit }}\right) & \text { f } X_{i} = X_{\text {exit }} \end{cases}$

$U^{Rank}(X_{i}) = \begin{cases} \max _{X_{j} \in \operatorname{PRE}(X_{i})} \left\{D^{Rank}(X_{j}) + AET(X_{j}) + CT_{i, j}\right\} & \text { if } X_{i} \neq X_{\text {entry }} \\ 0 & \text { f } X_{i} = X_{\text {entry }} \end{cases}$

where $PRE(X_{i})$ as a finite predecessor set of task $X_{i}$. Formal definition of $D^{Rank}(X_{i})$ is the greatest distance from $X_{\text {entry }}$ to $X_{i}$ and avoid the average execution time AET($X_{i}$).

+   b.  Critical Path Tasks

It has a critical path length $\left|\mathrm{C}^{\mathrm{p}}\right|$ which is the length of the greatest path from $X_{\text {entry }}$ to $X_{\text {exit }}$ of the given DAG $\text {. }$ The value of $\left|\mathrm{C}^{\mathrm{p}}\right|$ is $X_{\text {entry }}^{Priority}(X_{\text {entry }})$. This phase also identify the critical path tasks of the given $\mathrm{DAG}_{1}$ which is expressed as follows:

It is designated by $CP_{\mathrm{SET}}$ and computed [24] as

```
Step 1: $\mathrm{CP}_{\mathrm{SET}}=\{X_{\text {entry }}\}$
Step 2: $\mathrm{X}=X_{\text {entry }}$
Step 3: while $X \neq X_{\text {exit }}$ then
		Find successors of $X$ as $X_{j}$
		If $T_{j}^{Priority}(X)=\left|C^{P}\right|$ then
			$CP_{\mathrm{SET}}=CP_{\mathrm{SET}} \cup\{X\}$
		\Otherwise
			$X=X_{j}$
		End While.
Step 4: stop.
```

This algorithm helps to compute the all tasks on critical path of the given DAG.

+   c.  Critical Path VM

It identifies the virtual machine which takes minimum execution time while computing all critical path tasks $\mathrm{CP}_{\mathrm{SET}}$ on the same VM, i.e.,