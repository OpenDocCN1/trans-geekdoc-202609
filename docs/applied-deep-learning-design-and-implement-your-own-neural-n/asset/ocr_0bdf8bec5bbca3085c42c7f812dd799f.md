6. ReLU in any neural network never saturates.

a. False	b. True

# ## Answers

| 1 | c |
|---|---|
| 2 | a |
| 3 | a |
| 4 | b |
| 5 | c |
| 6 | a |

# ## Hands on

# ### 1. RNN code

Creating training data matrices

```
Vocab size = 8000
unknown = &quot;UNKNOWN_TOKEN&quot;;
sentence_start = &quot;SENTENCE_START&quot;;
sentence_end = &quot;SENTENCE_END&quot;;
read = csv.reader(f, skipinitialspace=True)
reader.next()
# Split full comments into sentences
sentences = itertools.chain(*[nltk.sent_tokenize(x[0].decode('utf-8').lower()) for x in reader])
# Append SENTENCE_START and SENTENCE_END
sentences = [&quot;%s %s %s&quot; % (sentence_start_token, x, sentence_end_token) for x in sentences]
print &quot;Parsed %d sentences.&quot; % (len(sentences)))
token_sentences = [nltk.word_tokenize(sent) for sent in sentences]
```

```
# Count the word frequencies
word_freq = nltk.FreqDist(itertools.chain(*tokenized_sentences))
print &quot;Found %d unique words tokens.&quot; % len(word_freq.items())
```