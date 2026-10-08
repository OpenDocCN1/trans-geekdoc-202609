# Extraction of Medical Entities Using a Matrix-Based Pattern-Matching Method

![](bbox=[0.169, 0.093, 0.811, 0.362])

**FIGURE 8.3** Comparison of performance of proposed method for treatment, problem, and test concepts based on precision and recall.

# # Precision

![](bbox=[0.206, 0.497, 0.789, 0.689])

**FIGURE 8.4** Comparison between precision of different text classification methods.

After conducting error analysis on the results, it is observed that improvement in recall is possible to some extent. A few concepts are missing because of the inaccurate boundary identification of sequences of entities. For frequent pattern generation, the minimum threshold value is 2 and patterns those are having frequency 2 or more than 2, they have considered. But in this system, only the POS feature was focused. In future work, the same system could be developed by using more features, like word, n-gram, semantics of words, lemma, prefix, and suffix.

Boundary identification of multword clinical concepts is the big issue [29] which is principally found in the problem and treatment concepts because the gold-standard