According to Table 4.2, if you pass the encoded version of the country variable to a model, it will make assumptions such as “Brazil (3) is greater than Canada (2),” which does not make any sense.

One possible solution for that scenario is applying another type of transformation on top of “country”: one-hot encoding. This transformation will represent all the categories from the original feature as individual features (also known as dummy variables), which will store the presence or absence of each category. Table 4.3 is transforming the same information from Table 4.2, but this time it’s applying one-hot encoding:

| Country | India | Canada | Brazil | Australia |
|---|---|---|---|---|
| India | 1 | 0 | 0 | 0 |
| Canada | 0 | 1 | 0 | 0 |
| Brazil | 0 | 0 | 1 | 0 |
| Australia | 0 | 0 | 0 | 1 |
| India | 1 | 0 | 0 | 0 |

Table 4.3 – One-hot encoding in action

You can now use the one-hot encoded version of the country variable as a feature of an ML model. However, your work as a skeptical data scientist is never done, and your critical thinking ability will be tested in the AWS Machine Learning Specialty exam.

Suppose you have 150 distinct countries in your dataset. How many dummy variables would you come up with? 150, right? Here, you just ran into a potential issue: apart from adding complexity to your model (which is not a desired characteristic of any model at all), dummy variables also add sparsity to your data.

A sparse dataset has a lot of variables filled with zeros. Often, it is hard to fit this type of data structure into memory (you can easily run out of memory), and it is very time-consuming for ML algorithms to process sparse structures.

You can work around the sparsity problem by grouping your original data and reducing the number of categories, and you can even use custom libraries that compress your sparse data and make it easier to manipulate (such as scipy.sparse.csr_matrix, from Python).

Therefore, during the exam, remember that one-hot encoding is definitely the right way to go when you need to transform categorical/nominal data to feed ML models; however, take the number of