```
3 doc1 an a DET
4 doc1 airplane airplane NOUN
5 doc2 I I PRON
6 doc2 had have VERB
7 doc2 to to PART
8 doc2 saw saw VERB
9 doc2 the the DET
10 doc2 wood wood NOUN
11 doc3 I I PRON
12 doc3 have have VERB
13 doc3 a a DET
14 doc3 saw saw NOUN
15 doc3 for for ADP
16 doc3 work work NOUN
```

The first instance of “saw” was tagged as a verb and lemmatized to “see.” The second instance of “saw” was also tagged as a verb but lemmatized to “saw.” The final “saw” was tagged as a noun and left alone. This allows us to distinguish between homonyms, which could be important for some research questions.38

38 If, for example, we’re exploring the meaning of work in diaries of 19th-century US homesteaders, we’ll want to distinguish whether the farmer labors to sow wheat or the sow bears piglets in labor.

We can incorporate the udpipe method for lemmatizing in our workflow with the following. For speed, we’ll only use the first 20 lines from our Star Trek corpus. Using as_tibble() to tidy the output and count() we’ll create a token-count “tripletlist” dataframe. Notice we also filter out any rows with lemmas matching [[:punct:]]+ (output in margin).

```
df_samp <- df_trek |>
head(n = 20) |>
mutate(lemma = tolower(line),
lemma = gsub("[[:digit:]]+", " ", lemma))
```

```
df_trip <- udpipe_annotate(
x = df_samp$lemma,
object = ud_eng,
as_tibble() |>
select(doc_id, lemma) |>
filter(!grepl("[[:punct:]]+", lemma)) |>
count(doc_id, lemma)
```

| doc_id | lemma | n |
|---|---|---|
| doc1 | aft | 1 |
| doc1 | buckl | 1 |
| doc1 | shield | 1 |
| doc10 | command | 1 |
| doc10 | course | 1 |
| doc10 | enter | 1 |
| doc10 | five | 2 |
| doc10 | mark | 1 |
| doc10 | my | 1 |
| doc10 | on | 1 |

We can then convert this tripletlist to a DTM with tidytext, but substituting in term = lemma in place of term = word (since the word column is called “lemma” instead of “word”).

```
dtm <- df_trip |>
cast_dfm(
document = doc_id,
term = lemma,
value = n
)

dtm[1:3, 1:7]
```

| docs | aft | buckl | shield | command | course | enter | five |
|---|---|---|---|---|---|---|---|
| doc1 | 1 | 1 | 1 | 1 | 0 | 0 | 0 |
| doc10 | 0 | 0 | 0 | 1 | 1 | 1 | 2 |
| doc11 | 0 | 0 | 1 | 0 | 0 | 0 | 0 |