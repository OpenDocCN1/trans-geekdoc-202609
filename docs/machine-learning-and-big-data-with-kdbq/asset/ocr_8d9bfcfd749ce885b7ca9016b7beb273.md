# 526

# MACHINE LEARNING

the dictionary with word frequency, and returns the measure calculated sentence by

quantQ.infth.wordMeasure:[document;wordFrequency]
// document -- text we want to analyse
// wordFrequency -- dictionary with corpus word frequency
// calculates word frequency measure
:distinct [[x;y] tmp:count each group] "vs x;(tmp y key tmp];
- wordFrequency:each document;

;

In the provided function, the document has to be a subset of the entire corpus.
Furthermore, the corpus was used to generate the dictionary. Recall when a dictionary is called with a non-defined key, and
it returns the corresponding null value:

daVinciWordfrequency["xxx"]

0N

We encourage readers to check the function that such the measure can cope with new
words. We use a Bayesian framework to the procedure. It is important to keep in
mind that when improperly done, the measure can exceed 1.0, which would be rather
pathological.

Let us apply the measure on the daVinci sample:

```
daVinciSentenceAnalytics: quantQ.infth.wordMeasure[daVinci;
daVinciWordfrequency];
```

> The outcome is an array of dictionaries, where every element of the array corre-
sponds to one sentence decomposed by a measure.

first daVinciSentenceAnalytics

```
"there":"is":no":"human":"experience":"that":"can":"be":"termed":"true";"
science":"unless":"it":"mathematically":"demonstrated"!;0.0212766
-0.00327869 0.0192307 0.1428571 0.0625 0.00671149 0.0540545
-0.0194072 0.0833333 0.0666667 0.1666667 0.00460825 1
```

The word "there" has a measure 0.0212766, while "mathematically" has the measure.
The former word common across the corpus and thus does not have value for
On the other hand, the latter word is unique and adds to the analysed
sentence.

We add a function which adds two words to every sentence: one corresponding to
the average measure per sentence, and one corresponding to the maximum value of a
measure for a sentence. This will be a useful tool to process the process:

```
quantQ.infth.worddaAnalytics:[documentMeasure]
// document analysed with defined measure
// sentence by sentence add and average measure x
:{tmpAvg: avg value x; tmpMax: max value x; (raze key x;enlist
- AVERAGE!;enlist "MAX")!
(raze value x;enlist tmpAvg;enlist tmpMax)) each documentMeasure;
```

;