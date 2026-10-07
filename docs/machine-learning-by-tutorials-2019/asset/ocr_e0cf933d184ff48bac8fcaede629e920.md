# Machine Learning

# Chapter 15: Natural Language Transformation, Part 1

encoded as 5?

No, you didn't, but there's no way for a machine learning algorithm to know that. Larger values for a given feature affect the model's calculations more than smaller ones. At worst this will ruin your model, but at best it will slow down the training process as the model attempts to undo those implied relationships.

There are a couple ways to resolve this encoding problem. In the next chapter, you'll see a different option in that here you'll convert token's integer value into what's called a one-hot encoding.

One-hot encoding a feature involves replacing each value with a vector the same length as the number of all possible values. These vectors are filled with zeros in all but one position, which contains a one. Imagine you wanted to use just the days Monday through Friday as possible inputs to a model.

The following image shows what it looks like to one-hot encoded values:

| Monday | 1 | 0 | 0 | 0 | 0 |
| Tuesday | 0 | 1 | 0 | 0 | 0 |
| Wednesday | 0 | 0 | 1 | 0 | 0 |
| Thursday | 0 | 0 | 0 | 1 | 0 |
| Friday | 0 | 0 | 0 | 0 | 1 |

> One-hot encoded values

As you can see, each vector is length five — the number of possible values. And each of these vectors is filled with zeros except for a single one in a unique location. This essentially turns one feature — the day of the week — into five exclusive features representing boolean flags indicating their absence or presence.

For your seq2seq model, there are in_vocab_size possible input values, and out_vocab_size output values. Rather than pass a sequence of integers to the model, you'll pass a matrix where each row represents a single character, one-hot encoded as the same size as the corresponding vocabulary.

To keep things in manageable chunks, you'll split the logic to one-hot encoding training batches into two functions. The first will create appropriately sized NumPy arrays filled with zeros, and the second will place ones into those arrays at the correct locations to encode the sequences.