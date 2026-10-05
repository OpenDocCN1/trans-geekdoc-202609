
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
// then one, select randomly
: first?corpusSubset where max[t]=t:{first x[y]][word] each
.quantQ.infth.tfidfSentence:{quantQ.infth.idf[corpus]} each
corpusSubset;
```

```
;
```

# 532 MACHINE LEARNING

Let us illustrate it on the following search:

```
.quantQ.infth.findBestSentence[daVinci;"there"]
```

- there can be no voice where there is no motion or percussion of the air
- there can be no percussion of the air where there is no instrument
- there is no such thing as an immaterial interest can be found
- being so a spirit can have neither voice nor shape nor force and if
- it assumes a shape it can penetrate nor enter where the
- issues are closed

The sentence is found with a large number of occurrences of "there". The sentence does not have much to find out more about the word itself. Since the test corpus is about science, we try to search for that word:

```
.quantQ.infth.findBestSentence[daVinci;"science"]
```

- science is that discourse of the mind which derives its origin from
ultimate principles beyond which nothing in nature can be found
forms a part of that science as in the continued quantity that
is to say the science of geometry which starting from the surfaces-of bodies has its origin in the line which is the end of the
superficies and are not satisfied by this because we know that
t line terminates in the point and the point is that which is the
least of things

Eureka! The sentence seems to explain the meaning of the word science. This is rather lucky, or a consequence of the fact that philosophers tend to construct long sentences which carry the compound message. In modern stylistics, the sentence would be cut out into pieces, and this would not work. We would have to use at least a paragraph instead of a sentence to achieve the same outcome.

Finally, we check the behaviour of the function for words which are not in the corpus. Da Vinci's description of a computer from the provided text reads:

```
.quantQ.infth.findBestSentence[daVinci;"computer"]
```

()

There is no output of our search query. Da Vinci does not anticipate computers in his work - or at least in the provided manuscript.

# 27.2 INFORMATION AS FEATURES

In this section, we introduce another method which aims to work with non-numerical objects. In this case, we consider the feature as follows. We observe one feature and the corresponding dependent variable. The feature itself is not a numeric feature in a classical sense, nor is it ordinal/cardinal variable. Imagine the feature is a document. Further, we observe a number of observations. We want to establish formally to work within such a framework, where we do not have features as we have been using today.

The missing piece we have to establish is a way to compare. Imagine the feature is a document. Further, we observe a number of observations. We want to establish formally to work within such a framework, where we do not have features as we have been using today.

The missing piece we have to establish is a way to compare. Imagine the feature is a document. Further, we observe a number of observations. We want to establish formally to work within such a framework, where we do not have features as we have been using today.

# Processing Information 533

The missing piece we have to establish is a way to compare. Imagine the feature is a document. Further, we observe a number of observations. We want to establish formally to work within such a framework, where we do not have features as we have been using today.

The missing piece we have to establish is a way to compare. Imagine the feature is a document. Further, we observe a number of observations. We want to establish formally to work within such a framework, where we do not have features as we have been using today.

The missing piece we have to establish is a way to compare. Imagine the feature is a document. Further, we observe a number of observations. We want to establish formally to work within such a framework, where we do not have features as we have been using today.

The missing piece we have to establish is a way to compare. Imagine the feature is a document. Further, we observe a number of observations. We want to establish formally to work within such a framework, where we do not have features as we have been using today.

The missing piece we have to establish is a way to compare. Imagine the feature is a document. Further, we observe a number of observations. We want to establish formally to work within such a framework, where we do not have features as we have been using today.

The missing piece we have to establish is a way to compare. Imagine the feature is a document. Further, we observe a number of observations. We want to establish formally to work within such a framework, where we do not have features as we have been using today.

# 27.2.1 Sample: Proteins

In this section, we introduce another method which aims to work with non-numerical objects. In this case, we consider the feature as follows. We observe one feature and the corresponding dependent variable. The feature itself is not a numeric feature in a classical sense, nor is it ordinal/cardinal variable. Imagine the feature is a document. Further, we observe a number of observations. We want to establish formally to work within such a framework, where we do not have features as we have been using today.

The missing piece we have to establish is a way to compare. Imagine the feature is a document. Further, we observe a number of observations. We want to establish formally to work within such a framework, where we do not have features as we have been using today.

The missing piece we have to establish is a way to compare. Imagine the feature is a document. Further, we observe a number of observations. We want to establish formally to work within such a framework, where we do not have features as we have been using today.

The missing piece we have to establish is a way to compare. Imagine the feature is a document. Further, we observe a number of observations. We want to establish formally to work within such a framework, where we do not have features as we have been using today.

# We will define two rather symbolic functions to achieve this:

```
.quantQ.infth.char2int([char])
// char argument of type char
// conversion from char to ASCII
:"-\$ char;
;
```

and

```
.quantQ.infth.char2([int])
// int argument of type integer
// conversion from ASCII to char
:"-\$ int;
;
```

In order to create a random protein, we use random integer generation and cast it between. The function which creates such a protein is given in the following:

```
.quantQ.infth.getProtein:([minLength;maxLength;nAcids]
// minLength length of the protein
// maxLength length of the protein
// nAcids number of different amino acids, number should not exceed
// 26 to have alphabetic representation offset for ASCII
// offset:quantQ.infth.char2int(["A"])
// choose the length of the protein
proteinLength: offset+first minLength+7(1+maxLength-minLength)
// create ASCII protein
protein: offset+proteinLength?nAcids;
// convert to chars and export
::quantQ.infth.int2char[protein];
;
```

Example of such a protein can be generated:

```
.quantQ.infth.getProtein(20;40;20);
```

> "MLBAFRAKRTEKIGSTRMPKSCHCAFHOGASSR"

For two proteins, we will be to assess and measure their difference. The suitable approach, as already advertised, is to use kernels. The kernels will allow us to assess the proximity relationship between two proteins. We can define a matrix with elements that are pairwise kernels for corresponding pairs. The index of a row and column of a proximity matrix corresponds to two proteins while the entry in the matrix is mutual proximity of those proteins. The kernels are the standard tool, and we can use methods we already know from literature dealing with numerical features. We will illustrate it in the nearest-neighbours method.
