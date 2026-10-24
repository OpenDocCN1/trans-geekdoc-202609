However, if one more parameter of orientation is added, then some degree of closeness can be marked. This is achieved by dot product. The dot product is calculated as shown by Equation 1.9:

$$u \cdot v = \lVert u \rVert \lVert v \rVert \cos \theta$$

A higher orientation between vectors will produce a higher dot product.

# 6.4.3  COSINE SIMILARITY

The shortcoming of the dot product approach lies in its limitation to normalize, which is very well addressed in the cosine similarity method. Similarity between two-word vectors can be calculated by Equation 1.10:

$$\operatorname{Sim}(x,y)=\frac{x\cdot y}{\lVert x\rVert\lVert y\rVert}=\frac{\sum_{i=1}^{n}x_i y_i}{\sqrt{\sum_{i=1}^{n}x_i^2}\sqrt{\sum_{i=1}^{n}y_i^2}}$$

All methods are heavily used in NLP using Sklearn implementation.

# 6.5  SEMANTIC ANALYSIS

Semantic analysis in NLP deals with capturing the meaning of a natural language rather than only finding the similarity of words (Elnagar et al., 2021).

Semantic analysis is a deeper technique, as it takes into account the context, grammar roles and logical structuring of the sentences. It detects emotion and sarcasm in the text and extracts meaningful inferences while looking for the dictionary meaning of the words in the sentence.

If the meaning is similar, the words are classified as similar even if they have entirely different forms from the alphabet (i.e., spelling). Semantic analysis can be divided into two parts: lexical semantic analysis and compositional semantic analysis.

Lexical semantic analysis involves fetching the dictionary meaning of a word in a given text corpus. Therefore, lexical semantic analysis works at the word level. On the other hand, compositional semantic analysis is a step forward.

To understand a text, understanding each individual word is a pre-requisite, but because of ambiguities in the language, the context, scenario and sentiment must also be completely understood to understand a phrase, sentence or document.

Consider the following texts:

+   - Text 1: Bitcoin is not declared a legal tender.
+   - Text 2: Legal tender of the bridge is declared.