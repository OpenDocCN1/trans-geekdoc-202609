```
tm_map just maps some function to every document in the corpus
docs <- tm_map(docs, content_transformer(tolower)) ## make lowercase
docs <- tm_map(docs, content_transformer(removeNumbers)) ## remove numbers
docs <- tm_map(docs, content_transformer(removePunctuation)) ## drop punctuation
docs <- tm_map(docs, content_transformer(removeWords), stopwords("SMART")) # stopwords
docs <- tm_map(docs, content_transformer(stripWhitespace)) ## clean whitespace
```

This is a more heavy-handed version of the cleaning and pruning in my Python snippet from Figure 8.1; for example, the SMART list of stop words includes many I would normally not drop:

```
head(stopwords("SMART"))
[1] "a" "s" "able" "about" "above" "according"
```

With only 12 documents, we need to cut liberally to keep the dimension low.

Once we have this clean text, we can convert from words to counts of words and create a document-term-matrix (DTM) X that has a row for each document and a column for each word. Element $x_{ij}$ is the count for word $j$ in document $i$.

```
dtm <- DocumentTermMatrix(docs)
dtm
<DocumentTermMatrix (documents: 11, terms: 4009)>
Non-/sparse entries: 7062/37037
Sparsity		: 84%
Maximal term length: 39
Weighting		: term frequency (tf)
```

This matrix contains more than 4000 terms (columns). As a final pruning step, we remove terms that have a zero count in more than 75% of the documents (since we have only 11, this will remove words that don't occur in at least three lectures). This leaves us with a total of around 700 terms.