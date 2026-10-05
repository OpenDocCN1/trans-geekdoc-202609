# Whole Genome Pattern Discovery

```
CCGAATG
|| | |
CCAATT-
```

The above alignment has three matches in addition to four mismatches, i.e., the first residue of sequence $x$ (which is C) is aligned with the first residue of sequence $y$ (which is C as well), the second residue of sequence $x$ (which is C as well) and the fourth residue of sequence $x$ (which is A) is aligned with the fourth residue of sequence $y$ (which is A as well),

The other alignment between these two sequences may show a different alignment format as shown below, where there are four matches and three mismatches,

```
CCGAATG
|| | |
-CCAATT
```

It can be seen that there will be many possible alignments for any two sequences. Each of these alignments will have a different alignment pattern as well as an alignment statistic such the number of matches as well as the number of mismatches plus the number of inserted gaps. Suppose the number of matches and the number of mismatches as well as the number of inserted gaps are incorporated into a unique alignment statistic. Among all possible alignments, if they can be exhausted, there must be one (or more than one) homology alignment which has the optimised alignment statistic. Therefore, a homology alignment process is an optimisation process. It is a process of discovering the best homology alignment with an optimised alignment statistic.

No doubt, an exhaustive search is impossible if sequences are significantly long. Therefore the best approach is to employ a heuristic optimisation process. One of the best approaches for this kind of optimisation process is the dynamic programming algorithm [Kirk, 1970; Alser, et al., 2019; Chen, et al., 2019]. The dynamic programming algorithm is well-designed for most combination optimisation programming.

A combination optimisation problem is such a process in which an optimised combination is searched based on the limited number of components. A decision is made on a course to discover the best or the optimal solution among many sequential combinations of the components.