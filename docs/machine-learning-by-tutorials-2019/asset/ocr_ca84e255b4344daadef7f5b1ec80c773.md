# Examples where context after a word matters

| English | Spanish |
|---|---|
| She waited by the bank of the river. | Ella esperó la orilla del río. |
| She waited by the bank until he came out with the money. | Ella esperó junto al hasta que él salió del dinero. |

The first five words are the same in the English versions of sentences, but the first two end up in the Spanish translations. That's because the meaning of the word "bank" is different in each sentence, so you cannot know that until you read that word in the sentence. That is, its meaning comes from its context, including the words *before* and *after*.

In order to consider the full context surrounding each token, you can use what's called a **bidirectional recurrent neural network** (BRNN), which processes sequences in both directions, like this:

![](bbox=[0.277, 0.429, 0.722, 0.606])

As the diagram shows, a bidirectional RNN consists of two recurrent layers: one processing the sequence from left to right and the other from right to left. These layers act independently of each other, but their outputs get merged into a single vector. In this chapter, you'll concatenate them, but other merge options, like taking the sum or average, can also work. The number of units in your bidirectional layer's output will be twice the number in its recurrent layers.

The forward and reverse layers themselves can be any recurrent type, such as the LSTMs you've worked with elsewhere in this book. However, in this chapter, you will use a new type called **gated recurrent unit**, or GRU.

GRUs were invented after Ls and were meant to serve the same purpose of learning longer-term relationships while training more than standard recurrent layers. Internally, they are implemented differently from LSTMs, but from a user's standpoint, the main difference is that they do not have separate hidden and

Bidirectional RNN