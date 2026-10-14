+   1. Load the data and create a list of text string descriptions of each wine.
+   2. Pad punctuation with spaces, so that each punctuation mark is treated as a separate word.
+   3. Pass the strings through a TextVectorization layer that tokenizes the data and pads/clips each string to a fixed length.
+   4. Create a training set where the inputs are the tokenized text strings and the outputs to predict are the same strings shifted by one token.

![](bbox=[0.12, 0.26, 0.88, 0.44])

Figure 9-1. Data processing for the Transformer

# Attention

The first step to understanding how GPT works is to understand how the attention mechanism works. This mechanism is what makes the Transformer architecture unique and distinct from recurrent approaches to language modeling. When we have developed a solid understanding of attention, we will then see how it is used within Transformer architectures such as GPT.

When you write, the choice that you make for the next word tensor in the sentence is influenced by other words that you have already written. For example, suppose you start a sentence as follows:

```
The pink elephant tried to get into the car but it was too
```

Clearly, the next word should be something synonymous with big. How do we know this?

Certain other words in the sentence are important for helping us to make our decision. For example, the fact that it is an elephant, rather than a sloth, means that we prefer big rather than slow. If it were a swimming pool, rather than a car, we might choose scared as a possible alternative to big. Lastly, the action of getting into the car implies that size is the problem—if the elephant was trying to squash the car instead, we might choose fast as the final word, with it now referring to the car.