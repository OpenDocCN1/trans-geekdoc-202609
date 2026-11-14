```
cit_imm <- get_direction(anchors = anchors, wv = atn_vectors)
```

The row is the direction, labeled with the first word in the anchor list for the “positive” pole (i.e., the side *from which* we subtract) followed by “_pole.” Let’s see what words tend to occur more when citizenship is discussed versus when immigration is.

```
sim_dir <- sim2(cit_imm, atn_vectors, method = "cosine")
df_dir <- data.frame(immigrants_pole = sim_dir["immigrants_pole", ],
                    terms = colnames(sim_dir)) |>
  mutate(cit_imm_label = ifelse(
                  immigrants_pole >= 0,
                  "Immigration", "Citizenship"),
         cit_imm = abs(immigrants_pole)
)
```

```
df_dir |>
  group_by(cit_imm_label) |>
  slice_max(cit_imm, n = 30) |>
  mutate(term = fct_reorder(terms, cit_imm)) |>
  ggplot(aes(term, cit_imm, fill = cit_imm_label, label = terms)) +
  geom_col() +
  guides(fill = "none") +
  labs(x = NULL, y = "Cosine Similarity to Pole") +
  coord_flip() +
  facet_wrap(~cit_imm_label, scale = "free")
```

Figure 11.8 shows, to the extent US-based news media articles tend to adopt the public meanings of citizenship and immigration (as defined by the massive Common Crawl archive), citizenship is “local,” synonymous with “community” and “providing.” In contrast, immigration is “non-white,” colonization,” and associated with “blackness.” News media tends to present citizenship in favorable terms while perpetuating racialized stereotypes about immigrants.64

Related to the semantic direction is the *semantic centroid*. A centroid is an averaged vector.65 Semantic centroids are useful on their own if we want to know what the discursive context of some domain of interest is, rather than the context of that domain *relative* to another (which is what we get with directions). For example, we may want to know the general context in which “immigration” is discussed — not *relative* to how “citizenship” is discussed. Nelson (2021b), for instance, uses semantic centroids in her analysis of the *intersection* of social categories of people across institutional spheres in first-person narratives in the 19th-century US South, and Lix and colleagues (2022) also used centroids to study how discursive diversity impacts the work performance of remote software development teams.

Let’s use `get_centroid()` to see the terms most similar to an “immigration” centroid.66

64 For research on the association between Blackness and immigration in US discourse, see Mora and Paschel (2020).

65 This is what we’d get with the pooled method for vector offsetting but before taking the difference between our two average vectors. This is also one strategy for creating sentence embeddings.

66 The centroid is labeled with the first word in the anchor list followed by “_centroid.”