# Which yields the first review in this data:

```
> inspect(corpus[[1]])
<<PlainTextDocument>>
Metadata:  7
Content:  chars: 1681
stuff going moment mj ive started listening music watching odd documentary
watched wiz watched moonwalker maybe just want get certain insight guy
thought really cool eighties just maybe make mind whether guilty innocent
moonwalker part biography part feature film remember going see cinema
originally released subtle messages mjs feeling towards press also obvious
message drugs bad mkaybr br visually impressive course michael jackson
unless remotely like mj anyway going hate find boring may call mj egotist
consenting making movie mj fans say made fans true really nice himbr br
actual feature film bit finally starts 20 minutes excluding smooth criminal
sequence joe pesci convincing psychopathic powerful drug lord wants mj dead
bad beyond mj overheard plans nah joe pescis character ranted wanted people
know supplying drugs etc dunno maybe just hates mjs musicbr br lots ...
<truncated>
```

# First, some preprocessing:

```
corpus <- tm_map(corpus, content_transformer(tolower))
corpus <- tm_map(corpus, content_transformer(removePunctuation))
corpus <- tm_map(corpus, content_transformer(removeWords),
stopwords("english"))
```

# The next step is to create bigrams. We saw that this is important:

```
BigramTokenizer <- function(x) { unlist(lapply(ngrams(words(x), 2), paste,
collapse = " "), use.names = FALSE)}
dtm <- DocumentTermMatrix(corpus, control = list(tokenize =
BigramTokenizer()))
dtm <- removeSparseTerms(dtm, 0.995)
X <- as.data.frame(as.matrix(dtm))
X$sentiment <- df$sentiment
X$sentiment <- ifelse(X$sentiment<0.5,0,1)
```

We are now ready to apply this data to a classification model; for instance, logistic regression.