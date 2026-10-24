
## 6 Natural Language Processing
### *A Study of State of the Art*
Nipun Sharma and Swati Sharma

### 6.1 INTRODUCTION

Natural language processing (NLP) is an amalgamation of both technology and language. Technology encompasses computer science and artificial intelligence (AI). Language covers both text and speech.

Over the generations, humans have been interacting and communicating with each other through language. The exchange of ideas occurs through speech or written text. In contrast, machines are programmed using low-level or high-level scripting.

Human–computer interaction (HCI) has been in existence for the past few years. To make it more interactive and intuitive, the intersection between human-to-human interaction (HHI) and HCI has been explored and researched at lightning speed (Xu et al., 2022). The idea and concept that has come up as a result of this research is to make HCI more similar to HHI.

That said, the machines were required to be empowered to interact with humans. Moreover, they understand text or speech and make decisions. Simply put, making machines understand and process both speech and text is the foundation of NLP.

Natural language processing is a tool that enables a machine to comprehend text and language. It is used to apply machine learning algorithms to both text and speech. At this conjuncture, it can be stated that NLP is a subdomain of linguistics, computer science and AI.

One question that may arise is why, initially, we require machines to interpret human language. The answer is simple and straightforward. Owing to the large volume and abundance of data, it is practically impossible to interpret such a high volume with too many dimensions.

Here, machines trained to do so will be a boon to gain insights, read hidden patterns and make decisions. This is why and that is how NLP came into existence. Despite its popularity, implementing NLP is an extremely challenging task because most of the language-based data are unstructured and often ambiguous (Bose et al., 2021).

There are many components in speech, such as dialect, tone, accent and sarcasm, other than plain words (Sonbol et al., 2022). This requires computers to comprehensively understand not only the words but also the intentions, emotions and sentiments.

Natural language processing has two broad components, namely, natural language understanding or natural language interpretation and natural language generation. Both aspects of NLP are indicators of the two-way communication between humans and machines.

Systematic reviews have been conducted to analyze text processing and normalization, which facilitates real-time user-generated content from social media (Rogers et al., 2022).

The use of the most popular machine learning algorithms, such as support vector machine, Bayesian classifier and decision trees, along with neural networks is evolving (Otter et al., 2021; Sharma & Sharma, 2023).

### 6.2 TEXT PRE-PROCESSING AND VECTOR-BASED MODELS

Textual data must be pre-processed and vectorized to be able to feed to a machine learning algorithm. Because language data generated from text or speech are unstructured, pre-processing becomes a mandatory step toward NLP.

Vectorizing pre-processed data simply refers to converting text into numbers. Therefore, NLP requires both data pre-processing and vectorization, especially in complex domains, such as software development, and has secured its position in accurate and timely pre-processing of bug reports based on priority and category, which is otherwise very complex, exhaustive and requires many resources (Ahmed et al., 2021).

### 6.3 TEXT PRE-PROCESSING TECHNIQUES

Text pre-processing refers to filtering the text corpus such that only relevant features are retained and the clutter is discarded. To achieve these objectives, common pre-processing techniques, such as stop words, stemming, part-of-speech tagging and tokenization, are used (Matcovschi, 2014).

In a natural language, every word has an essence or context. At the same time, some words are neutral, such as demonstratives, prepositions and articles. These words have little or no context and can be ignored. Such words are called stop words in NLP (Pecar et al., 2020).

The Natural Language Toolkit has its own library of stop words. Stemming refers to the generation of a base word from its variations. The stem or root is the part to which inflectional affixes (-ed, -ize, -d and -s) are added. The stem of a word is created by removing its prefix or suffix. Therefore, stemming a word may not necessarily result in actual words.

![](img/66ecdb8eb8654ae1c99705e55a45a836_121_0.png)

FIGURE 6.1 Stemming and Lemmatization.

Tokenization is another pre-processing technique that breaks text into smaller units called tokens. Depending on the use case, a token can be an alphabet, a word, a phrase or even a sentence. Text vectorization is a fundamental process in NLP.

As none of the machine learning algorithms understands text and, ironically, all the raw data for NLP are mostly text, it becomes an obligation to transform the raw data.

Fortunately, there are techniques available for this purpose. These techniques, if considered closely, are based on basic descriptive statistics and mathematics.

#### 6.3.1 TERM FREQUENCY–INVERSE DOCUMENT FREQUENCY

Term frequency–inverse document frequency (TF-IDF) is a text vectorization technique that has gained traction and popularity in the domain of NLP because it is a simple and basic technique.

Segregating the acronym into two parts, TF refers to the frequency of a term in a particular document, and IDF is precisely a weight assigned to a term.

Term frequency is an indicator of the importance and relevance of a specific term in a specific document. It is denoted as a matrix with rows equal to the number of documents, also referred to as instances or sample sets.

All the unique terms in the documents comprising the columns of the TF matrix (Jayasurya et al., 2022) demonstrate that TF-IDF-based models outperform the models based on count vectorizers for NLP applications.

#### 6.3.2 TERM FREQUENCY MATRIX

Document frequency (DF) gives the number of documents for which a particular term exists. It is an indicator of how common or how rare a particular term is. Inverse document frequency is expressed by the mathematical formula shown in Equation 1.1.

$$\mathrm{IDF}=\log(n/\mathrm{DF}) \tag{1.1}$$

Finally, TF-IDF, as the name suggests, is a straightforward matrix multiplication. To obtain the final TF-IDF score ($W$), the TF matrix is multiplied by the IDF, as shown in Equation 1.2.

$$W=\mathrm{TF}*\mathrm{IDF} \tag{1.2}$$

The basic idea of this approach is to assign a higher weight to the most uncommon word or term and a lower weight to the most common term. Words with higher weight scores are deemed to be more significant.

As an illustration of TF-IDF, consider three documents consisting of the following text:

- D1: I live in Bangalore.
- D2: Bangalore has pleasant weather.
- D3: I love the weather in Bangalore.

The TF matrix for the given set of documents is created, as shown in Table 6.1.

**TABLE 6.1**  
**TF Matrix.**

|  | I | live | in | Bangalore | has | pleasant | weather | love | the | of |
|:---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| D1 | 1 | 1 | 1 | 1 | 0 | 0 | 0 | 0 | 0 | 0 |
| D2 | 0 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | 0 | 0 |
| D3 | 1 | 0 | 0 | 1 | 0 | 0 | 1 | 1 | 1 | 1 |

In the next step, DF and IDF are calculated, as shown in Table 6.2.

**TABLE 6.2**  
**DF and IDF Matrix.**

|  | I | live | in | Bangalore | has | pleasant | weather | love | the | of |
|:---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| DF | 2 | 1 | 1 | 3 | 1 | 1 | 2 | 1 | 1 | 1 |
| IDF | 0.176 | 0.477 | 0.477 | 0 | 0.477 | 0.477 | 0.176 | 0.477 | 0.477 | 0.477 |

Finally, by multiplying the TF matrix with the IDF, the TF-IDF score was obtained, as shown in Table 6.3.

The combination of count vectorizer and TF-IDF has led to some interesting applications, such as gender identification from names pertaining to a regional language (Saha et al., 2021; Jayasurya et al., 2022).
