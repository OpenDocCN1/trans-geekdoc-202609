
-   [doc.vector](https://wiki.example.org/doc.vector): \[-1.39887929e-01 -1.95095055e-02  8.34191069e-02 -2.64628291e-01   2.40830615e-01  2.75315434e-01  2.51161046e-02  7.67326951e-02   8.21892098e-02  1.90768397e+00 -2.59143114e-01  1.49312809e-01  -6.83634281e-02 -1.11276604e-01 -1.17691800e-01 -2.02080399e-01  -7.09474012e-02  1.21521211e+00 -1.57256007e-01 -2.19138991e-02  // lines omitted for brevity   3.04495007e-01 -1.26671968e-02  6.86664060e-02 -1.62135810e-01  -6.57109767e-02  1.62497148e-01  4.26867157e-01  1.21716186e-01   8.21024999e-02  2.98182011e-01  5.26543036e-02  2.68678162e-02  -2.37585977e-01  1.15498960e-01 -1.25021964e-01 -1.34173691e-01   9.52331945e-02 -1.57274202e-01  9.77694020e-02  1.11879949e-02\]   tokens: wine beer soda   \=> token1.text, token2.text, token1.similarity(token2): wine wine 1.0 \=> token1.text, token2.text, token1.similarity(token2): wine beer 0.6600621 \=> token1.text, token2.text, token1.similarity(token2): wine soda 0.4345365 \=> token1.text, token2.text, token1.similarity(token2): beer wine 0.6600621 \=> token1.text, token2.text, token1.similarity(token2): beer beer 1.0 \=> token1.text, token2.text, token1.similarity(token2): beer soda 0.5788868 \=> token1.text, token2.text, token1.similarity(token2): soda wine 0.4345365 \=> token1.text, token2.text, token1.similarity(token2): soda beer 0.5788868 \=> token1.text, token2.text, token1.similarity(token2): soda soda 1.0   \=> token.text, token.has\_vector, token.vector\_norm, token.is\_oov: apple True 7.1346846 False \=> token.text, token.has\_vector, token.vector\_norm, token.is\_oov: banana True 6.700014 False \=> token.text, token.has\_vector, token.vector\_norm, token.is\_oov: orange True 6.5420218 False   \=> \[w\[0\].text for w in calc\_similarities\[:10\]\]: \['queen', 'man', 'he', 'let', 'nothin', 'lovin', 'nuff', 'dare', 'doin', 'all'\]

## **The scispaCy Library (Optional)**

The scispaCy Python library for NLP is based on spaCy, and it’s used for processing biomedical text. This library performs common NLP tasks, such as NER, POS tagging, dependency parsing, and sentence segmentation.

The scispaCy library contains two primary packages that contain models: en_core_sci_sm (a smaller vocabulary without word vectors) and en_core_sci_md (a larger vocabulary with word vectors).

In particular, NER tasks play a key role in various types of biomedical data in datasets of differing sizes and number of entities (and their types) for different domains, such as cancer genetics, disease-drug interactions, pathway analysis and trial population extraction. The accuracy of scispaCy NER models is comparable to a decent number of other existing models. If this Python library interests you, more information regarding scispaCy is here:

*[https://arxiv.org/pdf/1902.07669.pdf](https://arxiv.org/pdf/1902.07669.pdf)*

## **Summary**

This chapter showed you how to perform data cleaning tasks that involve regular expressions. Then you learned about BoW, along with an explanation of word embeddings. In addition, you saw how to use BeautifulSoup, which is a Python module for scraping HTML Web pages.

Then you learned about Scrapy, which is a Python-based library that provides web scraping functionality and various other APIs. In addition, you were introduced to spaCy, which is a Python-based library for NLP, along with Python code samples that show you various features of spaCy.

You also learned about word embeddings and the fact that they provide context for words, which can yield more powerful models. Then you saw a Python code sample that involved word2vec, which is a Python-based library (discussed in Chapter [4](#ch04.xhtml)) for NLP-related tasks that involve unstructured data as well as labeled data.

# CHAPTER 6

# ALGORITHMS AND TOOLKITS (II)

This chapter contains Python code samples that illustrate various NLP concepts that you learned in the previous two chapters. Since those chapters contain sufficient NLP-related theory, this chapter focuses almost exclusively on code samples. The majority of the code samples in this chapter involve NLTK (Natural Language Toolkit), along with several code samples that are based on gensim.

The first section (approximately two-thirds of this chapter) introduces NLTK and code samples that use NLTK with BoW, stemmers, and lemmatization. You will also see some examples of NLTK with Wordnet, lxml, XPath (not discussed in this book), n-grams, and skip-grams.

The second section introduces GloVe and gensim, which are very useful NLP Python libraries, along with some code samples.

## **What is NLTK?**

Natural Language Toolkit (NLTK)is an open source Python library specifically for NLP-related tasks. Although NLTK does not provide SOTA (state-of-the-art) performance, it does provide a variety of solutions to many NLP tasks. This library was developed in 2002, and its home page is here:

*www.nltk.org*

NLTK provides support for many NLP-related tasks, such as stemmers, tokenization (words, sentences, and documents), lemmatization, chunking, and grammars. In particular, NLTK supports the SnowballStemmers that creates non-English stemmers for more than 10 languages: Danish, Dutch, English, French, German, Hungarian, Italian, Norwegian, Portuguese, Romanian, Russian, Spanish, and Swedish.

NLTK also supports n-grams, skip-grams, BoW, word2vec, parts of speech (POS), and named entity recognition (NER). In fact, NLTK enables you to define your own custom grammars and then parse sentences to determine if their structure conforms to a custom grammar.

NLTK is well-suited for various NLP tasks, such as recommendation systems and sentiment analysis, both of which are discussed in more detail in Chapter [9](#ch09.xhtml). NLTK also supports Wordnet, which enables you to find words (via Sysnet) and their homonyms and synonyms.

## **NLTK and BoW**

[Listing 6.1](#ch06.xhtml#list6.1) displays the contents of ntk_bow.py that illustrates how to implement BoW in NLTK. Keep in mind that this code sample does involve regular expressions, also known as RegExs. If you are unfamiliar with RegExs, you can either “comment out” the two code snippets that involve regular expressions, or you can read the appendix that discusses this topic.

***LISTING 6.1: nltk_bow.py***

import nltk import numpy as np import re   text = 'the SF weather is hot and the LA weather is hotter' ds = nltk.sent_tokenize(text)   \# clean the words in the dataset: for i in range(len(ds)):   ds[i] = ds[i].lower()   ds[i] = re.sub(r'\\W', ' ', ds[i])   ds[i] = re.sub(r'\\s+', ' ', ds[i])   print("cleaned dataset:") print(ds) print()   \# construct BoW model: word2count = {} for data in ds:   words = nltk.word_tokenize(data)   for word in words:     if word not in word2count.keys():       word2count[word] = 1   else:       word2count[word] += 1   \# display word/frequency counts: for word, freq in word2count.items():   print(f'word: {word:8} frequency: {freq:3d}') 

[Listing 6.1](#ch06.xhtml#list6.1) initializes the variable text with a string and then initializes the variable ds with the tokens of text. Next, a for loop iterates through the tokens and converts them to lowercase, removes all nonalphabetic characters, and replaces multiple whitespaces with a single whitespace.

Next, the cleaned data is displayed, followed by a loop that constructs a BoW model based on the tokens in the variable ds. Note that multiple occurrences of a token are taken into account when populating the dictionary word2count. The final portion of [Listing 6.1](#ch06.xhtml#list6.1) displays each word and its frequency. Launch the code in [Listing 6.1](#ch06.xhtml#list6.1) and you will see the following output:

