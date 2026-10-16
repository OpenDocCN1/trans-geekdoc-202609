
优化发酵过程包含多种约束，如成本、人工劳动、开放式和耗时的工艺，这些工艺包含多个步骤。持续地，新的菌株和突变体在生物过程工业中被引入，因此需要进行优化实验（`[Stanbury et al. 2013](#ch6.xhtml#ref6_67)`）。随着发酵过程的加快，将需要技术来在低成本下获得高产量的终端产物，这将与传统的发酵工艺方法竞争。目前，遗传算法（GAs），一种非统计优化技术，被用于优化发酵过程。遗传算法是一种随机优化模型，可以通过模拟自然进化来找到最优或近似最优的解（`[Adeyemo and Enitan 2011](#ch6.xhtml#ref6_1)`）。GAs 是与概率论理论相关的强大随机搜索算法。GA 的核心概念是遗传学和自然选择过程，历史信息被用于将算法引向最佳水平。GAs 基于“适者生存”的原则，即在反复的变异步骤后，只有最佳个体才会存在。为了识别理想或最佳解集，算法模拟自然种群中的进化原因。在单一步骤中，从当前种群中 GAs 随机选择父染色体（一些个体解）以产生后代用于下一代。随着连续代数的重复，种群会演化为最适合的解决方案。同样，GAs 负责通过进化生物学、概率论和搜索算法来生产高产量的产品或解决方案，以优化发酵过程。在 GA 中，初始解集可以被理解为一个具有特定染色体的个体（属于种群）。选择两个染色体集作为父染色体，通过重组和突变过程得到后代种群（`[Vasant and Barsoum 2009](#ch6.xhtml#ref6_70)`）。每条染色体由多个基因组成，这些基因定义特定参数，每个位点描述该参数的值。决定下一代的三个过程是“选择”、“交叉”和“变异”。选择挑选父染色体，交叉将它们结合起来形成后代，就像自然界中的重组一样。变异在每个循环中对染色体引入随机变化（`V. [Singh et al. 2017](#ch6.xhtml#ref6_61)`）。选择通常基于染色体的适应度，由适应度因子定义（`[Doganis et al. 2006](#ch6.xhtml#ref6_16)`）。GA 相较于传统优化技术具有多项优势。它能够解决复杂的问题描述，并可并行运行。GA 可处理各种优化方法，其适应度（或目标）函数可采用多种形式，如带有随机噪声、线性/非线性、静态/非静态（随时间变化）以及连续/不连续。由于种群中的多个后代作为独立代理，样本组（或种群）可以在多个方向上并行探索搜索（或解）空间。由于这一特性，GA 通过并行化算法加快了寻找最优解的过程。此外，GAs 能够同时处理多个参数和不同的编码字符串组（`Table 6.1`）。

``` 
Table 6.1 Microbial Sources of Various Enzymes and Their Optimization Using Conventional Optimization Techniques 

| Microbial Source  || Enzyme || Applications || Optimization Method || Reference |
| --- | --- | --- | --- | --- |
| *Bacillus subtilis JK-79* || L-glutaminase || Therapeutic enzyme || PBD and RSM || [`Kiruthika and Murugesan (2020)`](#ch6.xhtml#ref6_33) |
| --- | --- | --- | --- | --- |
| *Aeromonas veronii* || L-glutaminase || Anti-cancer enzyme || PBD and CCD || [`Jesuraj et al. (2017)`](#ch6.xhtml#ref6_31) |
| *Alcaligenes faecalis KLU102* || L-glutaminase || Anti-cancer enzyme || RSM || [`Pandian et al. 2014`](#ch6.xhtml#ref6_45) |
| *Trichoderma reesei QM9414* || Cellulases || Cellulolytic enzyme || CCRD || [`Sirohi et al. 2019`](#ch6.xhtml#ref6_64) |
| *Penicillium citrinum YL-1* || Alkaline protease || Proteolytic || PBD and RSM || [`Xiao et al. 2015`](#ch6.xhtml#ref6_73) |
| *Streptomyces griseoloalbus* || α-galactosi-dase || Glycoside hydrolase enzyme || RSM || [`Anisha et al. 2008`](#ch6.xhtml#ref6_3) |
| *Bacillus subtilis RSP-GLU MTCC 9727* || L-glutaminase || Deamidation/aminohydrolase enzyme || RSM || [`Sathish et al. 2018`](#ch6.xhtml#ref6_56) |
| *Serratia marcescens NCIM 2919* || L-asparagi-nase || Therapeutic enzyme || RSM || [`Ghosh et al. 2013`](#ch6.xhtml#ref6_23) |
| *Enterobacter aerogenes MTCC111* || L-asparagi-nase || Therapeutic enzyme || RSM || [`Erva et al. 2017`](#ch6.xhtml#ref6_19) |
| *Bacillus* sp. *VUVD101* || Lactase || Lignocellulolytic enzyme || PBD || [`Karlapudi et al. 2018`](#ch6.xhtml#ref6_32) |
| Abbreviations: CCD – Central composite design, RSM – Response surface methodology, PBD – Plakett–Burman design |
| --- |
### 6.4.1 History of GA

