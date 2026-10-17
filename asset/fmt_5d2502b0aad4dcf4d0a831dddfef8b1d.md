

Listing 5.24 initializes the variable `sentences` as an array of sentences and then initializes the variable `nlp` as an instance of a SpaCy model. The next portion of Listing 5.23 is a for loop that is based on `nlp.pipe()`, which in this example only processes the entity recognizer (the tagger and parser recognizers have been excluded).

Launch the code in Listing 5.24 and you will see the following output:

```
=> document: We got a huge deep dish pizza from Pizzeria Uno.
=> document: Supplemented with a couple of pitchers of beer.
=> document: Then we went to the top of the Hancock building.
=> text: Hancock => label: GPE
```

As you can already see, pipelines are very flexible and convenient for processing text-based documents. More code samples and detailed information regarding spaCy pipelines is here:

[`spacy.io/usage/processing-pipelines`](https://spacy.io/usage/processing-pipelines)

## SpaCy and Word Vectors

Listing 5.25 displays the contents of `spacy_word_vectors.py` that illustrates word vectors for words.

### Listing 5.25: spacy_word_vectors.py

```python
import spacy

nlp = spacy.load('en_core_web_lg')

nlp(u'pizza').vector

doc = nlp(u'We ate deep dish pizza with wine and beer.')

print("=> doc.vector:")

print(doc.vector)

print()

# find similar pairs of tokens:

tokens = nlp(u'wine beer soda')

for token1 in tokens:

    for token2 in tokens:

        print("=> token1.text, token2.text, token1.similarity(token2):")

        print(token1.text, token2.text, token1.similarity(token2))

print()

# normalize tokens:

tokens = nlp(u'apple banana orange')

for token in tokens:

    print("=> token.text, token.has_vector, token.vector_norm, token.is_oov:")

    print(token.text, token.has_vector, token.vector_norm, token.is_oov)

print()

from scipy import spatial

cosine_similarity = lambda x, y: 1 - spatial.distance.cosine(x, y)

queen = nlp.vocab['queen'].vector

woman = nlp.vocab['woman'].vector

man = nlp.vocab['man'].vector

# find the closest vector to "man" - "woman" + "queen"

new_vector = queen - woman + man

calc_similarities = []

for word in nlp.vocab:

    # Ignore words without vectors and mixed-case words:

    if word.has_vector:

        if word.is_lower:

            if word.is_alpha:

                similarity = cosine_similarity(new_vector, word.vector)

                calc_similarities.append((word, similarity))

calc_similarities = sorted(calc_similarities, key=lambda item: -item[1])

print("=> [w[0].text for w in calc_similarities[:10]]:")

print([w[0].text for w in calc_similarities[:10]])

print()

doc = nlp(u'The quick brown fox jumped over the lazy dogs.')

print("doc:",doc)

print("doc.vector:",doc.vector)
```

