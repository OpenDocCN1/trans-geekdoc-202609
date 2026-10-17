
```python
print("input sentence #2:")

print(text2)

print()

print("Tokens from input sentence #2:")

print(tokenized_text2)

print()

# Map token strings to their vocabulary indices:
indexed_tokens2 = tokenizer.convert_tokens_to_ids(tokenized_text2)

# Display the words with their indices:
for pair in zip(tokenized_text2, indexed_tokens2):
    print('{:<12} {:>6,}'.format(pair[0], pair[1]))
```

The first half of Listing 11.9 is almost identical to the first half of Listing 11.8, using the variable `text2` instead of `text1`.

The next portion of Listing 11.9 contains two blocks of `print()` statements that display the contents of `text2` and `tokenized_text2`, respectively. The next code snippet initializes the variable `indexed_tokens2` to the result of converting the tokens in `tokenized_text2` to id values.

The final portion of Listing 11.9 contains a loop that displays tokens and their associated id values. The output of Listing 11.9 is here:

```text
input sentence #2: I got a book and after I book for an hour, it's time to book it.

Tokens from input sentence #2: ['[CLS]', 'i', 'got', 'a', 'book', 'and', 'after', 'i', 'book', 'for', 'an', 'hour', ',', 'it', "'", 's', 'time', 'to', 'book', 'it', '.', '[SEP]']

[CLS]            101 i            1,045 a            1,037 book          2,338 and          1,998 after        2,044 i            1,045 book        2,338 for          2,005 an          2,019 hour        3,178 ,            1,010 it          2,009 '          1,005 s          1,055 time        2,051 to        2,000 book        2,338 it        2,009 .          1,012 [SEP]        102
```

## The BERT Family

BERT has spawned a remarkable set of variations of the original BERT model, each of which provides some interesting features. Some of those variations are listed here:

- `ALBERT`
- `DistilBERT`
- `CamemBERT`
- `FlauBERT`
- `RoBERTa`
- `BioBERT`
- `DocBERT`
- `ClinicalBERT`
- `German BERT`

A lite BERT for self-supervised learning of language representations (`ALBERT`) was created by Google Research and Toyota Technological Institute. Like `RoBERTa`, `ALBERT` is significantly smaller than BERT, and it’s also more capable than BERT.

Keep in mind that `ALBERT` (unlike BERT) shares its parameters in all layers, which reduces the number of parameters, but has no effect on the training and inference time. In addition, `ALBERT` uses embedding matrix factorization, which further reduces the number of parameters. Furthermore, `ALBERT` uses sentence-order prediction (SOP), which is an improvement over next sentence prediction (NSP). Finally, `ALBERT` does not use a dropout rate, which also increases the model capacity.

`ALBERT` uses both whole-word masking and “n-gram masking,” where the latter refers to masking multiple sequential words. Here is a code snippet for `ALBERT`:

```python
from transformers import AlbertForMaskedLM, AlbertTokenizer

model1 = AlbertForMaskedLM.from_pretrained('albert-xxlarge-v1')
tokenizer = AlbertTokenizer.from_pretrained('albert-xxlarge-v1')

model2 = AlbertForMaskedLM.from_pretrained('albert-xxlarge-v2')
tokenizer = AlbertTokenizer.from_pretrained('albert-xxlarge-v2')
```

`DistilBERT` is a smaller version of BERT that contains 66 million parameters, which is 40% of the number of parameters of BERT Base (which has 110 million parameters). Even so, `DistilBERT` achieves 97% of BERT accuracy and is 60% faster than BERT Base, which makes `DistilBERT` useful for transfer learning.

As an aside, *knowledge distillation* involves a small model (called the “student”) that is trained to mimic a larger model or an ensemble of models (called the “teacher”). `DistilBERT` is an example of a distilled network that is also used in production.

To give you an idea of the type of code required for `DistilBERT`, here is an example of instantiating a `DistilBERT` tokenizer:

```python
import transformers

tokenizer = transformers.AutoTokenizer.from_pretrained('distilbert-base-uncased', do_lower_case=True)
```

Here is another example of instantiating a `DistilBERT` tokenizer:

```python
from transformers import DistilBertTokenizer: tokenizer = DistilBertTokenizer.from.pretrained('distilbert-base-uncased')
```

`RoBERTa` (from Facebook) leverages BERT’s language masking strategy, along with some modifications of BERT’s hyperparameters. Note that `RoBERTa` was trained on a corpus that is at least 10 times larger than the corpus for BERT.

Unlike BERT, `RoBERTa` does *not* use an NSP (Next Sentence Prediction) task. Instead, `RoBERTa` uses something called dynamic masking, whereby a masked token is actually modified during the training process.

Perform an online search to find more detailed information about the list of BERT‑related models in the first part of this section.

### Surpassing Human Accuracy: deBERTa

The `deBERTa` model from Microsoft recently surpassed human accuracy, as described in the following link:

[www.microsoft.com/en-us/research/blog/microsoft-deberta-surpasses-human-performance-on-the-superglue-benchmark/](https://www.microsoft.com/en-us/research/blog/microsoft-deberta-surpasses-human-performance-on-the-superglue-benchmark/)

The architecture for this model comprises 48 Transformer layers with 1.5 billion parameters. This model has a GLUE score of 90.8, and a SuperGLUE score of 89.9, which manages to exceed the human performance score of 89.8.

Microsoft intends to integrate `DeBERTa` with the Turing natural language representation model `Turing NLRv4` (also from Microsoft). The Turing models are ubiquitous in the Microsoft ecosystem, including products such as Bing and Azure Cognitive Services.

### What is Google Smith?

The SMITH model from Google is a model for analyzing documents. In a very simplified description, the SMITH model is trained to understand passages within the context of the entire document. By contrast, BERT is trained to understand words within the context of sentences. However, the SMITH model (which outperforms BERT) supplements BERT by performing major operations that are not possible in BERT.

This concludes the BERT‑specific portion of the chapter. The next section introduces GPT, followed by sections that contain details regarding GPT-2 (and code samples) as well as GPT-3.

## Introduction to GPT

Generative pretraining (GPT), or sometimes called generative pretraining transformers, is a pretrained NLP‑based model that was developed by OpenAI. GPT is trained with unlabeled data via unsupervised pretraining (also known as self‑supervision).

GPT is based on the transformer architecture and takes advantage of the self‑attention mechanism of the transformer. There are several versions of GPT, which includes GPT‑2 (developed in 2019) and GPT‑3 (the most recent version) that was released in June, 2020. Both GPT‑2 and GPT‑3 are discussed later in this chapter.

*Lottery Ticket Hypothesis*: In every sufficiently deep neural network, there is a smaller subnetwork that can perform just as well as the whole neural network.

### Installing the Transformers Package

The installation process involves the following command:

```bash
pip3 install transformers
```

You can perform an upgrade of transformers by invoking the following command:

```bash
pip3 install -U transformers
```

However, you might encounter the following error message:

```text
ERROR: After October 2020 you may experience errors when installing or updating packages. This is because pip will change the way that it resolves dependency conflicts. We recommend you use --use-feature=2020-resolver to test your packages with the new resolver before it becomes the default. sentence-transformers 0.3.7.2 requires transformers<3.4.0,>=3.1.0, but you'll have transformers 4.1.1 which is incompatible.
```

## Working with GPT-2
