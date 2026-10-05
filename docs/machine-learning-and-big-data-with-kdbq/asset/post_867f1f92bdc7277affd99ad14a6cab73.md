
# CHAPTER 27
# Processing Information

We have so far solely on numerical time series and devoted most of our time to analysing numbers. Recently, however, processing of non-numerical data, namely written text, has become an essential part of machine learning and data science. In this chapter, we introduce some concepts from the data processing field, which are motivated by how search engines assign importance to documents.

## 27.1 INFORMATION RETRIEVAL

The first method we review is from the information retrieval toolbox. The motivation is as follows. We have a set of basic building blocks, words, and a document composed of a subset of words. We want to assign a measure for the word how important it is for a given document. Since some words are more frequent than others, the natural frequency of words within the entire corpus of all has to be taken into account, and the measure has to be corrected for it.

Imagine we have a document, and we want to understand whether its content is relevant for a reader or not. The relevancy means that it is not just "another" permutation of words, but it contains unique words. Let us stress that we base our analysis on the uniqueness of words and not how they are structured within a sentence. Such an idea, if expressed using common words, cannot be captured with analytics we are building now and is beyond the aim of this book.

In this section, we first discuss the corpus we use for examples and two approaches for information retrieval: intuitive frequency counting and tf-idf method.

### 27.1.1 Corpus: Leonardo da Vinci

In order to illustrate the concept of information retrieval, we need a sample text. We will use a text by Leonardo da Vinci Thoughts on Art and Life, translated in 1906. We have accessed the text using Project Gutenberg; daV. We focus on the third section titled "Thoughts on Science". We exclude side notes and page numbers. The text is stored on the local drive in a text file.

We filter the text as follows. We read the text into memory:

```q
daVinci:"vs" sv read "C:\daVinciThoughtsOnArtAndLife_ChapterScience.txt"
```

Machine Learning and Big Data with kdb+/q, First Edition. Jan Novoty, Paul A. Bilikon, Ari Galios and Frédéric Delèze.
© 2020 Jan Novoty, Paul A. Bilikon, Ari Galios and Frédéric Delèze. Published 2020 by John Wiley & Sons, Ltd.

# MACHINE LEARNING

and explore the content (list of the output):

daVinci

> "There is no human experience that can be termed true science unless it can be mathematically demonstrated"; And if thou sayeth that the sciences which begin and end in the mind are true, this cannot be conceded, but must be denied for many reasons, and firstly because in such mental discourses experience is eliminated, and without experience there can be no certainty";

The sentences can contain symbols we do not understand. In addition, we convert everything lower case as the cases do not make a difference for us. We clean the text:

```q
daVinci:lower(x where not in ("\"\";\"!"))
```

Further, there are duplicate sentences within sentences; we remove them as:

We can explore the content of the corpus after we have performed the cleaning of the text:

daVinci

> "there is no human experience that can be termed true science unless it can be mathematically demonstrated";and if thou sayeth that the sciences which begin and end in the mind are true this cannot be conceded but must be denied for many reasons and firstly because in such mental discourses experience is eliminated and without experience there can be no certainty";

The sentences are now standardised and ready to be analysed in terms of word frequency.

Further, the notion of a document is played by a single sentence. The corpus is then the set of all sentences within the sample text specified above. This approach does not require dealing with excessively large data, which would not be suitable for the pedagogical purpose of the book (but reasonable in practical circumstances using q).

### 27.1.2 Frequency Counting

Our objective is to identify sentences – which play the role of documents – that carry the unique, informative content. Imagine we face a problem to choose a few sentences from the entire book (chapter in our case) which carry the most unique content. One possible way is to focus on sentences with different words. In addition, we extend the search question as follows. We are looking for a few sentences which contain a particular word or combination of words such that those sentences will tell us something unique about the word we search – yes, this corpus familiar; it is exactly what we want we “google” some term.

The sentences we are looking for are which contain unique content. The uniqueness of content within a sentence can be defined as “to contain as many words as possible”. This can be mathematically expressed as having in sentence frequently appearing words which are rare in the entire text.

For purpose, we define a frequency, or count of occurrence, for a given word, w, within the entire text as:

```math
$\Phi_{corpus}(w) = \sum_{w \in corpus} 1(w = w'),$ (27.1)
```

and a frequency for a given word within the sentence:

```math
$\Phi_{sentence}(w) = \sum_{w \in sentence} 1(w = w'),$ (27.2)
```

The measure of importance for a given word is then simply given as:

```math
$\Omega(w; corpus, sentence) = \frac{\Phi_{sentence}}{\Phi_{corpus}}$ (27.3)
```

where $\Omega$ is within (0, 1]. When the sentence contains all the instances of a given word within the entire corpus, the measure reaches 1 for an appearance of a common word will have value close to 0.

The measure $\Omega$ turns the sentence into a dictionary, where every different word in the sentence will have assigned numerical value. Let us implement the measure and illustrate it on our test sample. First, we define the global frequency for every word as:

```q
.quantQ.infth.wordFrequency:[corpus]
// corpus -- corpus with cleaned text
// count each group "vs" sv corpus;
```

and use the function for our data set:

```q
daVinciWordFrequency:=quantQ.infth.wordFrequency[daVinci];
```

The daVinciWordFrequency is a dictionary with word count throughout the corpus. In particular, the word “there” is present in the text 47 times, as can be seen:

```q
daVinciWordFrequency["there"]
```

47

The frequency within the sentence can be defined in the same way. We skip the step of creating the specific function for it and directly define a measure $\Omega$, which will proceed sentence sentence through the text and calculate the measure. Function wordMeasure takes two arguments: the document we want to analyse and the dictionary with word frequency, and returns the measure calculated sentence by

```q
quantQ.infth.wordMeasure:[document;wordFrequency]
// document -- text we want to analyse
// wordFrequency -- dictionary with corpus word frequency
// calculates word frequency measure
:distinct [[x;y] tmp:count each group] "vs x;(tmp y key tmp];
- wordFrequency:each document;
```

In the provided function, the document has to be a subset of the entire corpus.
Furthermore, the corpus was used to generate the dictionary. Recall when a dictionary is called with a non-defined key, and it returns the corresponding null value:

```q
daVinciWordfrequency["xxx"]
```

0N

We encourage readers to check the function that such the measure can cope with new words. We use a Bayesian framework to the procedure. It is important to keep in mind that when improperly done, the measure can exceed 1.0, which would be rather pathological.

Let us apply the measure on the daVinci sample:

```q
daVinciSentenceAnalytics: quantQ.infth.wordMeasure[daVinci;daVinciWordfrequency];
```

> The outcome is an array of dictionaries, where every element of the array corresponds to one sentence.

first daVinciSentenceAnalytics

```q
"there":"is":no":"human":"experience":"that":"can":"be":"termed":"true";"science":"unless":"it":"mathematically":"demonstrated"!;0.0212766
-0.00327869 0.0192307 0.1428571 0.0625 0.00671149 0.0540545
-0.0194072 0.0833333 0.0666667 0.1666667 0.00460825 1
```

The word "there" has a measure 0.0212766, while "mathematically" has the measure. The former word common across the corpus and thus does not have value for On the other hand, the latter word is unique and adds to the analysed sentence.

We add a function which adds two words to every sentence: one corresponding to the average measure per sentence, and one corresponding to the maximum value of a measure for a sentence. This will be a useful tool to process the process:

```q
quantQ.infth.worddaAnalytics:[documentMeasure]
// document analysed with defined measure
// sentence by sentence add and average measure x
:{tmpAvg: avg value x; tmpMax: max value x; (raze key x;enlist
- AVERAGE!;enlist "MAX")!
(raze value x;enlist tmpAvg;enlist tmpMax)) each documentMeasure;
```

;
