
![Figure 10.8 Generated lecture ranking comparison of template-based (TB), few shot (FS), and zero shot (ZS) using Gemini Pro With RAG.](html/images/9781032942346_C010_008.jpg)

**Figure 10.8** Generated lecture ranking comparison of template-based (TB), few shot (FS), and zero shot (ZS) using Gemini Pro With RAG.

[Figure 10.9](#ch20.xhtml#f79) represents the ranking of TB for each query type by plotting the number of times TB has attained ranks 1, 2, and 3. It can be observed that for each query type, it has been ranked first more than it has been ranked second or third and for ST queries it has been ranked third for about eight queries.

![Figure 10.9 Template-based rankings order for different query type (a) TC, (b) ST, (c) PQ.](html/images/9781032942346_C010_009.jpg)

**Figure 10.9** Template-based rankings order for different query type (a) TC, (b) ST, (c) PQ.

The applied template-based prompt engineering result for test set are shown in [Table 10.2](#ch20.xhtml#t39). It can be observed in results that 48% times TB has received first rank, 18% times TB ranked second, and remaining 26% times TB ranked third in comparison to zero-shot and few-shot prompt engineering technique specifically for LPM generation.

**Table 10.2** Prepared lecture ranking results for template-based prompt engineering technique

| Query type | Total count in test dataset | Number of times TB was ranked first | Number of times TB was ranked second | Number of times TB was ranked third |
| --- | --- | --- | --- | --- |
| CQ | 2 | 2 | 0 | 0 |
| TC | 13 | 6 | 4 | 3 |
| ST | 25 | 13 | 3 | 8 |
| PQ | 9 | 3 | 2 | 1 |
| OCQ | 1 | 0 | 0 | 1 |

### 10.5.3.3 Human evaluation

During this phase, from the test dataset a query of each type, which is total of five queries, along with their respective LPM generated using the three prompting techniques, that are, TB, FS, and ZS are shared with professors as a survey form. The survey required the participants to define their preferences as first, second, and third for the LPM generated using different techniques according with respect to the queries. The prompting techniques with which a particular LPM is generated were not revealed to the participants, and their ability to give similar preferences were enabled. The results obtained depicted that the LPM generated using FS prompt technique was majorly the first preference of the participants, followed by TB and then ZS. The LPM generated using TB was majorly a second preference, and the one generated using ZS was majorly given the third preference as visualized in [Figure 10.10](#ch20.xhtml#f80). This result also throws light on the gap between the sense of judgement of a human and LLMs like Gemini Pro as content evaluator.

![Figure 10.10 Multibar graph visualizing the count of all the prompt techniques as first, second, and third preference by a human evaluator.](html/images/9781032942346_C010_010.jpg)

**Figure 10.10** Multibar graph visualizing the count of all the prompt techniques as first, second, and third preference by a human evaluator.

## 10.6 Conclusion

This study involved leveraging advanced natural language processing techniques to generate education content. By employing various prompting techniques like template-based prompting, zero-shot prompting, and few-shot prompting techniques on Chat-GPT-3.5, lecture preparation materials were generated on topics related DSA and OOPs fundamentals and finally the performance of each prompting technique was compared by implementing a three phased evaluation. By carrying evaluation in three phases, we discerned the nuances in structure and content quality among the generated materials. The first two phases of evaluations, that are rule-based (structural criteria) where in for more than 55% of the queries in test dataset, TB has score of 10 out of 10 and for the remaining ones a score of 9 out of 10 which depicts structural completeness and Gemini Pro with RAG (content criteria) where in for about 48 % queries, the LPM generated using TB prompt technique are ranked first depicting content completeness, highlight the efficacy of template-based prompting in consistently producing well-structured and informative lecture content compared to zero-shot and few-shot prompting techniques for majority of the queries, but according to the third phase, that is human evaluation, the material generated using template-based prompting is majorly a second preference. Further, for evaluating generated education content, leveraging Gemini emphasizes on its value as a content evaluator as well as revealing areas where there is a scope of improvement to match human level evaluation. In conclusion, this study contributes to the ongoing discussion about the role of AI in education by throwing light on how content can be generated in educational systems by leveraging AI.

## References

*   [1] Meißner, N., Speth, S., Kieslinger, J., & Becker, S. (2024). EvalQuiz–LLM-based automated generation of self-assessment quizzes in software engineering education. In Software Engineering im Unterricht der Hochschulen 2024 (pp. 53–64). Gesellschaft für Informatik eV.
*   [2] Spasić, A. J., & Janković, D. S. (2023, June). Using ChatGPT standard prompt engineering techniques in lecture preparation: role, instructions and seed-word prompts. In 2023 58th International Scientific Conference on Information, Communication and Energy Systems and Technologies (ICEST) (pp. 47–50). IEEE.
*   [3] Bonner, E., Lege, R., & Frazier, E. (2023). Large language model-based artificial intelligence in the language classroom: practical ideas for teaching. Teaching English with Technology, 23(1), 23–41.
*   [4] Kojima, T., Gu, S. S., Reid, M., Matsuo, Y., & Iwasawa, Y. (2022). Large language models are zero-shot reasoners. Advances in Neural Information Processing Systems, 35, 22199–22213.
*   [5] An, Y., Xue, H., Zhao, X., & Zhang, L. (2021, August). Conditional self-supervised learning for few-shot classification. In IJCAI (Vol. 8, pp. 2140–2146).
*   [6] Lou, R., & Yin, W. (2024, March). Toward zero-shot instruction following. In Proceedings of the 18th Conference of the European Chapter of the Association for Computational Linguistics: Student Research Workshop (pp. 50–60).
*   [7] Wei, J., Bosma, M., Zhao, V. Y., Guu, K., Yu, A. W., Lester, B., ... & Le, Q. V. (2021). Finetuned language models are zero-shot learners. *arXiv preprint arXiv:2109.01652*
*   [8] Clavié, B., Ciceu, A., Naylor, F., Soulié, G., & Brightwell, T. (2023, June). Large language models in the workplace: A case study on prompt engineering for job type classification. In International Conference on Applications of Natural Language to Information Systems (pp. 3–17). Cham: Springer Nature Switzerland.
*   [9] Arawjo, I., Vaithilingam, P., Wattenberg, M., & Glassman, E. (2023, October). ChainForge: An open-source visual programming environment for prompt engineering. In Adjunct Proceedings of the 36th Annual ACM Symposium on User Interface Software and Technology (pp. 1–3).
*   [10] Sridhar, P., Doyle, A., Agarwal, A., Bogart, C., Savelka, J., & Sakr, M. (2023). Harnessing llms in curricular design: Using GPT-4 to support authoring of learning objectives. *arXiv preprint arXiv:2306.17459*.
*   [11] Leiker, D., Finnigan, S., Gyllen, A. R., & Cukurova, M. (2023). Prototyping the use of large language models (LLMs) for adult learning content creation at scale. *arXiv preprint arXiv:2306.01815*
