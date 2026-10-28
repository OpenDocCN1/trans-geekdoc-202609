![](bbox=[0.08, 0.1, 0.5, 0.38])

![](bbox=[0.52, 0.1, 0.92, 0.38])

(a) BERTScore similarity with original DBPEDIA abstracts

(b) BERTScore similarity with self-ROUGE summaries

# Figure 5. BERTScore for abstracts with different sentence lengths in 6 languages.

# Table 4. Human evaluation of the LLM-generated summaries in 6 languages. The average rate of annotators’ agreement = 0.71

|  | English | Spanish | German | French | Italian | Dutch |
|---|---|---|---|---|---|---|
| Short-abstracts | 28% | **48%** | 32% | **36%** | **46%** | 35% |
| T5 | 4% | 2% | **45%** | 25% | 12% | 9% |
| BART_large-50 | 22% | 42% | 6% | 24% | 34% | **36%** |
| BART_large-CNN | **36%** | 8% | 6% | 15% | 7% | 16% |
| BART_weak-sup | 9% | 0% | 11% | 0% | 1% | 4% |

36% selected the BART_large-50-generated summaries in Dutch. For Spanish, French, and Italian languages, the annotators selected short abstracts instead. These results suggest that the length of DBPEDIA abstracts influences human preferences. For shorter abstracts (less than five sentences), human annotators preferred short abstracts. For longer abstracts (more than five sentences), they selected the LLMs-generated summaries. This implies that short abstracts are informative enough in the case of full DBPEDIA abstracts with short content and do not need further summarization. In contrast, longer DBPEDIA abstracts can be summarized efficiently using pre-trained large language models.

In the second experiment, we performed another crowdsourcing evaluation to assess the quality of the generated summaries and short abstracts based on four criteria: informativeness, coherence, conciseness, and fluency. We used a 4-point scale, where 1 is the lowest and 4 is the highest rating. Each summary was compared with the original DBPEDIA abstract by three crowdworkers, following the same procedure as in the first experiment. The evaluation results in Table 5 demonstrate that the T5 model outperforms the other models in terms of informativeness and conciseness, whereas the BART_large-50 model performs better in terms of coherence and fluency.

Finally, we performed an in-depth analysis of the generated summaries and short abstracts based on their length, in the same manner, in Section 5.1. We used the same categorization of DBPEDIA abstracts based on the number of sentences Figure 6. We observe that T5 and BART_large-50 produced more informative and coherent summaries than short abstracts for DBPEDIA summaries with more than 9 sentences. Moreover,