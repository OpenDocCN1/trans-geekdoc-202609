# 528

# MACHINE LEARNING

We chose three sentences we hope will give us a useful metric:

daVinciSentenceAnalyticsMeasure where {0.5x["AVERAGE\]} each

daVinciSentenceAnalyticsMeasure

```
(("syllogism";"to";"speak";"doubtfully";"AVERAGE";"MAX")! 0.004 0.1666667
- 0.5426667 1
(\sophism";"to";"speak";"confused";"falsehood";"for";"truth";"AVERAGE";
"MAX")! 0.01666667 1 0.03225806 0.333333 0.5051971 1;
("AVERAGE";"MAX")! 1 1f
```

The three sentences have unique content. The last is actually the result of our filtering method. The selected sentences are two. The dictionary above does not provide the full sentence, it is one decomposed into individual words. We recover the sentences:

daVinci where {0.5x["AVERAGE\]} each daVinciSentenceAnalyticsMeasure

"syllogism to speak doubtfully";sophism to speak confused forshadow
- truth";"

The two sentences are rather unique. They sound like quotes worth remembering. We readers perform their own analysis of quotes by selected authors and establish a statistical validity to the hypothesis that quotes are likely to increase average measure Ω to an average text sample.

# 27.1.3 tf-idf

In this section, we elaborate on the measure for word frequency and introduce properly defined metrics used in the information for information retrieval. The metric is called term frequency-inverse document frequency, or tf-idf. It is based on a similar foundation as the previous metric; it considers a document as a bag of words where the order of words does not play any role. It assigns importance to every word and assesses the document based on the importance of individuals.

Let stay with the notion of a bag of words. This means that "John killed Mary" and "Mary killed John" are considered identical even though they carry a different meaning. In the end, a different person survived and a one was killed. This immediately brings limitations to the provided method. If we would like to include the meaning of sentences, we would need to employ much more sophisticated models like deep neural networks.

The importance of a word within the document is composed of two components. First, it is proportional to the frequency of a word within the document. If we write a text about polar bears, the term "polar bear" should frequently appear across the text. This will make the text relevant to the polar bear. On the other hand, the frequency itself has to be taken into context: How frequently is "polar bear" used throughout the entire corpus of all documents? If this is a common and present in many documents, we require a few occurrences within a document to consider it relevant. On the other