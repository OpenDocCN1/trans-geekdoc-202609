# ### 8.2.1  Backdoor Paths and Confounders

It is important to note that the definition of the average treatment effect is conditioned on $do(t)$, not on $t$, and that $P(Y \mid do(t))$ and $P(Y \mid t)$ are generally not the same. Specifically, they are not the same when there is a so-called *backdoor path* between $T$ and $Y$. Remember that a path is a sequence of steps along edges in the graph, irrespective of their direction. A *backdoor path* is any path from $T$ to $Y$ that (1) starts with an edge going into $T$ and (2) is not blocked. The reason for the name “backdoor” is because the first edge goes backwards into $T$. (Frontdoor paths have the first edge coming out of $T$.) Recall from Chapter 3 that a path is blocked if it contains:

+   1. a causal chain motif with the middle node observed, i.e. the middle node is conditioned upon,
+   2. a common cause motif with the middle node observed, or
+   3. a common effect motif with the middle node *not* observed (this is a collider)

anywhere between $T$ and $Y$. Backdoor paths can contain (1) the common cause without observation motif and (2) the common effect with observation motif between $T$ and $Y$. The motifs that block and do not block a path are illustrated in Figure 8.3.

The lack of equality between the interventional distribution $P(Y \mid do(t))$ and the associational distribution $P(Y \mid t)$ is known as *confounding bias*.$^3$ Any middle nodes of common cause motifs along a backdoor path are *confounding variables* or *confounders*. Confounding is the central challenge to be overcome when you are trying to infer the average treatment effect in situations where intervening is not possible (you cannot do$(t)$). Section 8.5 covers how to mitigate confounding while estimating the average treatment effect.

# ### 8.2.2  An Example

Figure 8.4 shows an example of using ABC Center’s causal graph (introduced in Figure 8.1) while quantifying a causal effect. The center wants to test whether reducing a client’s high anxiety to low anxiety affects their stable housing status. There is a backdoor path from anxiety to stable housing going through wages and child care. The path begins with an arrow going into anxiety. A common cause without observation, wages $\leftarrow$ child care $\rightarrow$ stable housing, is the only other motif along the path to stable housing. It does not block the path. Child care, as the middle node of a common cause, is a confounding variable. If you can do the treatment, that is intervene on anxiety, which is represented diagrammatically with a hammer, the incoming edges to anxiety from counseling sessions and wages are removed. Now there is no backdoor path anymore, and you can proceed with the treatment effect quantification.

Often, however, you cannot do the treatment. These are *observational* rather than *interventional* settings. The observational setting is a completely different scenario than the interventional setting. Figure 8.5 shows how things play out. Since you cannot make the edge between anxiety and wages go away through intervention, you have to include the confounding variable of whether the client has child care or not in your model, and only then will you be able to do a proper causal effect quantification between anxiety and stable housing. Including, observing, or conditioning upon confounding variables

$^3$There can be confounding bias without a backdoor path in special cases involving selection bias. Selection bias is when the treatment variable and another variable are common causes for the outcome label.