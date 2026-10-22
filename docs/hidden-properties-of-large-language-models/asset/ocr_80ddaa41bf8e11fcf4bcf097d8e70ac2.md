![](bbox=[0.12, 0.07, 0.87, 0.23])

(a) chat APIs

(b) instruct LLMs

(c) base LLMs

Figure 5.12: Confusion matrices for N-way classifiers on three groups of LLMs: chat APIs, instruct LLMs, and base LLMs.

# 5.7.6 Words and Letters

Figure 5.13 presents the frequencies of the 20 most commonly used words (left) and all English letters (right) across instruct and base LLMs. Consistent with our observations in Section 5.4.1, we find notable differences in the distribution of commonly used words between these models, such as “the”, “and”, “to”. In contrast, the letter distributions are nearly identical.

![](bbox=[0.11, 0.46, 0.88, 0.53])

(a) instruct LLMs

(b) base LLMs

Figure 5.13: Word and letter frequencies in instruct and base LLMs.

# 5.7.7 Characteristic Phrases

We provide additional results for characteristic phrases as presented in Section 5.4.1. We follow the same methodology in Figure 5.6 to extract characteristic phrases of instruct and base LLMs. Specifically, we train a four-way logistic regression classifier on the TF-IDF features of their responses and use the coefficients to select important phrases of each model.

As shown in Figure 5.14, each instruct LLM contains quite distinct characteristic phrases. For example, Llama frequently employs terms “including” and “such as” to introduce specific examples in the output, whereas Gemma tends to engage with users using phrases “let me” and “know if”. In contrast, the extracted phrases from base LLMs are less distinctive, primarily consisting of common words such as “the”, “to”, and “you”.

Figure 5.15 illustrates the distribution of first word choices in instruct and base LLMs. Similar to chat APIs (Figure 5.7), instruct LLMs display varied distributions. However, base LLMs exhibit substantial overlap in their most frequent first words, e.g., “the”, “and”, “of”, “to”, and “in”.