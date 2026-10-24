![](bbox=[0.28, 0.12, 0.62, 0.35])

**FIGURE 5.5**
A high-dimensional data set may contain a small set of colossal patterns but exponentially many midsize patterns.

![](bbox=[0.27, 0.44, 0.63, 0.67])

**FIGURE 5.6**
Pattern tree traversal: Candidates are taken from a pool of patterns, which results in shortcuts through pattern space to the colossal patterns.

Thus Pattern-Fusion has the capability to identify good merging candidates, which are the patterns that share some subpatterns and have some similar support sets. This does help the search leaps through pattern space more directly toward colossal patterns.

It has been theoretically shown that Pattern-Fusion leads to a good approximation of colossal patterns (see [ZYH+07]). The method was tested on synthetic and real data sets constructed from program tracing data and microarray data. Experiments show that the method can find most of the colossal patterns with high efficiency.