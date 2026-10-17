
Next, the variable iterator is initialized, and then the first two elements of the sents variable are displayed. The next four blocks of code invoke the `wordshape()` method of the TensorFlow text class in order to display capitalized tokens, upper case tokens, tokens with punctuation, and numeric tokens.

The last portion of [Listing 10.13](#ch10.xhtml#list10.13) invokes the `ngrams()` method of the built-in text class to initialize the variable bigrams with the bigrams in the tokens variable and then display the results. Launch the code in [Listing 10.13](#ch10.xhtml#list10.13) and you will see the following output:

`\[\[b'When', b'ignorance', b'is', b'bliss.'\]\] \[\[b'Tis', b'folly', b'to', b'be', b'wise!'\]\] tokens: <tf.RaggedTensor \[\[\[b'When', b'ignorance', b'is', b'bliss.'\]\], \[\[b'Tis', b'folly', b'to', b'be', b'wise!'\]\], \[\[b'According', b'to', b'the', b'famous', b'Bard!'\]\]\]>   Capitalized tokens: \[\[\[True, False, False, False\]\], \[\[True, False, False, False, False\]\], \[\[True, False, False, False, True\]\]\]   Uppercase tokens: \[\[\[False, False, False, False\]\], \[\[False, False, False, False, False\]\], \[\[False, False, False, False, False\]\]\]   tokens with punctuation: \[\[\[False, False, False, True\]\], \[\[False, False, False, False, True\]\], \[\[False, False, False, False, True\]\]\]   Numeric tokens: \[\[\[False, False, False, False\]\], \[\[False, False, False, False, False\]\], \[\[False, False, False, False, False\]\]\]   bigrams: \[\[\[b'When ignorance', b'ignorance is', b'is bliss.'\]\], \[\[b'Tis folly', b'folly to', b'to be', b'be wise!'\]\], \[\[b'According to', b'to the', b'the famous', b'famous Bard!'\]\]\] 

## **TF2/Keras and Word Encodings**

[Listing 10.14](#ch10.xhtml#list10.14) displays the contents of tf2_encoding.py that illustrates how to tokenize a sentence.

***LISTING 10.14: tf2_encoding.py***

```python
import tensorflow as tf train_data = [ "I enjoy coffee.", "I enjoy tea.", "I dislike milk.", "I am going to the supermarket later this morning for some coffee." ] test_data = [ "Enjoy coffee this morning.", "I enjoy going to the supermarket.", "Want some milk for your coffee?" ] num_words = 1000 oov_token = '<UNK>' pad_type = 'post' trunc_type = 'post' # Tokenize our training data tokenizer = tf.keras.preprocessing.text.Tokenizer(num_words=num_words, oov_token=oov_token) tokenizer.fit_on_texts(train_data) # Get our training data word index word_index = tokenizer.word_index # Encode training data sentences into sequences train_sequences = tokenizer.texts_to_sequences(train_data) # Get max training sequence length maxlen = max([len(x) for x in train_sequences]) # Pad the training sequences train_padded = tf.keras.preprocessing.sequence.pad_sequences(train_sequences, padding=pad_type, truncating=trunc_type, maxlen=maxlen) # Output the results of our work print("Word index:\\n", word_index) print("\\nTraining sequences:\\n", train_sequences) print("\\nPadded training sequences:\\n", train_padded) print("\\nPadded training shape:", train_padded.shape) print("Training sequences data type:", type(train_sequences)) print("Padded Training sequences data type:", type(train_padded))
```

[Listing 10.14](#ch10.xhtml#list10.14) starts with import statements and then initializes the variables train_data and test_data with a set of documents. The remaining code is very similar to the contents of [Listing 10.3](#ch10.xhtml#list10.3), which will not be duplicated here.

One other point to keep in mind: The pad_type parameter specifies how to pad sentences so that they will have the same length: the padding can be performed at the beginning of a sentence (“pre-pad”) or at the end of a sentence (“post-pad”). Now launch the code in [Listing 10.14](#ch10.xhtml#list10.14) and you will see the following output:

Word index: {'<UNK>': 1, 'i': 2, 'enjoy': 3, 'coffee': 4, 'tea': 5, 'dislike': 6, 'milk': 7, 'am': 8, 'going': 9, 'to': 10, 'the': 11, 'supermarket': 12, 'later': 13, 'this': 14, 'morning': 15, 'for': 16, 'some': 17} Training sequences: \[ \[2, 3, 4\], \[2, 3, 5\], \[2, 6, 7\], \[2, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 4\]\] Padded training sequences: \[\[ 2  3  4  0  0  0  0  0  0  0  0  0\]   \[ 2  3  5  0  0  0  0  0  0  0  0  0\]   \[ 2  6  7  0  0  0  0  0  0  0  0  0\]   \[ 2  8  9 10 11 12 13 14 15 16 17  4\]\] Padded training shape: (4, 12) Training sequences data type: <class 'list'> Padded Training sequences data type: <class 'numpy.ndarray'> 

## **Text Summarization with TF2/Keras and Reuters Dataset**

[Listing 10.15](#ch10.xhtml#list10.15) displays the contents of reuters_mlp.py that illustrates how to perform text summarization with a Keras-based MLP in TF2. This code sample has been adapted from reuters_mlp.py that is part of the standalone Keras distribution:

*[https://github.com/keras-team/keras/blob/master/examples/reuters_mlp.py](https://github.com/keras-team/keras/blob/master/examples/reuters_mlp.py)*

***Listing 10.15: reuters_mlp.py***

```python
#Train/evaluate an MLP on the Reuters dataset from __future__ import print_function import tensorflow as tf import numpy as np max_words = 1000 batch_size = 32 epochs = 5 print('Loading data...') (x_train, y_train), (x_test, y_test) = tf.keras.datasets.reuters.load_data(num_words=max_words, test_split=0.2) print(len(x_train), 'train sequences') print(len(x_test), 'test sequences') num_classes = np.max(y_train) + 1 print(num_classes, 'classes') print('Vectorizing sequence data...') tokenizer = tf.keras.preprocessing.text.Tokenizer(num_words=max_words) x_train = tokenizer.sequences_to_matrix(x_train, mode='binary') x_test = tokenizer.sequences_to_matrix(x_test, mode='binary') print('x_train shape:', x_train.shape) print('x_test shape:', x_test.shape) print('Convert class vector to binary class matrix (for use with categorical_crossentropy)') y_train = tf.keras.utils.to_categorical(y_train, num_classes) y_test = tf.keras.utils.to_categorical(y_test, num_classes) print('y_train shape:', y_train.shape) print('y_test shape:', y_test.shape) print('Building Keras-based model...') model = tf.keras.models.Sequential() model.add(tf.keras.layers.Dense(512, input_shape=(max_words,))) model.add(tf.keras.layers.Activation('relu')) model.add(tf.keras.layers.Dropout(0.5)) model.add(tf.keras.layers.Dense(num_classes)) model.add(tf.keras.layers.Activation('softmax')) print("Compilation step...") model.compile(loss='categorical_crossentropy', optimizer='adam', metrics=['accuracy']) print("Training step...") history = model.fit(x_train, y_train, batch_size=batch_size, epochs=epochs, verbose=1, validation_split=0.1) print("Evaluation step...") score = model.evaluate(x_test, y_test, batch_size=batch_size, verbose=1) print('Test score: ', score[0]) print('Test accuracy:', score[1])
```

[Listing 10.15](#ch10.xhtml#list10.15) starts with an import statement and then initializes four variables with data from the built-in Reuters dataset, as shown here:

`(x_train, y_train), (x_test, y_test) = tf.keras.datasets.reuters.load_data(num_words=max_words, test_split=0.2)`

Next, the variable tokenizer is initialized as you have seen in previous examples, and then the variables x_train and x_test are converted to 2D arrays via the method tokenizer.sequences_to_matrix(), followed by the variables y_train and y_test that are converted from vectors to binary class matrices. Note that in this code sample the vectors are integer-valued, but the vectors can be floating point values for other types of tasks (such as image classification).
