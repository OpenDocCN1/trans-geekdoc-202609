weighted. The entry tells us more than just the presence or absence of a tie. It tells us how many times a term appears in a document. Second, the row and column entities are different—we have documents *and* terms, not just family names in both rows and columns. In network terms, a matrix with different row and column entities is called a *two-mode matrix*. The graph equivalent is called a *bipartite graph*.31 If we put these two things together, then we can call our DTM a *weighted bipartite graph*. The graph is visualized in Figure 12.6.

31 One-mode networks—such as the Florentine family network—are called *unipartite* graphs. *Bipartite* graphs are also called affiliation networks, usually when the entities are people and organizations.

```
set.seed(37201)
dtm.ars [>]
 ggraph(layout = "fr") +
 geom_edge_link(color = "gray50", alpha = .2) +
 geom_node_point(aes(fill = type), size = 3,
 shape = 21, color = "black") +
 scale_fill_discrete(labels = c("Article Abstract", "Term"))
```

# Figure 12.6: ARS Corpus as a Bipartite Graph.

![](bbox=[0.34, 0.43, 0.72, 0.68])

● Article Abstract ○ Term

The dark nodes in the graph are the article abstracts and the light nodes are the terms. The network has a hub-and-spoke structure. All term nodes seem to radiate out from the article nodes. None of those term nodes connect to—that is, are "adjacent to"—other term nodes.

How do we go about finding patterns in bipartite graph like this? Generally, we proceed in three ways. First, we could ignore the bipartite structure and use standard unipartite network analysis.32 Second, we could use newer tools and methods designed to work specifically on two-mode relational data. Third, we could convert the weighted bipartite

32 This is probably not a good idea for reasons beyond our scope.