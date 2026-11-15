![](bbox=[0.17, 0.1, 0.83, 0.43])

Figure 3.5: Comparison of ABC against state-of-the-art cascade baselines for black-box API-based inference. The faded, hatched-patterned variants represent budget-friendly, 2-level cascade instances where we do not include the costly Tier 3. Most of these methods show competitive performance, but ABC matches their accuracy at significantly lower costs in all tasks. Note that all these methods (aside from the MoT-LLM cascade) incur additional setup costs not reflected in our plots.

Appendix. We can see at least a 3× reduction in cost in terms of $/hour for image tasks, and a more moderate 10-30% reduction in language tasks.

# Monetary Cost for Black-box API-Based Inference

In the current landscape dominated by LLMs, many providers offer black-box API access to their proprietary LLMs [160, 164, 191]. Similarly to the large cost difference between GPU generations discussed in the previous subsection, we also observe a large cost disparity between various generations/tiers of API calls. For example, using Together.ai—one of the lowest-cost serverless endpoint providers for LLMs¹—as a case study, we find that models within the 7B-8B range cost $0.20 per million tokens, while LlaMA3.1-405B costs $5.00. This translates to the larger model costing 25× more than the smaller model range ($\gamma = \frac{1}{25}, \rho = 1$). If we consider GPT-4 as the gold

¹together.ai/pricing as of September 2024.