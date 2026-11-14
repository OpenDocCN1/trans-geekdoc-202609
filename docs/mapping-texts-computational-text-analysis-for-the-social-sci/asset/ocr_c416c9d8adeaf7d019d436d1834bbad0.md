```
dtm <- df_trek |> mutate(doc_id = rownames(df_trek)) |> dtm_builder(lemma, doc_id) |> dtm_stoplist(stop_list = stoplist("snowball2014"))
```

Look at the first few columns of our DTM.

```
dtm[1:5, 1:7]
```

```
aft shield buckle transfer auxiliary power go
1 1 1 . . . . .
2 . 1 1 1 1 1 .
3 1 1 . . . . 1
4 . . . . . . .
5 . . . . . . .
```

The dictionary lookup method has a limitation: How to deal with homonymy? Consider the word “saw.” This word could be a past-tense verb (“I saw an airplane fly by.”), a verb indicating “to cut” (“I had to saw the plank of wood in half.”), or a noun (“I had to buy a saw for the project.”). Ideally, lemmatizers can distinguish between homonyms. For this, some lemmatizers “tag” each token with its predicted part of speech.36 The lemma for the token is assigned conditional on that token’s part of speech.

The TreeTagger model does this (Schmid 2013). We can also use udpipe . We’ll talk more about udpipe in the next chapter on non-English part-of-speech tagging; for now, though, we’ll quickly illustrate lemmatizing with parts of speech using this package. First, we’ll download an English language model37 that allows us to tag the parts of speech and then assign lemmas using those tags.

```
eng <- udpipe_download_model(language = "english-gum")
ud_eng <- udpipe_load_model(eng$file_model)
```

Now let's do some tagging. We’ll first create a small corpus using the “saw” homonym issue. We’ll then use udpipe_annotate() to tag the documents and assign the lemmas.

```
docs <- c(
  "I saw an airplane,",
  "I had to saw the wood",
  "I have a saw for work"
)
udpipe_annotate(x = docs, object = ud_eng) |>
  as.data.frame() |>
  select(doc_id, token, lemma, upos)
```

And we'll get the following output (we’re printing only the document ID, token, lemma, and part of speech tag here).

```
doc_id token lemma upos
1 doc1 I I PRON
2 doc1 saw see VERB
```