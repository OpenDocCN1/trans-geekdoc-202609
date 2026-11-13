# PREPARING THE DATA

Just like in the previous chapter, let's download and uncompress the IMDB movie reviews dataset.

# Listing 12.2 Downloading and uncompressing the IMDB movie reviews dataset

```
```
!wget https://ai.stanford.edu/~amaas/data/sentiment/aclImdb_v1.tar.gz
!tar -xf aclImdb_v1.tar.gz
```
```

You're already familiar with the structure of the data: we get a folder named aclImdb containing two subfolders, one for negative-sentiment movie reviews, and one for positive-sentiment reviews. There's one text file per review. We'll call `text_dataset_from_directory` with `label_mode=None` to create a dataset that reads from these files and yields the text content of each file.

# Listing 12.3 Creating a dataset from text files (one file = one sample)

```
```
import tensorflow as tf
from tensorflow import keras
dataset = keras.utils.text_dataset_from_directory(
    directory="aclImdb", label_mode=None, batch_size=256)
dataset = dataset.map(lambda x: tf.strings.regex_replace(x, "<br />", " "))
```
```

> Strip the `<br />` HTML tag that occurs in many of the reviews. This did not matter much for text classification, but we wouldn't want to generate `<br />` tags in this example!

Now let's use a TextVectorization layer to compute the vocabulary we'll be working with. We'll only use the first `sequence_length` words of each review: our TextVectorization layer will cut off anything beyond that when vectorizing a text.

# Listing 12.4 Preparing a TextVectorization layer

```
```
from tensorflow.keras.layers import TextVectorization
sequence_length = 100
vocab_size = 15000
text_vectorization = TextVectorization(
    max_tokens=vocab_size,
    output_mode="int",
    output_sequence_length=sequence_length,
)
text_vectorization.adapt(dataset)
```
```

> We'll only consider the top 15,000 most common words—anything else will be treated as the out-of-vocabulary token, "[UNK]".

> We want to return integer word index sequences.

> We'll work with inputs and targets of length 100 (but since we'll offset the targets by 1, the model will actually see sequences of length 99).

Let's use the layer to create a language modeling dataset where input samples are vectorized texts, and corresponding targets are the same texts offset by one word.

# Listing 12.5 Setting up a language modeling dataset

```
```
def prepare_lm_dataset(text_batch):
    vectorized_sequences = text_vectorization(text_batch)
```
```

> Convert a batch of texts (strings) to a batch of integer sequences.