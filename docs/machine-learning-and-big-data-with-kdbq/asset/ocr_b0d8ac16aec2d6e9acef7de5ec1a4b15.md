# Processing Information

sentence and the second one is the idf evaluation for the sentence. The function return tf-idf for every word in the sentence:

```
quantQ.infth.tfidfSentence:{sentence;idf}
// sentence sentence of words to be analysed
// idf -- idf calculated for the corpus
// word frequency dictionary
wordFrequency:quantQ.infth.wordFrequency[enlist sentence];
// tf-idf for every word
:t!(value wordFrequency)!=enlist idf each: key wordFrequency);
;
```

Let us calculate tf-idf for first sentence of the corpus:

```
.quantQ.infth.tfidfSentence{first davinci};quantQ.infth.idf[davinci]}
("there";"is";"no";"human";"experience";"that";"can";"be";"termed";"true"\cience";"unless";"it";"mathematically";"demonstrated")!2.159484
0.4792773 1.84711 3.614771 2.921624 0.965618 4.52969 2.332465
4.462069 3.075775 3.768922 7.985077 5.560682
```

The outcome is a dictionary, for every word of the sentence is a corresponding numerical value, tf-idf. Let us illustrate the value for the two words. The first is one very common:

```
tfidf[enlist "is"]
```

enlist and the second one is rather rare:

```
tfidf[enlist "mathematically"]
```

enlist 0.560682

The values of tf-idf reveal the intuitive notion of being rare; the latter word has much higher score compared to the first. The value itself, however, does not give meaning. We slightly turn the problem and reformulate it as follows. We are provided with a word to search for and we find a sentence which is the most relevant in terms of tf-idf metric. for that we enter the entire corpus and the word we are searching for. It returns the sentence from the corpus which has a given word the highest tf-idf:

```
quantQ.infth.findBestSentence:{corpus;word}
// corpus corpus cleaned text
// word -- word to be searched for
// subset of corpus with given word
corpusSubset:where {first x in "vs" y[word]; each corpus;
// return the sentence with the maximum tf-idf for a given word, if more
then one, select randomly
: first?corpusSubset where max[t]=t:{first x[y]][word] each
.quantQ.infth.tfidfSentence:{quantQ.infth.idf[corpus]} each
corpusSubset;
```

```
;
```