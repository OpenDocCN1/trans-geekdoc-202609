# # TABLE 5.1 Interpretation of BLEU Score

| BLEU Score | Interpretation |
| :--- | :--- |
| < 10 | Almost useless |
| 10–19 | Hard to get the gist |
| 20–29 | The gist is clear, but has significant grammatical errors |
| 30–40 | Understandable to good translations |
| 40–50 | High quality translations |
| 50–60 | Very high quality, adequate, and fluent translations |
| 60–70 | Quality often better than human |
| > 70 | Be cautious as it might mean overfitted models rather than extremely high quality |

Source: Adapted based on Google Developers (n.d.-b).

BLEU scores above 70 may indicate that the model is not measuring correctly or is overfitting. Table 5.1 is a summary based on Google AutoML Translation, a platform offered by Google which allows users to create and customize translation models.

# ## 5.4.2.2 Factors that impact the performance of BLEU

From the algorithm perspective, BLEU has innate disadvantages. First, the unit of comparison is the word. As discussed earlier, this metric attempts to capture allowable variation in word choice by comparing the candidate sentences against (multiple) reference translations. In order to overcome the problem of variation in word order, BLEU uses modified n-gram precision, as illustrated previously. This criterion makes this metric biased towards systems based upon statistical approaches, such as statistical and neural MT. For other types of systems, such as rule-based MT, simply using BLEU scores may vastly underestimate its actual quality. There are other examples showing that BLEU’s correlation with human judgments might have been overestimated and that BLEU is quite a crude measurement of translation quality (see Callison-Burch et al., 2006, pp. 253–255).

Second, as BLEU is very sensitive to the words that are present in the output of the machine translation engine, a key technology embedded in this metric involves the way that MT output is segmented into words. The performance of this technology varies across languages, which ultimately impacts the BLEU score. For example, with Chinese, Thai, and similar languages, the definition of ‘word’ is flexible or not completely clear, and there is no space separating word units like in English. The word segmentation employed in the software can have a substantial impact on the BLEU score and how to interpret it.

Thirdly, the number of references used in generating a BLEU score also plays a role. Generally speaking, when multiple references are used, the BLEU score tends to be higher, as Papineni et al. (2002) point out in an example: “on a test corpus