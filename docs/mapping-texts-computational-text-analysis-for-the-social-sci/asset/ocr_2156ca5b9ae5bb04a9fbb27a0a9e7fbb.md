This is the dot product between each pair of documents. Bigger dot products indicate two documents with more vocabulary overlap.

Consider the small example below. Create a corpus of three documents, each one sentence long, taken from Hughes' poem, *Dreams*. Then use `dtm_builder()` to turn this corpus into a DTM.

```
toy_corpus <- data.frame(
  id = 1:3,
  docs = c(c("hold fast to dreams"),
           c("for when dreams go"),
           c("life is a barren field"))
  )
```

```
toy_dtm <- toy_corpus |> dtm_builder(docs, id, dense = TRUE)
```

# # Document-Term Matrix

| | hold | fast | to | dreams | for | when | go | life | is | a | barren | field |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 1 | 1 | 1 | 1 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| 2 | 0 | 0 | 0 | 1 | 1 | 0 | 1 | 1 | 0 | 0 | 0 | 0 |
| 3 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 1 | 1 | 1 |

# # Term-Document Matrix

| | 1 | 2 | 3 |
|---|---|---|---|
| hold | 1 | 0 | 0 |
| fast | 1 | 0 | 0 |
| to | 1 | 0 | 0 |
| dreams | 1 | 1 | 0 |
| for | 0 | 1 | 0 |
| when | 0 | 1 | 0 |
| go | 0 | 1 | 0 |
| life | 0 | 0 | 1 |
| is | 0 | 0 | 1 |
| a | 0 | 0 | 1 |
| barren | 0 | 0 | 1 |
| field | 0 | 0 | 1 |

We'll need to multiply this DTM by the _TDM_—the *transpose* of the DTM (compare above with output in the margin).

```
toy_tdm <- t(toy_dtm)
```

Remember, matrix multiplication is different from regular multiplication. We find the dot product between the _row_ vectors of the DTM and the _column_ vectors of the TDM. Below, we take the first row of the DTM and the second column of the TDM.

```
row1 <- toy_dtm[1, ] # row vector
coll <- toy_dtm[, 2] # column vector
proj <- sum(row1 * coll) # dot product of the two vectors
```

This gives us a "1." In the document-level projection, we expect "1" where the first document and second document intersect (and vice versa since the projection is symmetric). This "1" is easy to interpret: documents 1 and 2 share a single word in common, *dreams*.

Let's find the document-level projection using `tcrossprod()`. ²

```
tcrossprod(toy_dtm)
```

| | 1 | 2 | 3 |
|---|---|---|---|
| 1 | 4 | 1 | 0 |
| 2 | 1 | 4 | 0 |
| 3 | 0 | 0 | 5 |

Sure enough, the _doc_<sub>1</sub>_,doc_<sub>2</sub> and _doc_<sub>2</sub>_,doc_<sub>1</sub> cells have a 1. We also see documents 2 and 3 are the least similar (no words in common). The diagonal is the total words in each document.