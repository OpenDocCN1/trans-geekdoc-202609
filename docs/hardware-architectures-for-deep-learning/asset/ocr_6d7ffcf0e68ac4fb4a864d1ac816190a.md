# Chapter 2

# Hardware acceleration for recurrent
neural networks

Sima Sinaei¹ and Masoud Daneshtalab¹

Sequence learning refers to an important subset of machine learning tasks that deal
with data for which order is important—that is, the data is arranged in a specific order,
and this order is relevant to the task at hand. For example, a sequence learning task
might be to predict the next-day closing price of a stock, given the closing price of that
stock from the past 60 days. This is a regression task, in which the goal is to predict
an unknown continuous-valued output. Another example of a sequence learning task
would be to predict the next word in a sentence, given a sample phrase like “went
to the gym to exercise." This is a classification task, where the goal is to predict
unknown, but discrete-valued output. Another example would be to label the word
being spoken in a segment of audio; this is also a classification task, but the goal
to produce the correct label for the entire sequence, rather than for the next item
in the sequence. There is a wide range of sequence learning problems, for which
special class of neural networks, recurrent neural networks (RNN), often yield
state-of-the-art results.

One of the most widely used and effective RNN models used for sequence learning
is called short-term memory (LSTM) [1]. This model is derived from a basic
modification to the baseline RNNs for more efficient handling of sequential data.
LSTM is a powerful neural network algorithm that has been shown to provide state-
of-the-art performance in various sequence learning tasks, including natural language
processing (NLP) [2], video classification [3], and speech recognition [4].

Implementing a deep learning task takes place in two stages: training and
inference. During the training phase, a large amount of data is fed to the model in a
recurrent phase. By examining the difference between the desired output and the
actual output returned by the model, small incremental adjustments are made to
t model's parameters until it can perform the task with an acceptable level of accuracy
over the training dataset. Then, in the inference stage, the trained neural network is
employed to perform the target task under real-world workloads. An appropriately
trained neural network can generate accurate output for the input data, including the
data that were not in the training data set.

¹Division of Intelligent Future Technologies, Mälardalen University, Västerås, Sweden