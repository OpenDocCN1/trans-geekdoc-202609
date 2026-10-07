# Machine Learning Chapter 15: Natural Language Transformation, Part 1

training your model, but for now just know we chose 45 based on the length of the
Spanish sentences in the SMDB app.

You can display the list of items to be sure they look as expected:

```
print(samples[:2])
[('Ve.', '\tGo.\\n'), ('Vete.', '\tGo.\\n')]
```

The first two samples after loading the dataset

> Note: The two lines you wrote to create samples a Python construct called
list comprehensions. If you aren't familiar with this syntax, it's an optimized
way to create a list by iterating over a collection. The anatomy of a
comprehension is [a for b in c]. It creates a new list with items madey calling the expression with each item b from the collection c. Optionally,
You can add a condition to limit which items from c you process, this is: [a
for b in c if d] where d is some conditional expression involving b. You
should get comfortable with this syntax if you plan on using Python since it's
extremely common — plus the Python interpreter runs these more efficiently
for loops builds with append.

If you've followed along with this book far, then you already know it's best tonhave separate training, validation and test sets when building machine learning
models.keras can randomly select samples from your training data to use for
validation when you train your model, but you won't rely on that. That's
there is a situation you need to handle when working with text — out-of-
vocabulary (OOV) tokens — and that requires some preprocessing on the validation
sets. You'll deal with it in hand, for now, separating the data into training
and validation sets. Run a call with the following code to do so:

```
from sklearn.model_selection import train_test_split
train_samples, valid_samples = train_test_split(
samples, train_size=.8, random_state=42)
```

You use scikit-learn train_test_split to randomly assign samples from
your dataset into training and validation sets, with 80 percent going towards
training. Providing a random_state is optional, but specifying 42 here generates the
s datasets we used when training our models.

Before you deal with OOV tokens, you need to know what's in the vocabulary.