```
c(get_stoplist("snowball2014"), "s")) |>
arrange(desc(human)) |>
head(n = 6) |>
print()
}
```

We could then probe the embedding spaces further and/or do close reading of each series’ transcripts to see how these terms contextualize the subject of humanness.

# Semantic Directions and Semantic Centroids

Let’s discuss two ways of conceptualizing meaningful dimensions in embedding spaces: **semantic directions** and **semantic centroids**.

54 The “and/or” language here is intentional. As long as domain-specific words reside in the same portions of the embedding space, their coordinates will be similar. This also means that words need not *literally* co-occur to be close. Even if “pie” and “cake” never co-occur, they do share context words like “sweet,” and “fruit.”

A direction is a path on which something moves or sits. This is analogous to discursive bias: given two semantic “poles,” we can place a document along the line between those poles—and the closer it is to one pole, the more that document is “biased toward” that pole relative to the other one. Our earlier gender bias walk-through involved a *semantic direction*: the closer a word was (using cosine similarity) to the “boy” end of a gender direction, the more that word is used in semantic contexts where “boy” and/or other “boy-related” words tended to be used as opposed to “girl” and/or other “girl-related” words.54 Semantic directions are, essentially, one-dimensional “subspaces” within the higher-dimensional embedding space.

Semantic directions—analyzing them and how documents and document producers engage with them—is a popular social-scientific use of word embeddings. Kozlowski, Taddy, and Evans (2019) used directions to analyze how meanings of social class shifted over the 20th century. Similarly, Arseniev-Koehler and Foster (2020) used directions to examine the gendered, moral, health-centered, and socioeconomic biases in how *The New York Times* discusses obesity. We (Stoltz and Taylor 2021) analyzed how the racial, moral, and affluence dimensions of immigration vs. citizenship discourse evolved from 1880 to 2000 in American English.

55 This corpus grows every so often.

Let’s get some directions. We’ll switch up the data, though, and now move over to a small random sample of 3,800 articles from the All the News (ATN) corpus (Thompson 2020) that mention either “immigrant” or “immigration” at least once. As of this writing,55 this is a corpus of 2.7 million news articles from 27 different US-based news organizations. We sampled from an earlier, smaller version of this corpus that we used in Stoltz and Taylor (2021), which consists of 204,135 articles across 18 news organizations.