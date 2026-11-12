Subsequently, an equal number (\(\alpha \cdot |U'|\)) of new samples are randomly selected from the \(\mathcal{D}_{poisoned} \setminus U'\). This iterative process continues until completion.

However, the FUS strategy has limitations: the filtering ratio \(\alpha\) is fixed, and sample selection relies solely on direct removal without dynamic adjustment based on real-time sample performance. To address these issues, we propose a Dynamically Adjusted Filtering-and-Updating Strategy (DAFUS). We observe that the same poisoned sample may exhibit varying \(F_n\) when trained with different poisoned sample pools. Moreover, because we employ an early stopping mechanism during training, the number of training epochs can further influence the \(F_n\) value of a given poisoned sample. Therefore, instead of adjusting based on the average number of forgetting samples, we dynamically adapt the selection based on the attack success rate. We define the change in ASR as:

\(\Delta\text{ASR} = \text{ASR}_s - \text{ASR}_{s-1}.\) (11)

The update ratio \(\alpha\) for poisoned samples is dynamically adjusted as follows:

\(\alpha_s = \begin{cases} \alpha_{s-1} - \eta_1 \times (\Delta\text{ASR}), & \text{if } \Delta\text{ASR} > \Delta_{\text{th}}, \\ \alpha_{s-1} + \eta_2 \times (|\Delta\text{ASR}|), & \text{if } |\Delta\text{ASR}| \le \Delta_{\text{th}}, \\ \alpha_{s-1}, \quad U_s = U_{s-1}, & \text{if } \Delta\text{ASR} < -\Delta_{\text{th}}. \end{cases}\) (12)

where \(\Delta_{\text{th}}\) represents a predefined threshold that distinguishes significant changes in ASR, \(\eta_1\) and \(\eta_2\) are adjustment rates that determine the magnitude of adjustments, and \(U_s\) denotes the backdoor training set at iteration \(s\).

+   - When the ASR increases significantly (\(\Delta\text{ASR} > \Delta_{\text{th}}\)), the update ratio \(\alpha\) is proportionally reduced based on the increase in ASR. This ensures that high-contribution samples are retained, preventing excessive replacement.
+   - When the change in ASR is insignificant (\(|\Delta\text{ASR}| \le \Delta_{\text{th}}\)), the update ratio \(\alpha\) increases proportionally according to the magnitude of the variation in ASR. This enhances exploration and mitigates the risk of being trapped in a local optimum.
+   - When the ASR decreases significantly (\(\Delta\text{ASR} < -\Delta_{\text{th}}\)), the poisoned sample set is immediately reverted to the previous iteration (\(U_s = U_{s-1}\)). This rollback mechanism helps restore attack effectiveness, which may have been compromised due to the removal of high-contribution samples.

We maintain an index of the poisoned samples for each iteration and ultimately select the sample set corresponding to the highest ASR as the final poisoning set. This strategy effectively balances exploration and exploitation by adaptively adjusting the update ratio of poisoned samples, leading to improved attack performance. We summarized the overall process of our attack framework in Algorithm 1.