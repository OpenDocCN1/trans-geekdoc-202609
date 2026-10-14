
$$\\begin{array}{l} {\\widetilde{F} + \\widetilde{G} = {(m\\_{1} + n\\_{1},f\\_{1} + h\\_{1},f\\_{2} + h\\_{2})}\_{LR}} \\\\ {\\widetilde{F} - \\widetilde{G} = {(m\\_{1} - n\\_{1},f\\_{1} + h\\_{2},f\\_{2} + h\\_{1})}\_{LR}} \\\\ {\\widetilde{F}.\\widetilde{G} = (m\\_{1}n\\_{1},m\\_{1}h\\_{1} + n\\_{1}f\\_{1} - f\\_{1}h\\_{1},m\\_{1}h\\_{2} + n\\_{1}f\\_{2} +} \\\\ {f\\_{2}h\\_{2})\\_{LR}} \\\\ {\\frac{\\overset{\\rightarrow}{F}}{G} = (\\frac{m\\_{1}}{n\\_{1}},\\frac{m\\_{1}h\\_{2}}{n\\_{1}(n\\_{1} + h\\_{2})} + \\frac{f\\_{1}}{n\\_{1}} - \\frac{f\\_{1}h\\_{2}}{n\\_{1}(n\\_{1} + h\\_{2})},\\frac{m\\_{1}h\\_{1}}{n\\_{1}(n\\_{1} - h\\_{1})} + \\frac{f\\_{2}}{n\\_{1}} +} \\\\ {f\\_{2}h\\_{1}}{n\\_{1}(n\\_{1} - h\\_{1})})\\_{LR}} \\\\ \\end{array}$$  

### Notations

*`m̃`*[ij]**\=** fuzzy low and high priority arriving customers, i = 1,2 & j = L, H

*`λ̃`*[ij]**\=** fuzzy Priority input rate, i = 1,2 & j = L, H

*`λ̃′`*[i] = fuzzy general arrivals, i = 1,2

*`µ̃`*[ij]**\=** fuzzy cost of service for low and high priority visitors, i = 1,2 & j = L, H

*`µ̃`*[i] = fuzzy service rate at parallel subsystems

*`α̃`*[ij]**\=** fuzzy probabilities from i’th server to j’th server

*`L̃`* = fuzzy queue length of the system

## III. Stochastic mathematical modeling

The proposed model consists of biserial and parallel severs C[1] and C[2] both linked to server C[3] . The sub-systems C[11] and C[12] are in bi-series relation and C[21] and C[22] are parallel at server C[1] and C[2] respectively. Both type of customers with Poisson Mean arrivals *λ*[1]*[L]*, *λ*[1]*[H]*, *λ*[2]*[L]*, *λ*[1]*[H]*, *λ′*[1], *λ′*[2], arrived at subsystems C[11,] C[12,] C[21] and C[22] for availing services with probable conditions α[12] + α[15] = 1, α[21] + α[25] = 1, α[35] = 1, α[45] = 1, where priority is taken only at entry level biserial subsystems C[11] and C[12.] After, that customer move for next phase service at C[3] and finally leave the system ([Figure 10.1](#ch10.xhtml#fig10_1)).

![Figure 10.1 Priority queue network model](images/fig10_1_C.jpg)

[Figure 10.1 Priority queue network model](#ch10.xhtml#R_fig10_1)

Let us, define a probability function P[*m*[1]*[L]*,*m*[1]*[H]*,*m*[2]*[L]*,*m*[2]*[H]*,*m*[2],*m*[3],[*m*[5]]], (*t*) at any time t for the arrivals *m*[1]*[L]*, *m*[1]*[H]*, *m*[2]*[L]*, *m*[2]*[H]*, *m*[2], *m*[3], from outside in the system. The model’s continuous solution is derived from the solutions of differential equations by using GF and PGF solution methodology as

$$\\begin{array}{l} {\\text{H}(\\text{Z}\\_1,\\text{Z}\\_2,\\text{Z}\\_3,\\text{Z}\\_4,\\text{Z}\\_5,\\text{Z}\\_6,\\text{Z}\\_7) =} \\\\ {G\_{1}\\left\\lbrack {\\mu\_{1H}\\left( {1 - \\frac{\\alpha\_{12}Z\\_4}{Z\\_2} - \\frac{\\alpha\_{15}Z\\_7}{Z\\_2}} \\right) - \\mu\_{1L}\\left( {1 - \\frac{\\alpha\_{12}Z\\_3}{Z\\_1} - \\frac{\\alpha\_{15}Z\\_7}{Z\\_1}} \\right)} \\right\\rbrack + \\mu\_{2}^{\\prime}\\left( {1 - \\frac{\\alpha\_{45}Z\\_7}{Z\\_6}} \\right)G\_{4} +} \\\\ {G\_{2}\\left\\lbrack {\\mu\_{2H}\\left( {1 - \\frac{\\alpha\_{21}Z\\_2}{Z\\_4} - \\frac{\\alpha\_{25}Z\\_7}{Z\\_4}} \\right) - \\mu\_{2L}\\left( {1 - \\frac{\\alpha\_{21}Z\\_1}{Z\\_3} - \\frac{\\alpha\_{25}Z\\_7}{Z\\_3}} \\right)} \\right\\rbrack + \\mu\_{1}^{\\prime}\\left( {1 - \\frac{\\alpha\_{35}Z\\_7}{Z\\_5}} \\right)G\_{3} + \\mu\_{3}\\left( {1 - \\frac{1}{Z\\_7}} \\right)G\_{5}} \\\\ \\frac{+ \\mu\_{1L}\\left( {1 - \\frac{\\alpha\_{12}Z\\_3}{Z\\_1} - \\frac{\\alpha\_{15}Z\\_7}{Z\\_1}} \\right)G\_{6} + \\mu\_{2L}\\left( {1 - \\frac{\\alpha\_{21}Z\\_1}{Z\\_3} - \\frac{\\alpha\_{25}Z\\_7}{Z\\_3}} \\right)G\_{7}}{\\lambda\_{1L}(1 - Z\\_1) + \\lambda\_{1H}(1 - Z\\_2) + \\lambda\_{2L}(1 - Z\\_3) + \\lambda\_{2H}(1 - Z\\_4) + \\mu\_{1H}\\left( {1 - \\frac{\\alpha\_{12}Z\\_4}{Z\\_2} - \\frac{\\alpha\_{15}Z\\_7}{Z\\_2}} \\right) + \\mu\_{3}\\left( {1 - \\frac{1}{Z\\_7}} \\right)} \\\\ + \\lambda\_{1}^{\\prime}(1 - Z\\_5) + \\lambda\_{2}^{\\prime}(1 - Z\\_6) + \\mu\_{2H}\\left( {1 - \\frac{\\alpha\_{21}Z\\_2}{Z\\_4} - \\frac{\\alpha\_{25}Z\\_7}{Z\\_4}} \\right) + \\mu\_{1}^{\\prime}\\left( {1 - \\frac{\\alpha\_{35}Z\\_7}{Z\\_5}} \\right) + \\mu\_{2}^{\\prime}\\left( {1 - \\frac{\\alpha\_{45}Z\\_7}{Z\\_6}} \\right)} \\\\ \\end{array}$$  

To solve the above equation, by applying L’ hospital rule with conditions *| Z*[1] *|=| Z*[2] *|=| Z*[3] *|=| Z*[4] *|=| Z*[5] *|=| Z*[6] *|=| Z*[7] *|=1* and H(Z[1], Z[2], Z[3], Z[4], Z[5], Z[6], Z[7] ) = 1. And find the utilization factors at different servers in stochastic environment

$$\\begin{array}{l} {\\gamma\_{1} = \\frac{\\lambda\_{1\\text{H}} + \\lambda\_{2\\text{H}}\\alpha\_{21}}{\\mu\_{1\\text{H}}(1 - \\alpha\_{12}\\alpha\_{21})}} \\\\ {\\gamma\_{2} = \\frac{\\lambda\_{2\\text{H}} + \\lambda\_{1\\text{H}}\\alpha\_{12}}{\\mu\_{2\\text{H}}(1 - \\alpha\_{12}\\alpha\_{21})}} \\\\ {\\gamma\_{3} = \\frac{\\lambda\_{1}^{\\prime}}{\\mu\_{1}^{\\prime}\\alpha\_{35}}} \\\\ {\\gamma\_{4} = \\frac{\\lambda\_{2}^{\\prime}}{\\mu\_{2}^{\\prime}\\alpha\_{45}}} \\\\ \\end{array}$$  

$$\\begin{array}{l} {({\\overline{\\lambda}}\\_1^{\\prime} + \\lambda\_{2}^{\\prime})(1 - \\alpha\_{12}\\alpha\_{21}) + \\alpha\_{15}\\lbrack(\\lambda\_{1\\text{H}} + \\lambda\_{2\\text{H}}\\alpha\_{21}) + (\\lambda\_{1\\text{L}} + \\lambda\_{2\\text{L}}\\alpha\_{21})\\rbrack} \\\\ {\\gamma\_{5} = \\frac{+ \\alpha\_{25}\\lbrack(\\lambda\_{2\\text{H}} + \\lambda\_{1\\text{H}}\\alpha\_{12}) + (\\lambda\_{2\\text{L}} + \\lambda\_{1\\text{L}}\\alpha\_{12})\\rbrack}{\\mu\_{3}(1 - \\alpha\_{12}\\alpha\_{21})}} \\\\ {\\gamma\_{6} = \\frac{\\mu\_{1\\text{L}}(\\lambda\_{1\\text{H}} + \\lambda\_{2\\text{H}}\\alpha\_{21}) + \\mu\_{1\\text{H}}(\\lambda\_{1\\text{L}} + \\lambda\_{2\\text{L}}\\alpha\_{21})}{\\mu\_{1\\text{L}}\\mu\_{1\\text{H}}(1 - \\alpha\_{12}\\alpha\_{21})}} \\\\ {\\gamma\_{7} = \\frac{\\mu\_{2L}(\\lambda\_{2H} + \\lambda\_{1H}\\alpha\_{12}) + \\mu\_{2H}(\\lambda\_{2L} + \\lambda\_{1L}\\alpha\_{12})}{\\mu\_{2L}\\mu\_{2H}(1 - \\alpha\_{12}\\alpha\_{21})}} \\\\ \\end{array}$$  

Time- independent solution of the proposed model is that

$$\\begin{array}{l} {P\_{m\_{1L},m\_{1H},m\_{2L},m\_{2H},m\_{2},m\_{3,m\_{5}}} =} \\\\ {= \\gamma\_{1}^{m\_{1H}}\\gamma\_{2}^{m\_{2H}}\\gamma\_{3}^{m\_{2}}\\gamma\_{4}^{m\_{3}}\\gamma\_{5}^{m\_{5}}\\gamma\_{6}^{m\_{1L}}\\gamma\_{7}^{m\_{2L}}(1 - \\gamma\_{1})(1 - \\gamma\_{2})(1 -} \\\\ {\\gamma\_{3})(1 - \\gamma\_{4})(1 - \\gamma\_{5})(1 - \\gamma\_{6})(1 - \\gamma\_{7})} \\\\ \\end{array}$$  

With the conditions exist if γ[1], γ[2], γ[3], γ[4], γ[5], γ[6], γ[7] ≤ 1

## IV. Numerical illustration

For particular crisp values, we get

Using [Table 10.1](#ch10.xhtml#tab10_1), utilization factor and queue length is

[Table 10.1 Crisp values](#ch10.xhtml#R_tab10_1)

| m[1L] = 2 || λ[1L] = 2 || µ[1L] = 9 || α[12] = 0.4 |

| --- | --- | --- | --- |

| *m*[1]*[H]* = 4 || λ[1]*[H]* = 4 || µ[1]*[H]* = 16 || α[15] = 0.6 |

| --- | --- | --- | --- |

| *m*[2]*[L]* = 3 || λ[2]*[L]* = 3 || µ[2]*[L]* = 12 || α[21] = 0.3 |

| *m*[2]*[H]* = 5 || λ[2]*[H]* = 5 || µ[2]*[H]* = 15 || α[25] = 0.7 |

| *m*[2] = 3 || λ′[1] = 4 || µ′[1] = 10 || α[35] = 0.6 |

| *m*[3] = 4 || λ′[2] = 3 || µ′[2] = 13 || α[45] = 0.8 |

|  ||  || µ[3] = 27 ||  |

$$\\begin{array}{l} {\\gamma\_{1} = .3906,\\gamma\_{2} = .5,\\gamma\_{3} = .6666,\\gamma\_{4} = .2885,} \\\\ {\\gamma\_{5} = .7777,\\gamma\_{6} = .7568,\\gamma\_{7} = .8598} \\\\ {L\_{1} = \\frac{\\gamma\_{1}}{1 - \\gamma\_{1}} = .6409,\\, L\_{2} = \\frac{\\gamma\_{2}}{1 - \\gamma\_{2}} = 1,} \\\\ {L\_{3} = \\frac{\\gamma\_{3}}{1 - \\gamma\_{3}} = 1.9994,L\_{4} = \\frac{\\gamma\_{4}}{1 - \\gamma\_{4}} = .4055,} \\\\ {L\_{5} = \\frac{\\gamma\_{5}}{1 - \\gamma\_{5}} = 3.4984,L\_{6} = \\frac{\\gamma\_{6}}{1 - \\gamma\_{6}} = 3.1118,} \\\\ {\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\, L\_{7} = \\frac{\\gamma\_{7}}{1 - \\gamma\_{7}} = 6.1326} \\\\ \\end{array}$$  

### Fuzzified model
