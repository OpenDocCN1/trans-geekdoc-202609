# FGUGChain: Blockchain Application Framework

Here, the encryption carried out is double encryption, i.e., per wire complex encryption call is made twice. This creates a bottleneck on efficiency and makes the protocol impractical. The step-by-step working of GC construction and evaluation is shown with illustrated example by Innocent and Sangeeta (2014a; 2014b).

# APPENDIX 9.2

# AND CIRCUIT IN SCD

For an example to show the SCD circuit construction using NOR gates, AND circuit is used, which is nothing but the simple AND gate function giving output 1 when both A and B are I. Figure 9.5 shows the AND circuit designed only with NOR gates, and is suitable for representation in SCD format. The truth table for the AND circuit is shown in Table 9.3.

SCD format of any function can be represented using a 7-tuple, $f_{old}=(n,m,q,A,B,G,O)$. Name and meaning of parameters in it and their respected values for AND circuit shown in Figure 9.5 are given next:

+   Number of inputs, n=2
Number of outputs, m=1
Number of gates, q=3
First input wires to the gates, A[]={1, 2, 3}
Second input wires to the gates, B[]={1, 2, 4}
Gate type, G=1
Output wire, O[]={5}

![](bbox=[0.198, 0.542, 0.802, 0.672])

FIGURE 9.5 AND circuit generated only with NOR gates, and suitable for SCD format.

# TABLE 9.3
Truth Table of AND Circuit

| A | B | C |
|---|---|--|
| 0 | 0 | 0 |
| 0 | 1 | 0 |
| 1 | 0 | 0 |
| 1 | 1 | 1 |