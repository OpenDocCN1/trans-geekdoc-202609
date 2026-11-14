We have more assurances with this last DTM that homonyms have been accurately lemmatized.

# Lemmatizing in French

udpipe can lemmatize many different languages.39 Let's lemmatize some paragraphs from Proust's Du côté de chez Swann using a corpus from proustr , a package with seven books by the late-19th- and early-20th-century French novelist, Marcel Proust. Let's look at one paragraph.

39 Currently, udpipe has 65 language models. To see what is available, run help(udpipe_download_model)

```
```
data("ducotedechezswann", package = "proustr")
ducotedechezswann$text[60]
```
```

Next, we'll need to download a French-language model.

```
```
fre <- udpipe_download_model(language = "french-gsd")
ud_fre <- udpipe_Load_model(fre$file_model)
```
```

Now, we can lemmatize the text. Let's go with the 60th paragraph.

```
```
ducotedechezswann$text[60] |> udpipe_annotate(object = ud_fre) |> as_tibble() |> select(doc_id, token, lemma, upos)
```
```

> —Françoise, imaginez-vous que Mme Goupil est passée plus d’un quart d’heure en retard pour aller chercher sa sœur ; pour peu qu’elle s’attarde sur son chemin cela ne me surprendrait point qu’elle arrive après l’élévation.”

```
```
doc_id token lemma upos
1 doc1 — PUNCT
2 docl Françoise Françoise PROPN
3 docl , , PUNCT
4 docl imaginer, imaginer VERB
5 docl -vous vous PRON
..
..
..
40 doc1 elle il PRON
41 doc1 arrive arriver VERB
42 doc1 après après ADP
43 docl l' le DET
44 docl élévation élévation NOUN
45 docl . . PUNCT
```
```

# WRANGLING WORKFLOW

Table 7.6 lists some common text wrangling decisions. Further, below is an overview of a typical text preparation script we might use. These steps are not what should always be taken; rather, we’ll use variations on these scripts, testing the effects of different decisions on our analyses. Furthermore, whether we take these steps ought to be reported in our final analysis—as a bare minimum.