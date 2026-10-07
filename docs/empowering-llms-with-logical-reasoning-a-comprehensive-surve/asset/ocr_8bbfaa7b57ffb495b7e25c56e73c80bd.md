# Empowering LLMs with Logical Reasoning: A Comprehensive Survey

Fengxiang Cheng$^1$, Haoxuan Li$^{2,3}$, Fenrong Liu$^{1,4}$, Robert van Rooij^1$
Kun Zhang$^{5,6}$ and Zhouchen Lin$^{6,7,8}$

$1$Institute for Language and Computation, University of Amsterdam
$2$Machine Learning Department, MBUZAI
$3$Department of Physics, Tsinghua University
4$Department of Philosophy, CMB
$5$Institute for Artificial Intelligence, Peking University
$6$Peng Chem Laboratory
$7$National Key Lab of AI, School of Science and Technology, Peking University
{$cheng,r.m.vanrooij}@uva.nl, hli@stu.edu.cn, fenrong@tsinghua.edu.cn, kun2@zmu.edu.cn

# Abstract

Large language models (LLMs) have achieved remarkable successes over various natural language tasks. However, recent studies have found that there are significant challenges to the reasoning abilities of LLMs. This paper aims to categorize these challenges into two aspects: (**Logical reasoning**, LLMs often fail to get the correct answer within complex problems which requires sophisticated strategies); (**Logical consistency**, LLMs are prone to producing inconsistent responses across different questions. For example, in the Macaw question-answering task LLMs answer Yes to both questions: "Does a bird have wings? Does a dog have wings?" To address this direction, we investigate various reasoning methods and provide detailed tactics of these methods. Specifically, to accurately answer complex logical questions, methods can be categorized based on relation to external solvers, prompting, and inference. We also discuss concepts of various locations of logical consistency, including implication, negation, truthfulness, consistency and composition. In addition, we review benchmark evaluation metrics and discuss research directions, such as extensions to model logic to account for uncertainty, and efficient algorithms satisfying multiple-logical consistency simultaneously.

including generation, classification and translation. However, recent studies have found that there are significant challenges to the reasoning abilities of LLMs. On one hand, handling syntax, semantics, and word tasks such as next-word prediction or masked language modeling does not ensure the logical ability of LLMs [Liu et al., 2023]. On the other hand, the primacy of LLMs in processing human-written texts, lacks high-quality logical reasoning such as logical deduction and proofs [Moshita et al., 2024]. These challenges significantly limit the ability of LLMs due to the following summarized aspects.

LLMs fail to get the correct logical answer in questions which require deductive, inductive or abstract reasoning from given premises and constraints. Specifically these questions can be broadly divided into two categories: (Determination whether a statement can be deduced from given information, namely the truth value of, true or false. For example, the premise and constraints could be Metal conductivity. Insulators do not conduct electricity. If metal is made of iron, is it a conductor? The logical question is whether the statement true, false, or unknown? Cannot conductivity. To answer this question correctly, LLMs need to conduct logical reasoning-of iron-metal-deductive electricity before concluding that iron conducts electricity and correctly select any option that can satisfy the given constraints from the multiple choices. Surprisingly, LLAMA-13B achieves 33.63% accuracy under 8-shot prompting on the logical datasets FOLIO, which is only slightly better than random guessing with an accuracy of 33.33% [Han et al., 2024]. This study reflects the restriction of LLMs in interacting real-world situations such as problem-solving and decision-making.

# 1 Introduction

Large language models (LLMs) have demonstrated performance in a broad range of natural language tasks-

LLMs are also prone to producing inconsistent responses across different questions, which is regarded as violation of logical consistency. Note that the form of logical consistency can be diverse. For example, Llama2-7b answers yes to both questions with an although on an organ-

> *Haoxuan Li is the corresponding author. *Note

![](bbox=[0.015, 0.31, 0.045, 0.68])