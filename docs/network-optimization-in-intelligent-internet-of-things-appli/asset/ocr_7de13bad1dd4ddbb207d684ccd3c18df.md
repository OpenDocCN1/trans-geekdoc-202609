# 236 Network Optimization in Intelligent IoT Applications

satisfy both memory and real-time requirements. This triggers an additional learner, updating the samples present in the AW to enhance the learner's reliability further. After this potential drift detection and learner update, the system transitions back to its normal state, for any forthcoming drift detections (lines 26–35).

Conversely, if the accuracy of the SW stabilizes or even increases to the regular level during the warning phase, it will be treated as a false alarm. Subsequently, the AW will be reset, and the system will revert to its normal state, to monitor any possible subsequent drift occurrences (lines 19–24).

# Algorithm 13.1: Optimal Sliding and Adaptive Windowing (OSA)

Input:

Str: streaming network traffic data,
i: th, for warning and drift
p: the constant size of the $sliding\window$,
pp'_{max}$: upper limit on the adaptive window's size,
Model: A Machine Learning model,

Output:

Acc$_{max}$: Performance Metrics.

```
1 $Drift\Adapt(Str, i, j, p, p'_{max})$;
2 $AW \leftarrow \varnothing$; // Adaptive window initialization
3 $St \leftarrow 0$; // States: normal, drift, warning
4 for each sample $n_k \in Str$ do$ // last $p$ sliding window of $n_k$
5 $SW_k; AccSW_k \leftarrow accuracy(SW_k)$; // Present window accuracy
6 $AccSW_{k-p} \leftarrow accuracy(SW_{k-p})$; // Previous window accuracy
7 $if (St = 0) \&\& (AccSW_k < <* AccSW_{k-p})$
8 then// Transition to warning from normal state
9 $AW \leftarrow AW \cup \{n_k\}$; // Start collecting new instances in $AW$
10 $St \leftarrow 1$; // In warning\_state
11 end
12 $if (St = 1)$ then // warning\_state
13 $p' \leftarrow Size(AW)$;
14 $ifAccSW_k < j*AccSW_{k-p}$, then//Current window accuracy falls to drift
15 $St \leftarrow 2$; // Enter drift state
16 $f \leftarrow k$; // Store first new concept\nwindow accuracy as baseline
17 $Model \leftarrow Retrain Classifier on $AW'$
// classifier retrained on new\_samples
```