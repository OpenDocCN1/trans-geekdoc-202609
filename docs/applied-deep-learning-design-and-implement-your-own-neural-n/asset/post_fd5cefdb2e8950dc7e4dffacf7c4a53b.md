
So, here the successive inputs are not independent of each other as while predicting the character e, we will want to know the previous input to the model along with the current input. Moreover, here the length of the input word, along with the total number of predictions, is not fixed. Such as, words have, input, and character all have a different number of total characters.

Also, if we observe figure 6.5, we can see that each network (represented with red-blue-green) is performing the same task; that is, it is taking input as a character and producing the output as a character.

Let us elaborate on each of the vertical networks of figure 6.5 to understand what they are. Each vertical network consists of the input layer as red, the hidden layer as blue, and the output layer as green, which are connected through the Fully Connected layer, as shown in figure 6.6:

![](img/7e519fee1b702b91799cdf1664598392_432_0.png)

Figure 6.6: Fully connected network

These types of problems are known as sequential learning problems, where the input is in the form of sequential data. Thus, we have to look at the sequence of the input data, which is dependent on each other, and finally, predict the output.

Also, here each input directs to a time stamp. Let us take another example to understand it properly. Let us say we have been assigned the task of predicting different parts of speech (POS) tags in a given sentence, such as noun, verb, adverb, and adjective in a given sentence, as shown in figure 6.7. Let us say we have a sentence as man is a social animal:

![](img/7e519fee1b702b91799cdf1664598392_433_0.png)

Figure 6.7: Speech tag prediction (POS prediction)

Now, in a sentence, once we can see the word social, which is an adjective, we can confidently say that the next word is a noun, that is, man or animal. Hence, the current output, which is a noun, depends on the current as well as the previous input. And also, the size of the input is not fixed, as sentences can have any number of total words.

As we can observe in figure 6.7, we are predicting the output for every timestamp. And again, each network is performing the same task, that is, taking input like a word and giving output as a tag.

Sometimes instead of predicting the output at every stage, we may want to predict the output at the final stage only. So, in such types of cases, the model must look at the full sequence first and then predict the output.

Consider a case of prediction of the movie review’s polarity as shown in figure 6.8 for the sentence The movie was boring and long:

![](img/7e519fee1b702b91799cdf1664598392_434_0.png)

Figure 6.8: Polarity prediction of movie review

If we observe figure 6.8, we can see that the prediction of the polarity does not only depend upon the previous word but also on the words which appeared before.

Here, again sentences can be composed of anything and not only words. For example, a video can be treated as a sequence of images. For example, a video of Surya Namaskar, as shown in figure 6.9:

![](img/7e519fee1b702b91799cdf1664598392_435_0.png)

## Sequence generation

The process of sequence generation generates a new sequence of output, which has the same characteristics as that of other sequences.

For example:

- Given: [a, c, e], [g, i, k]
- Predict: [c, e, g]

Some other examples of sequence generation are as follows:

- **Generation of music**: If given a set of music examples, the model has to generate new musical components that have the same properties as the provided musical components.
- **Generation of text**: If given a set of text data, such as some words from the novel of Shakespeare, the model has to generate new words or sentence components, which have the same properties of the provided Shakespeare text component.
- **Prediction of handwriting:** If given a set of handwriting data of a person, the model has to generate handwriting for new words or sentence components, which have the same properties of the provided handwritten data component.

Also, the generation of the sequence by using a single input observation comes under the sequence generation process.

For example, the textual (automatic) description of the input image is a part of this. Such that we have given an input image, and we have to generate the word sequence which describes the input image, as shown in figure 6.10:

![](img/7e519fee1b702b91799cdf1664598392_436_0.png)

Figure 6.10: Textual description of an image

## Sequence classification

Sequence classification is the process of prediction of a class label for an input sequence. For example, in figure 6.11:

- Given: a, b, c, d, e
- Predict: “bad” or “good”

![](img/7e519fee1b702b91799cdf1664598392_436_1.png)

Figure 6.11: Textual description of an image

Sequence classification aims to make a model that performs the classification by using a dataset (X-Labeled) such that the model can predict the upcoming unseen sequence class models.

Here, the input data sequence can be in the form of numerical numbers such as real or discrete numbers, so for this, the sequence classification process is termed as discrete sequence classification.

Some other applications of sequence classification are as follows:

- **Anomalous sequence detection**: Here, a model is provided with a definite sequence of observations, and the model has to predict if the provided sequence shows anomalous behavior or not.
- **Classification of the DNA Sequence**: When provided AGCT values of the DNA sequence, the model has to predict whether the AGCT values belong to the non-coding region or the coding region.
- **In Semantic Analysis**: When given a phrase or paragraph denoting a tweet or a review of some movie, the model has to predict if the phrase is negative or positive.

## Sequence to sequence predictions

It is the process of prediction of the output sequence when given an input sequence.

For example, in figure 6.12:

- **Given sequence**: a, b, c, d, e.
- **Predict sequence**: f, g, h, i, j.

![](img/7e519fee1b702b91799cdf1664598392_437_0.png)

Figure 6.12: Sequence-to-sequence prediction model

It is the extended version of Sequence prediction in which instead of predicting a new value in the sequence, the whole sequence is being predicted, which may or may not be of similar length of the old sequence.

For time-series input and output sequences, the problem is referred to as time-series forecasting modeling.

Some more examples of sequence-to-sequence prediction are as follows:

- **Predicting the summary of the text**: In this case, a document of some text is provided to the model; the model has to predict the shorter sequence or, say, the summary of the text, which must include all the important information regarding the original text document.
- **Forecasting for multi-step time series problems**: When given a series of timestamp observations, the model has to predict the upcoming sequence of a range of observations for future time stamps.
- **Execution of the Program**: When given a mathematical equation or some textual program, the model has to predict the numerical or alphabetical sequences, which should describe the output of the program.

## Recurrent neural networks (RNN)

Do you know how Google’s feature of auto-complete sentence prediction predicts the remaining words which the user is typing in Google’s search icon?

First is the collection of large volumes of the most frequently occurring consecutive words, as shown in figure 6.13:

![](img/7e519fee1b702b91799cdf1664598392_438_0.png)

Figure 6.13: Collection of large volumes of most frequently occurring consecutive words

This is fed into an RNN, which performs the analysis of data by determining the sequence of the words occurring frequently and builds a model that predicts the next word in the sentence, as shown in figure 6.14:

![](img/7e519fee1b702b91799cdf1664598392_439_0.png)

Now, let us say the user types a sentence such as **What is the best food to eat in New**, as shown in figure 6.15:

![](img/7e519fee1b702b91799cdf1664598392_439_1.png)

So google will recommend that the most common auto-complete word for this sentence is Delhi as **What is the best food to eat in New Delhi**, as shown in figure 6.16:

![](img/7e519fee1b702b91799cdf1664598392_439_2.png)
