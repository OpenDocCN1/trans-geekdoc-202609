essential for designing more effective and resource-efficient reasoning models
in the future.

In this chapter, we address this question by investigating the scaling of
reasoning effort in LLMs using a specific, infinitely scalable logic puzzle: the
Tents puzzle$^1$ (see Figure 9.1). This puzzle offers a controlled environment
for studying algorithmic reasoning, as its problem size can be systematically
increased, and it possesses a known linear-time solution. Our analysis focuses
on how the number of tokens used by state-of-the-art reasoning LLMs changes
as the puzzle grid size grows. In addition to reasoning effort, we also evaluate
and discuss the success rate of the models across different puzzle sizes to
provide a comprehensive view of their performance.

# 9.2 Related Work

The exploration of reasoning abilities in large language models (LLMs) is a
rapidly evolving field with significant implications for artificial intelligence.
Several benchmarks have been developed to evaluate the reasoning capabilities
of LLMs across various domains. These benchmarks provide standardized
tasks and evaluation metrics to assess and compare different models. Notable
benchmarks include GSM8K [50], ARC-AGI [48], GPQA [221], MMLU [117],
SWE-bench [138] and NPHard-eval [86]. These benchmarks cover topics from
mathematics to commonsense reasoning and coding. More recently, also math
competitions such as AIME2024 [201] have been used to evaluate the newest
models. Estermann et al. [84] have introduced PUZZLES, a benchmark
focusing on algorithmic and logical reasoning for reinforcement learning.
While this benchmark does not focus on LLMs, except for a short ablation
in the appendix, we argue that the scalability provided by the underlying
puzzles is an ideal testbed for testing extrapolative reasoning capabilities in
LLMs.

The reasoning capabilities of traditional LLMs without specific prompting
strategies are quite limited [127]. Using prompt techniques such as chain-
of-thought [281], least-to-most [311] and tree-of-thought [301], the reasoning
capabilities of traditional LLMs can be greatly improved. Lee et al. [158]
have introduced the Language of Thought Hypothesis, based on the idea
that human reasoning is rooted in language. Lee et al. propose to see the
reasoning capabilities through three different properties: Logical coherence,

$^1$The puzzle is available to play in the browser at https://www.chiairk.greenend.org.
uk/~sgtatham/puzzles/js/tents.html