
## Deep learning algorithms for NLP

Following are the deep learning algorithms used for NLP:

- Deep learning models, such as recurrent neural networks (`RNNs`) and transformer-based architectures (for example, Bidirectional Encoder Representations from Transformers (`BERT`), have revolutionized NLP.
- These models excel in tasks like machine translation, sentiment analysis, and question answering.

### Text preprocessing

Text preprocessing is the process of transforming unstructured text into structured form for analysis. It involves tasks like tokenization, normalization, and stop word removal to enhance accuracy and efficiency in NLP tasks.

Here are some of the main components of text preprocessing:

- Tokenization: Breaking text into words or sub-word units.
- Using `torchtext`: `torchtext` provides utilities for text processing, including tokenization.

The code snippet in the following uses the tokenizer function from `torchtext`. It processes the sample text input and tokenizes:

```
import torchtext

from torchtext.data import get_tokenizer

tokenizer = get_tokenizer("basic_english")

sentence = "You can now install TorchText using pip!"

tokens = tokenizer(sentence)

print(tokens)

# Output: ['you', 'can', 'now', 'install', 'torchtext', 'using', 'pip', '!']
```

The basic English tokenizer splits the sentence into lowercase tokens, removing punctuation.

- Using pre-trained models: If you are working with more complex models like Text-to-Text Transfer Transformer (`T5`), tokenization involves additional steps.

For instance, `T5` uses a SentencePiece model for text tokenization.

The code snippet in the following uses a pre-trained SentencePiece model to build the text preprocessing pipeline:

```
from torchtext.models import T5Transform

padding_idx = 0

eos_idx = 1

max_seq_len = 512

t5_sp_model_path = "[^1^][1]"

transform = T5Transform(

sp_model_path=t5_sp_model_path,

max_seq_len=max_seq_len,

eos_idx=eos_idx,

padding_idx=padding_idx,

)
```

This pipeline tokenizes, converts tokens to integer IDs, truncates sequences, and adds end-of-sequence (`EOS`) and padding token IDs.

#### Stop word removal, stemming, and lemmatization

Stop words are common words (for example, `the` and `in`) that add little meaning to a sentence. Stop word removal helps improve text processing efficiency and focuses on essential content. Stemming reduces words to their root form by removing suffixes (for example, `running` to `run`). It helps with information retrieval and indexing in search engines. Lemmatization converts words to their base or dictionary form (for example, `better` to `good`). It preserves semantic meaning and is more accurate than stemming.

The code snippet in the following uses the library Natural Language ToolKit (`NLTK`) to remove the stop words:

- Stop word removal using `NLTK`: The following codes are used:

```
import nltk

from nltk.corpus import stopwords

from nltk.tokenize import word_tokenize

nltk.download('stopwords')

nltk.download('punkt')

example_sent = "This is a sample sentence, showing off the stop words filtration."

tokens = word_tokenize(example_sent)

filtered_tokens = [word for word in tokens if word.lower() not in stopwords.words('english')]

print(filtered_tokens)

# Output: ['sample', 'sentence', ',', 'showing', 'stop', 'words', 'filtration', '.']
```

- Lemmatization using `NLTK`: Lemmatization reduces words to their base or dictionary form.

The code snippet below uses the `NLTK` library that provides a lemmatizer:

```
from nltk.stem import WordNetLemmatizer

lemmatizer = WordNetLemmatizer()

lemmatized_tokens = [lemmatizer.lemmatize(word) for word in filtered_tokens]

print(lemmatized_tokens)

# Output: ['sample', 'sentence', ',', 'showing', 'stop', 'word', 'filtration', '.']
```

- Stemming using `NLTK`: Stemming reduces words to their root form.

The code snippet in the following uses the `NLTK` library that provides a stemmer:

```
from nltk.stem import PorterStemmer

stemmer = PorterStemmer()

stemmed_tokens = [stemmer.stem(word) for word in filtered_tokens]

print(stemmed_tokens)

# Output: ['sampl', 'sentenc', ',', 'show', 'stop', 'word', 'filtrat', '.']
```

#### Handling special characters, punctuation, and case sensitivity

Special characters (for example, `@`, `#`) need to be removed characters during text preprocessing. They can disrupt tokenization and model performance.

Punctuation helps in the detection of sentence boundaries. It can be retained or removed based on context.

Case sensitivity is normalizing text to lowercase for consistency. It helps avoid duplication (for example, `apple` versus `Apple`).

Let us look into code examples:

- Removing special characters and punctuation: The code snippet in the following uses regular expressions or string manipulation to remove special characters and punctuation:

```
import re

def remove_special_chars(text):

return re.sub(r'[^a-zA-Z0-9\s]', '', text)

cleaned_sentence = remove_special_chars(sentence)

print(cleaned_sentence)

# Output: "This is an Example Sentence"
```

- Lowercasing text: The code snippet in the following converts the input text into lowercase, as shown in the output:

```
sentence = "This is an Example Sentence."

lowercased_sentence = sentence.lower()

print(lowercased_sentence)

# Output: "this is an example sentence."
```

## Text classification

Text classification involves assigning predefined labels or categories to text documents. In this chapter, we explore both binary and multiclass text classification using PyTorch:

- Binary text classification: Binary text classification deals with problems where there are only two possible classes. Examples include spam detection (`spam` vs. `non-spam`) or sentiment analysis (`positive` vs. `negative`). The approach is to build models that learn to distinguish between these two classes effectively. PyTorch provides powerful tools for implementing logistic regression and other algorithms.
- Multiclass text classification: Multiclass text classification extends binary classification to handle more than two classes. For instance, classifying news articles into topics like sports, politics, or entertainment. Techniques such as one-vs-rest or softmax activation can be used for multiclass classification.

We will explore how to adapt existing models for this purpose.

### Supervised learning algorithms for text classification

Several algorithms can be used for text classification in PyTorch. Following is the list of algorithms that can be adapted for text classification using PyTorch:

- Logistic regression: It is a linear model commonly used for text classification. It models the probability of a document belonging to a particular class. In PyTorch, we can implement logistic regression using a single-layer neural network.
- Support vector machines (`SVM`): `SVMs` can be tailored for text classification using appropriate kernel functions (for example, linear and radial basis functions). They find a hyperplane that best separates text features in high-dimensional space. PyTorch libraries allow us to implement `SVM`-like models.
- Neural networks for text classification: Neural networks offer a versatile range of architectures for tackling text classification tasks, each suited to capture different aspects of text data for effective learning and prediction.
- Model architectures: Here are some key types of neural network architectures used in text classification:

  - Feedforward neural networks (`FNNs`) with hidden layers learn complex representations from text data.
  - Convolutional neural networks (`CNNs`) capture local patterns (for example, n-grams) in text.
  - `RNNs` process sequential data (for example, sentences and documents).

### Evaluation metrics for text classification

There are different evaluation metrics that can be used for text classification. Following are some of the important and popular evaluation metrics:
