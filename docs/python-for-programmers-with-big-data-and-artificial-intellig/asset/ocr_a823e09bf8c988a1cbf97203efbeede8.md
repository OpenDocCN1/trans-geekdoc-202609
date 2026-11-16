learning from sequences like the ones we described above.

RNNs have been used for many tasks including: 4 5 .

4 tps://www.analyticsindiamag.com/overview-of-recurrent-neural-etworks-and-their-applications/.

5 tps://en.wikipedia.org/wiki/Recurrent_neural_network#Applications.

6 ttp://karpathy.github.io/2015/05/21/rnn-effectiveness/.

+   * predictive text input—displaying possible next words as you type,
+   * sentiment analysis,
+   * responding to questions with the predicted best answers from a corpus,
+   * inter-language translation, and
+   * automated closed captioning in video.

# 15.9.1 Loading the IMDb Movie Reviews Dataset

The IMDb movie reviews dataset included with Keras contains 25,000 training samples and 25,000 testing samples, each labeled with its positive (1) or negative (0) sentiment. Let’s import the tensorflow.keras.datasets.imdb module so we can load the dataset:

lick here to view code image

```
[1]: from tensorflow.keras.datasets import imdb
```

The imdb module’s load_data function returns the IMDb training and testing sets. There are over 88,000 unique words in the dataset. The load_data function enables you to specify the number of unique words to import as part of the training and testing data. In this case, we loaded only the top 10,000 most frequently occurring words due to the memory limitations of our system and the fact that we’re (intentionally) training on a CPU rather than a GPU (because most of our readers will not have access to systems with GPUs and TPUs). The more data you load, the longer training will take, but more data may help produce better models:

lick here to view code image

```
[2]: number_of_words = 10000
[3]: (X_train, y_train), (X_test, y_test) = imdb.load_data(num_words=number_of_words)
```

The load_data function returns a tuple of two elements containing the training and testing sets. Each element is itself a tuple containing the samples and labels, respectively. In a given review, load_data replaces any words outside the top 10,000 with a placeholder value, which we’ll discuss shortly.