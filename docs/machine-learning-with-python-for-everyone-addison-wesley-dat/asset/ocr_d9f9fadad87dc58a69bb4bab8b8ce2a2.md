In [2]:

```
docs = ["the cat in the hat",
    "the cow jumped over the moon",
    "the cat mooed and the cow meowed",
    "the cat said to the cow cow you are not a cat"]
```

To create our features of interest, we need to record all of the unique words that occur in the entire corpus. Corpus is a term for the entire group of documents we are considering.

In [3]:

```
vocabulary = set(" ".join(docs).split())
```

We can remove some words that are unlikely to help us. These throwaway words are called stop words. After we remove them, we are left with our vocabulary of words that show up in the corpus.

In [4]:

```
common_words = set(['a', 'to', 'the', 'in', 'and', 'are'])
vocabulary = vocabulary - common_words
print(textwrap.fill(str(vocabulary)))
```

{'cow', 'not', 'cat', 'moon', 'jumped', 'meowed', 'said', 'mooed', 'you', 'over', 'hat'}

# 14.1.1.1 Binary Bags of Words

With our vocabulary in place, some quick MacGyver-ing with Python gets us a simple yes/no table of words in documents. The key test is the w in d that asks if a word is in a document.

In [5]:

```
# {k:v for k in lst} creates a dictionary from keys:values
# it is called a "dictionary comprehension"
doc_contains = [{w:(w in d) for w in vocabulary} for d in docs]
display(pd.DataFrame(doc_contains))
```

|   | cat | cow | hat | jumped | meowed | mooed | moon | not | over | said | you |
|---|-----|-----|-----|--------|--------|-------|------|-----|------|------|-----|
| 0 | True | False | True | False | False | False | False | False | False | False | False |
| 1 | False | True | False | True | False | False | True | False | True | False | False |
| 2 | True | True | False | False | True | True | False | False | False | False | False |
| 3 | True | True | False | False | False | False | False | True | False | True | True |