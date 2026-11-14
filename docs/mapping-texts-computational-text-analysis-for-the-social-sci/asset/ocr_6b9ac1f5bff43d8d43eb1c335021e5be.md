In all, this topic does have a “future of education” element to it—but it seems more general than that. Given the focus on investing in childrens’ futures, perhaps “securing our children’s future” is a better interpretation of the topic.

Let’s look at one more document to see if we overspecified our interpretation.31 We’ll use the speech with another high loading: Bush’s 2005 speech.

```
df_sotu |> filter(doc_id == "Bush_2005") |> select(text)
```

Our generation has been blessed - by the expansion of opportunity, by advances in medicine, and by the security purchased by our parents’ sacrifice ...

...Over the next several months, on issue after issue, let us do what Americans have always done, and build a better world for our children and grandchildren.

It does seem like this is a “securing our children’s future” topic. Recall that LSA attempts to explain the variation in our DTM using the fewest possible dimensions. This is a spatial interpretation of “variation,” built on the vector space approach to meaning.

LSA has a long history as a form of topic modeling. For most researchers, though, LSA is probably not what they have in mind with topic modeling. The reason for this is that in the early 2000s, a new form of topic modeling—one that explicitly defined itself as such—emerged, known as latent Dirichlet allocation, or LDA for short (Blei et al. 2003). Let’s explore that now.

# # Topic Modeling with LDA

LDA emerged, in part, because of shortcomings in LSA. For instance, with LSA, nothing is preventing negative values in the singular vectors (for either the terms or documents). Interpreting the singular vectors in an absolute sense is a little tricky.32 They define a single point for the term/document in the latent space. Larger values indicate that the term/document loads higher on it and is therefore consequential for determining the topic’s meaning—but any coordinate on its own is uninterpretable.33

Many alternatives to LSA have been proposed to deal with these issues, including non-negative matrix factorization (Lee and Seung 1999) and probabilistic LSA (Hofmann 2001), but LDA is the one that stuck—at least in the social sciences.34 We’ll therefore focus our attention here.

31 In practice, we’ll want to read more documents per topic to have a robust interpretation of what themes the dimension is picking up on.

32 For instance, the topic loading for the term “security” on topic #9 (our “securing our children’s future” topic) is -0.254 and the loading for the term “challenge” on that same topic is 0.221. So, -0.254 and 0.221 are what, exactly?

33 Some suggest that SVD doesn’t perform well for certain tasks, such as finding word similarities (Gamallo and Bordag 2011).

34 See, for example, the 2013 special issue of the journal Poetics (Mohr and Bogdanov 2013).