+   - A three-fold process to analyze KGQA datasets, i.e., Qualitative Analysis, Translations Review, and Quantitative Analysis. We apply this process to analyze the quality of the Spanish language in the QALD-9 dataset.
+   - A publicly available KGQA dataset with accurate Spanish translations. We integrate our work with QALD-9-plus to increase its adoption.
+   - An evaluation of our QALD-9-ES dataset against KGQA systems using the GERBIL QA framework and showing improvements in most of the metrics compared to its predecessor.

This article is organized into the following sections: (2) previous work, (3) dataset development and description, (4) baseline evaluation, and (5) conclusions.

# 2. Previous Work

For the elaboration of this work, we reviewed KGQA datasets and related tools to develop and compare KGQA datasets. Table 1 summarizes each dataset’s information showing the lack of accurate Spanish translations.

Table 1. For existing KGQA datasets, we show the number of unique questions and available languages. QALD-9 is the only dataset available for the Spanish language, but it suffers from quality issues.

| Dataset | Available for | No. of questions | Available languages |
|---|---|---|---|
| QALD-9 | DBpedia | 558 | en, it, de, ru, fr, pt, hi.IN,fa, ro, es, nl |
| QALD-9-plus⁹ | DBpedia | 558 | en, lt, de, ru, fr, uk, be, ba, hy |
| QALD-9-plus⁹ | Wikidata |  |  |
| rewordQALD9 | DBpedia | 551 | en, it |
| LC-QUAD | DBpedia | 5000 | en |
| LC-QUAD 2.0 | DBpedia | 30000 | en |
| LC-QUAD 2.0 | Wikidata |  |  |

# 2.1. KGQA Datasets

# 2.1.1. QALD-9, the 9th Challenge on Question Answering over Linked Data (QALD-9):

QALD is a challenge with eleven years of history with the objective of providing up-to-date benchmarks for assessing and comparing state-of-the-art KGQA systems¹⁰. QALD-9 [2] is the 9th edition of the QALD challenge. This dataset provides 408 training questions and 150 test questions for DBpedia, available in 11 different languages, making QALD-9 one of the few multilingual KGQA benchmarks available and the only one we are aware of that counts with Spanish translations. In the 9th version of QALD, the questions were compiled and curated from previous versions and are accompanied by manually specified SPARQL queries and answers. The community reported multiple issues with the translations in the QALD-9 dataset; they were reported to be incorrect and of poor quality for different languages [3]. After reviewing the Spanish translations, we