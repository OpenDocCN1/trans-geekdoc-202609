
Document classification is a generalization of sentiment analysis and typically involves more than three possible flags per article:

[https://towardsdatascience.com/natural-language-processing-pipeline-decoded-f97a4da5dbb7](https://towardsdatascience.com/natural-language-processing-pipeline-decoded-f97a4da5dbb7%20)

In addition to the preceding list of sample applications, there are many use cases for NLP, some of which are listed here:

Question answering

Filter email messages

Detect fake news

Improve clinical documentation

Automatic text summarization

Sentiment analysis and semantics

Machine translation and generation

Personalized marketing

Some of the use cases in the preceding list (such as sentiment analysis) are discussed in later chapters.

### NLU and NLG

NLU is an acronym for natural language understanding and although you might not see numerous books about this topic, it’s a very significant subset of NLP. In very high-level terms, NLU attempts to understand human language in determining the context of a text string or document. NLU addresses various NLP tasks, such as sentiment analysis and topic classification. Another extremely important NLU task is called relation extraction, which is the task of extracting semantic relations that may exist in a text string. Moreover, the sources of input text can be from chatbots, documents, blog posts, and so forth.

As a simple example, consider this block of text and notice the different meanings of the pronouns “he” and “them”:

"John lived in France and he attended an International school. Mary lived in Germany and she also attended an International school. Dave lived in London and met both of them in Paris. One of these days, when he has some free time, they will meet up again. Steve met all of them on New Year's Eve."

Although the preceding paragraph is easy for humans to understand, it poses some challenges for NLU, such as determining the correct answers to the following questions:

1. Who does the first occurrence of “he” refer to?

2. Who does the second occurrence of “he” refer to? Is it ambiguous?

3. Who does the first occurrence of “them” refer to?

4. Who does the second occurrence of “them” refer to? Is it ambiguous?

As you undoubtedly know, one of the challenges of human language involves the correct interpretation of words that are used ambiguously in a sentence, and such ambiguity can be classified into several types. For example, lexical ambiguity occurs when a word has multiple meanings, which can change the meaning of a sentence that contains that word. One approach to handling this type of ambiguity involves POS (Parts Of Speech) techniques, which is illustrated in the chapter with NLTK content.

Another type of ambiguity is syntactical ambiguity is also called grammatically ambiguity, which occurs when a sequence of words (instead of a single word) has multiple meanings.

Yet another type of ambiguity is referential ambiguity that can occur when a noun in one location is referenced elsewhere via a pronoun, and the reference is not completely clear.

Another very important subset of NLP is natural language generation (NLG), which is the process of producing meaningful phrases and sentences in the form of natural language from some internal representation. One impressive example of NLG is the ability of GPT-3 (discussed in Chapter [11](#ch11.xhtml)) to generate meaningful responses to a wide variety of questions.

NLP can be used to analyze speech (not discussed in this book), words, and the structure of sentences. As such, we need to become acquainted with text classification, which is the topic of the next section.

### What is Text Classification?

Text classification is a supervised approach for determining the category or class of a text-based corpus, which can be in the form of a blog post, the contents of a book, the contents of a Web page, and so forth. The possible classes are known in advance, and they do not change; the classes are often (but not always) mutually exclusive.

Text classification involves examining text to determine the nature of its content, such as:

topic labeling (the major topics of a document)

the sentiment of the text (positive or negative)

the human language of the text

categorizing products on websites

whether or not it’s spam

However, most text-based data is unstructured, which complicates the task of analyzing text-based documents. From a business perspective, machine learning text classification algorithms are valuable when they structure and analyze text in a cost-effective manner, thereby expediting business processes and decision-making processes.

As you can probably surmise, text classification is important for customer service, which can involve routing customer requests based on the (human) language of the text, determining if it’s a request for assistance (products or services), detecting issues with products, and so forth.

Note that some older text classification algorithms are based on bag of words (BoW) that only determines word frequency in documents. The BoW algorithm is explained in Chapter [5](#ch05.xhtml), along with code samples for BoW in Chapter [6](#ch06.xhtml).

One more thing: text summarization is related to text classification, and it’s described in Chapter [9](#ch09.xhtml) in the section that discusses recommender system.

### Information Extraction and Retrieval

The purpose of information extraction is to automatically extract structured information from one or more sources, which could contain unstructured data in documents. For example, an article might provide details of an IPO of a successful start-up, or the acquisition of a larger company by an even larger company. Information extraction would involve generating a summary sentence from the contents of the article. In a larger context, information extraction is related to topic modeling (i.e., finding the main topics in a document) that is discussed toward the end of this chapter.

Information extraction also requires information retrieval, where the latter involves methods for indexing and classifying large documents. Information extraction involves various subtasks, such as identifying named entities (i.e., nouns for people, places, and companies), automatically populating a template with information from an article, or extracting data from tables in a document.

As a simple example, suppose that a program regularly scrapes (retrieves) the contents of HTML pages to summarize their contents. One of the first tasks that must be performed is data cleaning, which in this case involves removing HTML tags, removing punctuation, converting text to lower case, and then splitting sentences into tokens (words). Fortunately, the BeautifulSoup Python library can easily perform each of the preceding tasks.

Another area of great interest in NLP is the proliferation of chatbots, which interact with users to provide information (directions, hours of operation, and so forth) or perform specific tasks (make reservations, book hotels, car rentals, and so forth).

### Word Sense Disambiguation

Up until several years ago, word sense disambiguation was an elusively difficult task because words can be overloaded (i.e., possess multiple meanings). A well-known NYT article describes one humorous misinterpretation in machine learning. The following sentence was translated into Russian and then translated from Russian into English:

The spirit is willing, but the flesh is weak

The result of the second translation is here:

the vodka is good, but the meat is rotten

Here is the link to the NYT article:

[https://www.nytimes.com/1983/04/28/business/technology-the-computer-as-translator.html](https://www.nytimes.com/1983/04/28/business/technology-the-computer-as-translator.html)

As another simple example of an overloaded word, consider the following four sentences:
