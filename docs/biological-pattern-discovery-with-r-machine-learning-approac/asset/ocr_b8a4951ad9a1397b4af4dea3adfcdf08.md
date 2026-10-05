Biological Pattern Discovery with R

LGPSSKQT
| | | |
LGPS--QT

# 7.2.1.2 The alignment gap

The second issue of sequence homology alignment alignment is the alignment gap. An alignment algorithm has to satisfy the following requirements. Aligning two sequences without inserted a gap may not work properly, especially when an indel event has happened. This is because two sequences definitely have different lengths when an indel event has happened. For instance, the evolution of the ancestor sequence LGPSSKQT to the descendant sequence LGPSQT has resulted in sequences with different lengths. Without introducing gaps, aligning these two sequences will not generate a meaningful alignment. Of course, aligning two sequences with too many gaps is also unacceptable. Therefore, an alignment should maximise the number of the aligned pairs and minimise the number of the inserted gaps. A gap penalty, which can quantify the impact of gap insertion on an alignment performance, which therefore been introduced for this purpose in almost every alignment algorithm.

# 7.2.1.3 The alignment strategy

The third issue of sequence homology alignment is the alignment strategy. There are mainly two strategies, i.e., the global homology alignment and the local homology alignment [Polyanovsky, et al., 2011; Pollard, et al., 2004]. A global homology alignment process employs all the residues from two sequences to generate an alignment model. The alignment shown below is such a global alignment,

LGPSSKGTKGGS-SRIWDN
| | | | |
LN-ITKQAGGAIMRLGDA

A local homology alignment may align the above two sequences by employing only subsets of residues from two sequences. One possibility for aligning two above sequences is shown below, where only five pairs