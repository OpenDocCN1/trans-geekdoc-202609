
that is taken may be contingent on elements of the application domain and/or the structure of the dataset.

### Question 9: How do you interpret the TF-IDF scores for terms in a document?

Answer: The TF-IDF score of a term is defined within the constraints of a document and ranges from 0 to 1, and it represents the term’s importance or relevance in the given document compared with the other documents. Here is an interpretation:

Starting with, the TF-IDF score is a combination of TF and IDF, the two working in a multiplication manner. It is done locally within the specific document as well as globally over the whole corpus of documents. A higher score for a specific term results from its higher frequency within the given document and at the same time resulting from the lower frequency of that term across the whole corpus or collection of documents.

In interpretation:

- Higher the value of TF-IDF, the term is considered to be more important or relevant to the given document and may hold significant topics or subject areas.
- On the other hand, a low TF-IDF score means that the term is frequently used in the document or, generally, in the corpus, and for that reason, it may not effectively help discriminate between documents.

In general, if we recall that the goal of TF-IDF scores is to specify terms that are more relevant to individual documents as compared to a large number of documents available in a given set.

## Bag of words model

### Question 1: How does the BoW model represent text data?

BoW model is an approach used in the transformation of documents into numerical vectors that depict the text data. Every vector is a document, and the degree of the dimension in the vector is the occurrence of the word in the vocabulary. The value placed by each dimension represents the relative frequency or the total occurrence of the particular word in the document. In contrast with the syntactic model, this model does not take into consideration word order or grammar of sentences but only the presence of words and their frequencies. Hence, it offers a rather efficient method for classifying and clustering building blocks of text documents—the words.

### Question 2: What are the steps involved in creating a BoW representation?

Creating a BoW representation involves the following steps:

- **Tokenization**: Tokenization where the text should be divided into fine granularities of words or tokens.
- **Lowercasing**: Consider the variations of the same words to be equal and use the lowercase to convert all the words of the given data.
- **Building the vocabulary**: There should be a list of different words extracted from the periodically tokenized text.
- **Counting word occurrences**: Make count of the number of occurrences of each of the words in the vocabulary in the text.
- **Vectorization**: Based on the BoW model, express the text as the numerical vectors, each of which expresses the count of each word in the vocabulary.
- **Normalization (Optional)**: Preprocessing vectors should be scaled with respect to differences in document length or relative importance of words, normally dividing by the total number of words or using TF-IDF.

These steps lead to the so called BoW model, where each document is modelled as a sparse vector of word counts or frequencies, disregarding the grammatical structure and position of the words but taking into account whether certain words are either present in the document at all.

### Question 3: What is the importance of tokenization in the BoW model?

**Answer**: Tokenization is crucial in the BoW model for several reasons:

- **Word separation**: Like any other language model, tokenization fragments the raw text into individual words or tokens for further analysis.

These counts or frequencies should then be assigned to related positions within the vector.

- **Vectorization:**
  - Documents are now in a fixed dimensional space where each dimension is a particular word in the known vocabulary.
  - The values in the vector represent the occurrence of a particular word in the document or their importance depending on the function in use.
- **Normalization (Optional):**
  - Standardises the vectors if they are of different sizes, depending on the number of documents.
- **Finalization:**
  - It can be used in the input data for machine learning algorithms for all tasks like classification or clustering, etc.

It turns raw text data into a form that can fit into an equation and is easier to be modelled by machine learning algorithms for text-based data.

### Question 5: What are the common techniques for representing the frequency of words in the BoW model?

Answer: In the BoW model, common techniques for representing the frequency of words include the following:

- **Raw frequency**: Tells the frequency at which a word occurs in a document, which refers to an inventory of the document.
- **Binary**: These are represented in the binary where a word either is in a document (marked 1) or is not in a document (marked 0).
- **TF**: Calculates the TF of a word in a document as the number of times the word appears in that document divided by the total number of words in that document.
- **TF-IDF**: Acknowledges the significance of a word in a document in relation to its distribution across all the documents in the corpus; resultant of TF and inverse document frequency.

These techniques help the BoW model in interpreting the frequency of the words in any of the following aspects, giving different dimensions in the documents as well as in the total corpus.

### Question 6: How does the BoW model handle the order of words in a text?

The BoW model does not incorporate the position of words in a text in one of its components. It reads each document as a vocabulary of unordered words and then generates a number from those given the frequency of each word. This means that the BoW model fails to capture the order of the words in the document where in reality it should. Consequently, the kind of relations between words it produces do not comprehend possible syntactic and semantic relations that exist due to words’ locations in the text. Instead of that, it concerns particular terms within a document, and whether and how often they appear in it.

### Question 7: What are the limitations of the BoW model?

The BoW model has the following limitations:

- **Loss of word order**: Using simple word level vectors, BoW discards order of words within documents and, thus, the important order of text within documents is lost.

- **Structure:**
  - **Rows**: Capture documents in the corpus as prominent individuals.
  - **Columns**: In this type, terms come as words or tokens from the entire vocabulary of the document.
- **Entries:**
  - **Raw frequency**: Tells the word frequency distribution of terms in a document.
  - **Binary**: Binary form; 1 means the term exists in that document, while 0 means the term does not exist in the document.
  - **Weighted**: An organization may also scale frequency depending on the relevance of terms in a document, such as with the use of TF-IDF.

The term-document matrix is crucial for performing all forms of text analytics as it brings the text data into the form that is required for input to most machine learning algorithms.

### Question 9: How does the BoW model handle OOV words?

**Answer**: The BoW model handles OOV words in the following ways:

- **Ignore OOV words**: Some of these are omissions of words in text processing based on the contextual vocabulary given in advance.
- **Use a special token**: Introduce a special token like <UNK> to treat OOV words in a uniform manner and replace OOV words with this token, which is also in the vocabulary.
