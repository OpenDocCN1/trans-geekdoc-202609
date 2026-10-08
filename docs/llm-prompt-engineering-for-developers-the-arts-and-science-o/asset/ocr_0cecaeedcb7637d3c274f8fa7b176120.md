don’t need to access the vast training data, which isn’t always open to the public.

Over a wide range of tasks, we show that the lower the perplexity of the prompt is, the better the prompt is able to perform the task.

Perplexity is a measure or a metric of how well the model predicts a sample. A lower perplexity means the model is more certain and accurate in its predictions, while a higher perplexity indicates uncertainty. Think of perplexity as the model’s level of “surprise”. If a model reads a sentence and predicts the next word correctly without much doubt, it has low perplexity - it’s not very “surprised” by the actual next word because it expected it. Conversely, if it struggles to predict the next word, its perplexity is high - it’s more “surprised” by the actual word that comes next.

Think of this as giving someone a task in a language they are fluent in versus a language they’ve just started learning. Naturally, they’d perform better with the familiar language.

# ## 12.2 - How to Calculate Perplexity?

In general, perplexity is calculated using the following formula:
PP(s) = p(w1, w2, ..., wN) ^(-1/N)
Where:

+   * **s** is the sample
* **wx** is a word from the sample
* **N** is the number of words in the sample
* **p(wx)** is the probability of the word

If all words are independent, the formula can be simplified to:
p(w1, w2, ..., wN) = p(w1) * p(w2) * ... * p(wN)