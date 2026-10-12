
在关联多路盲源分离（BSS）中，对一组数据张量 $\mathbf{\underline{X}}^{(s)} \in \mathbb{R}^{I_1 \times I_2 \times \dots \times I_N}$ ($s = 1, 2, \dots, S$) 进行近似分解，这些张量代表多个受试者和/或多个任务（参见 Figure 8.9）。目标是找到一组受约束的因子矩阵 $\mathbf{U}^{(n,s)} = [\mathbf{U}_C^{(n)}, \mathbf{U}_I^{(n,s)}] \in \mathfrak{R}^{I_n \times J_n}$（$n = 1, 2, 3$）和核心张量 $\mathbf{\underline{G}}_{(s)} \in \mathfrak{R}^{J_1 \times J_2 \times J_3}$，它们部分关联或最大相关，即它们具有相同的公共成分或高度相关的成分。

在 EEG 信号的情况下，四维张量 $\mathbf{\underline{X}}$ 可以通过其三维分量定义为：

其中 $\times [k]$ 表示沿板（维度）$k$ 的张量乘法。每个因子 $\mathbf{U}^{(n,s)}$ 由两部分组成：一部分是 $\mathbf{U}_C^{(n,s)}$，这是组内所有受试者的公共基，对应相同或最大相关的成分；另一部分是 $\mathbf{U}_I^{(n,s)}$，对应于与刺激/任务无关的个体特征。$\mathbf{\underline{X}}^{(s)}$ 代表第 $s$ 个受试者的空间（通道）–时间–频率数据。

通常使用交替优化方法来估计因子，该方法最小化 Eq. (8.54) 左右两边项之间的距离。为了获得所有因子的唯一解，需要一些约束。对于 EEG 信号，此类约束可以是近似源定位、空间或频域稀疏性，或核心矩阵的已知结构，例如对于独立因子，核心矩阵是对角的。

![图 8.9 用于链接多路 BSS 的张量分解概念模型。目标是寻找一组受约束的因子矩阵 images，n = 1, 2, 3) 和核张量 images，它们部分链接或最大相关，即它们具有相同的公共成分或高度相关的成分 [77]。](images/c08f009.gif)

**图 8.9** 用于链接多路 BSS 的张量分解概念模型。目标是寻找一组受约束的因子矩阵 `images` `n = 1, 2, 3)` 和核张量 `images`，它们部分链接或最大相关，即它们具有相同的公共成分或高度相关的成分 [[77]](#c08.xhtml#c8-bib-0077)。

## 8.12 总结

利用 EEG 或 MEG 信号估计脑区连接性的研究，源于大约三十年前开展的工作。尽管 MVAR 和 DTF、SEM、PDC 以及 dDTF 等各种方法在连接性估计方面颇为流行，但利用 S 变换、扩散自适应、张量分解和基于图的信号处理等新方法，在连接性的建模与估计两方面均开辟了新领域。将这些新方法应用于 EEG 信号尚处于早期阶段，因此，需要开展更多研究，以建立用于 EEG 或 MEG 连接性度量的稳健流程。这些方法中的一个主要问题是，所有源均被视为皮层源，因此未曾尝试检查深层源的连接性。这需要对多个深层源进行定位，而这又是另一个极具挑战性的问题。在 Thatcher 等人 [[78]](#c08.xhtml#c8-bib-0078) 的一项工作中，低分辨率电磁断层扫描算法 (LORETA) 源定位算法已被应用于确定大脑中大量感兴趣区 (ROI) 内现存的电流源。随后计算时域和空域相关性作为连接性的度量。在连接性估计之前，先从噪声和无关信息中恢复信号，并更好地处理非皮层源，这也是合理的。当然，相关源无法使用传统的 BSS 方法进行分离。此外，连接性估计的应用不仅有助于痴呆、阿尔茨海默病 (AD) 和轻度认知障碍 (MCI) 等神经系统疾病的研究，还能协助追踪大脑内的运动相关电位。这些概念将在本书后续章节中讨论。

## 参考文献

1. **1** Sporns, O. (2011). Networks of the Brain. MIT Press.

2. **2** Sporns, O. (2011). The human connectome: a complex network. Annals of the New York Academy of Sciences 1224: 109–125.

3. **3** Steriade, M. (1995). Cellular substrates of brain rhythms. In: Electroencephalography (eds. Niedermeyer and L. da Silva), 27–62. Baltimore: Williams and Wilkins.

4. **4** Nunez, P. (1981). Electrical Fields of the Brain. New York: Oxford University Press.

5. **5** Nunez, P. (1994). Neocortical Dynamics and Human EEG Rhythms. New York: Oxford University Press.

6. **6** Adey, W.R., Walter, D.O., and Hendrix, C.E. (1961). Computer techniques in correlation and spectral analyses of cerebral slow waves during discriminative behavior. Experimental Neurology 3: 501–524.

7. **7** Sterman, M. and Kaiser, D. (2001). Comodulation: a new QEEG analysis metric for assessment of structural and functional disorders of the central nervous system. Journal of Neurotherapy 4 (3): 73–83.

8. **8** Kaminski, M. and Blinowska, K.J. (1991). A new method of the description of the information flow in brain structure. Biological Cybernetics 65: 203–210.

9. **9** Kaminski, M., Blinowska, K.J., and Szelenberger, W. (1997). Topographic analysis of coherence and propagation of EEG activity during sleep and wakefulness. Electroencephalography and Clinical Neurophysiology 102: 216–227.

10. **10** Korzeniewska, A., Kasicki, S., Kaminski, M., and Blinowska, K.J. (1997). Information flow between hippocampus and related structures during various types of rat's behaviour. Journal of Neuroscience Methods 73: 49–60.

11. **11** Jung, R.E. and Haier, R.J. (2007). The Parieto‐frontal integration theory (P‐FIT) of intelligence: converging neuroimaging evidence. The Behavioral and Brain Sciences 30 (2): 135–154.

12. **12** Picard, N. and Strick, P.L. (1996). Motor areas of the medial wall: a review of their location and functional activation. Cerebral Cortex 6: 342–353.

13. **13** Paus, T., Koski, L., Caramanos, Z., and Westbury, C. (1998). Regional differences in the effects of task difficulty and motor output on blood flow response in the human anterior cingulate cortex: a review of 107 PET activation studies. Neuroreport 9: R37–R47.

14. **14** Gerloff, G., Richard, J., Hadley, J. et al. (1998). Functional coupling and regional activation of human cortical motor areas during simple, internally paced and externally paced finger movements. Brain 121 (8): 1513–1531.

15. **15** Sharott, A., Magill, P.J., Bolam, J.P., and Brown, P. (2005). Directional analysis of coherent oscillatory field potentials in cerebral cortex and basal ganglia of the rat. Journal of Physiology 562 (3): 951–963.

16. **16** Kaminski, M. and Blinowska, K. (1991). A new method of the description of information flow in the brain structures. Biological Cybernetics 65: 203–210.

17. **17** Baccala, L.A. and Sameshima, K. (2001). Partial directed coherence: a new conception in neural structure determination. Biological Cybernetics 84: 463–474.

18. **18** Kaminski, M., Ding, M., Truccolo, W., and Bressler, S. (2001). Evaluating causal relations in neural systems: Granger causality, directed transfer function, and statistical assessment of significance. Biological Cybernetics 85: 145–157.

19. **19** Granger, C.W.J. (1969). Investigating causal relations in by econometric models and cross‐spectral methods. Econometrica 37: 424–438.

20. **20** Bernosconi, C. and König, P. (1999). On the directionality of cortical interactions studied by spectral analysis of electrophysiological recordings. Biological Cybernetics 81 (3): 199–210.

21. **21** Nolte, G., Ziehe, A., Nikulin, V.V. et al. (2008). Robustly estimating the flow direction of information of information in complex physical systems. Physical Review Letters 100 (23): 1–4.
