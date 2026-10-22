![](bbox=[0.12, 0.07, 0.88, 0.18])

# (a) instruct LLMs

# (b) base LLMs

Figure 5.14: Characteristic phrases for instruct¹ and base LLMs.

![](bbox=[0.12, 0.25, 0.82, 0.45])

# (a) instruct LLMs

# (b) base LLMs

Figure 5.15: Distribution of first word choices in instruct and base LLMs.

# 5.7.8 Unique Markdown Formatting

In this part, we provide additional results for the analysis of markdown formatting as presented in Section 5.4.2. Figure 5.16 illustrates the distribution counts of six markdown formatting elements across different models. For both chat API models (Figure 5.16a) and instruct LLMs (Figure 5.16b), we observe distinct differences in the usage of bold texts, headers, enumerations, and bullet points, while italic texts show less variation. Intriguingly, Gemini uses much more italic texts (a lower density at zero in the italic text) than other chat APIs, where similar observations can be found on Gemma2.

# 5.7.9 Open-ended Language Analysis

Ablation on LLM judges. Here we demonstrate our findings in Figure 5.9 of Section 5.4.3 remains consistent under several LLM judges. Specifically, we change the LLM judge from ChatGPT to Claude, Grok, and Gemini. We show the results in Figure 5.17. Regardless of the choice of LLM judges, our language analysis reveals that ChatGPT often uses detailed

¹In Llama of instruct LLMs, the phrase “explanation the” corresponds to a markdown header or bold text for “explanation” followed by a new sentence starting with “the”.