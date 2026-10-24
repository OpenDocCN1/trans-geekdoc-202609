where \(d^i\) is the difference of the i-th state variable, \(v^i\), normalized by the observed range in the history, i.e.,

\(d^i = \frac{v_k^i - v_{now}^i}{v_{max}^i - v_{min}^i}\)

where \(v_{min}\) and \(v_{max}\) are the minimum and maximum values for \(v^i\) in the history. The normalization (which leads to a difference between 0 and 1) is important because it prevents a variable with a significant change of values from dominating the overall difference.

For the configuration component, the difference is either 0, if the configuration remains identical, or 1, if the configuration is different in anyway because even a slight change in configuration may result in a significant functional change in the node or application process.

The weight for the \(S \rightarrow D\) edge is computed as follows:

\(E(S \rightarrow D) = \frac{\sum_{k=1}^N (1 - |D_k - D_{now}|) \times w_k}{\sum_{k=1}^N w_k}\)

where \(w_k\) is the weight assigned to chunk \(k\) and it is determined by the state differences for S:

\(w_k = \begin{cases} 1 - |S_k - S_{now}|, & \text{if } |S_k - S_{now}| \le \delta \\ 0, & \text{otherwise} \end{cases}\)

where \(\delta\) is heuristically set to be 1/3 in [20]. The weighing scheme assigns a higher weight on historical states that are more similar. Furthermore, it excludes the chunks where the most similar state differs from \(S_{now}\) by more than \(\delta\). This is a rational decision because it is baseless to compute the state differences for \(D\) when the state for \(S\) is significantly different from \(S_{now}\).

It may occur that no useable historical data can be found (i.e., \(w_k = 0\) for \(k = 1, ... N\)), the edge weight is set to be 0.8 (obviously Equation 3.6 cannot be used for the calculation in this case). The decision for assigning a high weight to the edge is based on the assumption that the abnormality is more likely caused by a component that has not been seen in a similar state before. This is consistent with the principle that we would rather see false positive than failing to diagnose a faulty component.

The final step is to predict the root causes of the abnormality. The causality of the abnormality of a component is inferred from