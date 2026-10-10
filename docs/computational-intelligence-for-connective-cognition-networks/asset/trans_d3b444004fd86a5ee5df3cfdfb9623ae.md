

![Figure 10.8 Generated lecture ranking comparison of template-based (TB), few shot (FS), and zero shot (ZS) using Gemini Pro With RAG.](html/images/9781032942346_C010_008.jpg)

**Figure 10.8** 使用带 RAG 的 Gemini Pro 生成的基于模板 (TB)、少样本 (FS) 和零样本 (ZS) 的讲座排名比较。

[Figure 10.9](#ch20.xhtml#f79) 通过绘制 TB 获得第 1、2、3 名的次数，展示了 TB 在每种查询类型中的排名。可以观察到，对于每种查询类型，其获得第 1 名的次数多于第 2 名或第 3 名，对于 ST 查询，其获得第 3 名的次数约为 8 个查询。

![Figure 10.9 Template-based rankings order for different query type (a) TC, (b) ST, (c) PQ.](html/images/9781032942346_C010_009.jpg)

**Figure 10.9** 不同查询类型的基于模板的排名顺序 (a) TC，(b) ST，(c) PQ。

应用于测试集的基于模板的提示工程结果如 [Table 10.2](#ch20.xhtml#t39) 所示。从结果中可以观察到，与零样本和少样本提示工程技术相比，特别是针对 LPM 生成，TB 有 48% 的时间获得第 1 名，18% 的时间排名第 2，剩余 26% 的时间排名第 3。

**Table 10.2** 基于模板的提示工程技术的讲座排名结果

| Query type | Total count in test dataset | Number of times TB was ranked first | Number of times TB was ranked second | Number of times TB was ranked third |
| --- | --- | --- | --- | --- |
| CQ | 2 | 2 | 0 | 0 |
| TC | 13 | 6 | 4 | 3 |
| ST | 25 | 13 | 3 | 8 |
| PQ | 9 | 3 | 2 | 1 |
| OCQ | 1 | 0 | 0 | 1 |

### 10.5.3.3 人工评估

在此阶段，从测试数据集中选取每种类型的一个查询，共五个查询，连同使用三种提示技术（即 TB、FS 和 ZS）生成的各自 LPM，以调查表的形式分享给教授们。调查要求参与者根据查询，将使用不同技术生成的 LPM 的偏好定义为第一、第二和第三。生成特定 LPM 所用的提示技术未向参与者透露，且保留了他们给出相似偏好的能力。获得的结果表明，使用 FS 提示技术生成的 LPM 主要是参与者的首选，其次是 TB，然后是 ZS，如 [Figure 10.10](#ch20.xhtml#f80) 所示。使用 TB 生成的 LPM 主要是第二选择，而使用 ZS 生成的 LPM 主要被给予第三选择。这一结果也揭示了人类的判断力与 Gemini Pro 等作为内容评估者的 LLMs 之间的差距。

![Figure 10.10 Multibar graph visualizing the count of all the prompt techniques as first, second, and third preference by a human evaluator.](html/images/9781032942346_C010_010.jpg)

**Figure 10.10** 多柱图展示了人工评估者将所有提示技术作为第一、第二和第三偏好的计数。

## 10.6 结论

本研究涉及利用先进的自然语言处理技术生成教育内容。通过在 Chat-GPT-3.5 上采用基于模板的提示、零样本提示和少样本提示等各种提示技术，生成了与 DSA 和 OOP 基础相关的讲座准备材料，最后通过实施三阶段评估来比较每种提示技术的性能。通过三阶段评估，我们辨别了生成材料在结构和内容质量方面的细微差别。前两个评估阶段，即基于规则的评估（结构标准），其中测试数据集中超过 55% 的查询 TB 得分为 10/10，其余查询得分为 9/10，这表明结构完整性；以及带 RAG 的 Gemini Pro（内容标准），其中约 48% 的查询使用 TB 提示技术生成的 LPM 排名第一，表明内容完整性，突显了基于模板的提示在持续生成结构良好且信息丰富的讲座内容方面的有效性，优于大多数查询的零样本和少样本提示技术，但根据第三阶段，即人工评估，使用基于模板的提示生成的材料主要是第二选择。此外，对于评估生成的教育内容，利用 Gemini 强调了其作为内容评估者的价值，同时也揭示了需要改进以达到人工评估水平的领域。总之，本研究通过阐明如何利用 AI 在教育系统中生成内容，为关于 AI 在教育中作用的持续讨论做出了贡献。

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

