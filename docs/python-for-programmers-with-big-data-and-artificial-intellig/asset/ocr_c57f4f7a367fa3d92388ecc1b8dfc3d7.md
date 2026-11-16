# # 11.2.12 Getting Definitions, Synonyms and Antonyms from WordNet

WordNet 9 is a word database created by Princeton University. The TextBlob library uses the NLTK library's WordNet interface, enabling you to look up word definitions, and get synonyms and antonyms. For more information, check out the NLTK WordNet interface documentation at:

9 https://wordnet.princeton.edu/.

https://www.nltk.org/api/nltk.corpus.reader.html#module-nltk.corpus.reader.wordnet

# ## Getting Definitions

First, let's create a Word:

lick here to view code image

```
```python
In [1]: from textblob import Word

In [2]: happy = Word('happy')
```
```

The Word class's definitions property returns a list of all the word's definitions in the WordNet database:

lick here to view code image

```
```python
In [3]: happy.definitions
Out[3]:
['enjoying or showing or marked by joy or pleasure',
'marked by good fortune',
'eagerly disposed to act or to be of service',
'well expressed and to the point']
```
```

The database does not necessarily contain every dictionary definition of a given word. There's also a define method that enables you to pass a part of speech as an argument so you can get definitions matching only that part of speech.

# ## Getting Synonyms

You can get a Word's synsets—that is, its sets of synonyms—via the synsets property. The result is a list of Synset objects:

```
```python
In [4]: happy.synsets
Out[4]:
[Synset('happy.a.01'),
Synset('felicitous.s.02'),
Synset('glad.s.02'),
Synset('happy.s.04')]
```
```

Each Synset represents a group of synonyms. In the notation happy.a.01: