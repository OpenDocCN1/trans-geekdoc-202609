

3. IP 厂商 3：基于故障安全的 HLS 工具（[Sengupta 和 Sedaghat, 2015](#Chapter6.html#c06_bib31)）

4. IP 厂商 4：基于水印的 HLS 工具（[Koushanfar *et al.*, 2005](#Chapter6.html#c06_bib12)）

5. IP 厂商 5：基于木马安全的 HLS 工具（[Rajendran *et al.*, 2013](#Chapter6.html#c06_bib21)）

6. IP 厂商 6：基于 PSO 的 HLS 工具（[Mishra 和 Sengupta, 2014](#Chapter6.html#c06_bib18)）

7. IP 厂商 7：基于 BFOA 的 HLS 工具（[Sengupta 和 Bhadauria, 2015](#Chapter6.html#c06_bib24)）

表 [6.1](#Chapter6.html#c06_tbl1) 至 [6.6](#Chapter6.html#c06_tbl6) 展示了针对各种 DSP 和多媒体内核所获得的分析结果。如这些表所示，定制 CFE 方法（[Sengupta 和 Kachave, 2018](#Chapter6.html#c06_bib26））能够解决每个内核的所有权冲突。此外，即使多个 IP 内核功能在竞争 IP 厂商之间重叠，定制 CFE 仍然能够解决所有权冲突。这表明定制 CFE 方法在当前功能集上具有强大的解决所有权冲突的能力。值得注意的是，一个功能就足以区分竞争的 IP 厂商。例如，在功能集的十个功能中，即使两个 IP 内核（对应两个竞争 IP 厂商）的九个功能与待测 IP 重叠，但只有一个功能彼此不同，这可能足以识别实际 IP 所有者。这是因为拥有九个重叠功能的竞争 IP 厂商与 IP[ID] 的匹配度为 90%，而实际 IP 厂商与 IP[ID] 的匹配度为 100%。例如，如 [表 6.1](#Chapter6.html#c06_tbl1) 所示，尽管 IP[V1]、IP[V5] 和 IP[V7] 共有八个功能，但这些工具相对于 IP[ID] 的所有权冲突是基于剩余两个功能解决的，所有权被授予 IP 内核厂商 5。FIR 基准测试获得的结果显示了一个特殊情况，如第 III.B 节所述，其中没有任何竞争厂商的“功能集”与 IP[ID] 的“功能集” 100% 匹配。在这种情况下，所有权不会授予任何竞争厂商。

**Table 6.1** IP[ID] 和 IP[V] 对于 ARF 基准的功能集（注：IP[Vn] = 由竞争 HLS 工具的 IP 厂商“n”生成的 IP 内核）

![image](OEBPS/images/tab6.1.jpg)

**Table 6.2** IP[ID] 和 IP[V] 对于 BPF 基准的功能集

![image](OEBPS/images/tab6.2.jpg)

**Table 6.3** IP[ID] 和 IP[V] 对于 DCT 基准的功能集

![image](OEBPS/images/tab6.3.jpg)

**Table 6.4** IP[ID] 和 IP[V] 对于 FFT 基准的功能集

![image](OEBPS/images/tab6.4.jpg)

**Table 6.5** IP[ID] 和 IP[V] 对于 FIR 基准的功能集：FIR（23 节点）

![image](OEBPS/images/tab6.5.jpg)

**Table 6.6** IP[ID] 和 IP[V] 对于 JPEG IDCT 基准的功能集

![image](OEBPS/images/tab6.6.jpg)

表 [6.7](#Chapter6.html#c06_tbl7) 展示了基于设计开销（存储寄存器）的 CFE（[Sengupta 和 Kachave, 2018](#Chapter6.html#c06_bib26)）与硬件水印（[Koushanfar *et al.*, 2005](#Chapter6.html#c06_bib12)）在 DSP IP 内核保护方面的相对比较。如结果所示，与硬件水印相比，CFE（[Sengupta 和 Kachave, 2018](#Chapter6.html#c06_bib26)）产生 0% 的设计开销。这是因为硬件水印需要将厂商签名嵌入 IP 内核设计，这可能会产生存储开销。另一方面，CFE 在 IP 内核生成后执行。因此，定制 CFE 不会产生设计开销。此外，出于同样的原因，CFE 不会影响 IP 内核的设计性能；然而，硬件水印过程中的签名插入可能会影响 IP 内核的性能。

**Table 6.7** 定制 CFE 方法与水印（[Koushanfar *et al.*, 2005](#Chapter6.html#c06_bib12)）在 HLS 期间 IP 保护中的存储开销比较

![image](OEBPS/images/tab6.7.jpg)

### 6.5 结论

本章讨论了一种名为 CFE 的替代所有权保护方法，来自 [Sengupta 和 Kachave (2018)](#Chapter6.html#c06_bib26)，适用于解决 DSP IP 内核的所有权冲突。此外，本章描述了“功能集”的几个功能，这些功能用于以 0% 的硬件性能下降解决所有权冲突，并与流行的基于硬件水印的 DSP 内核所有权保护（[Koushanfar *et al.*, 2005](#Chapter6.html#c06_bib12)）相比，产生 0% 的存储开销。

未来方向可以针对开发新的“扩展功能集”，以在“死锁”情况下解决 DSP IP 内核的所有权冲突。此外，可以修改“调度算法”功能的功能提取规则，以包含其他调度算法，如力导向调度。

### 6.6 练习

1. CFE 和水印之间有什么区别？

2. CFE 和 IP 计量之间有什么区别？

3. CFE 的不同阶段是什么？

4. 功能提取是如何工作的？

5. 解释链式的功能提取算法。

6. 解释多周期的功能提取算法。

7. 解释流水线的功能提取算法。

8. 解释木马安全的功能提取算法。

9. 解释瞬态故障安全的功能提取算法。

10. 解释 IP 验证过程。

11. 解释调度的功能提取算法。

12. 功能提取应用在哪里？

13. 用于 IP 内核保护的 CFE 与普通 CFE 有何不同？

14. 通过 HLS 工具生成的 IP 内核的其他哪些功能可用于功能提取？

15. IP 保护的 CFE 中通用功能和独特功能有什么区别？

16. 解释 CFE 可以应用于的一些 HLS 工具/方法。

17. CFE 功能集中不同功能的平均提取时间的趋势是什么？

18. 解释 IP 内核保护期间 CFE 方法的一些基本假设。

19. 如果使用的功能集无法找到实际 IP 所有者，会发生什么？

20. 为什么 CFE 不会产生任何硬件开销？

### 参考文献

Bhunia S., Abramovici M., Agrawal D., et al., ‘Protection against hardware Trojan attacks: Towards a comprehensive solution’, *Proceedings of IEEE Design & Test*, 2013, **vol. 99**, pp. 1–1.

D’Angelo S., Metra C., and Sechi G., ‘Transient and permanent fault diagnosis for FPGA-based TMR systems,’ Defect and Fault Tolerance in VLSI Systems, 1999. DFT ‘99. International Symposium on, Albuquerque, NM, 1999, pp. 330–338.

Express Benchmark Suite Express Benchmark Suite, University of California San Diego, [http://www.ece.ucsb.edu/EXPRESS/benchmark/](http://www.ece.ucsb.edu/EXPRESS/benchmark/), Last accessed on 2018.

Franke K. and Srihari S. N., ‘Computational forensics: An overview’. In: Srihari S.N., Franke K. (eds) *Computational Forensics. IWCF 2008. Lecture Notes in Computer Science*, 2008, **vol. 5158**. Springer, Berlin, Heidelberg.

Gupta S., ‘Loop shifting and compaction for the high-level synthesis of designs with complex control flow’, Technical Report CECS-TR-03-14, 2003, UC Irvine.

Harish Ram D. S., Bhuvaneswari M. C., and Logesh S. M., ‘A novel evolutionary technique for multi-objective power, area and delay optimization in high level synthesis of datapaths,’ Proceedings of the IEEE Computer Society Annual Symposium on VLSI (ISVLSI ’11), 2011, pp. 290–295.

Inoue T., Henmi H., Yoshikawa Y., and Ichihara H., ‘High-level synthesis for multi-cycle transient fault tolerant datapaths.’ 2011 IEEE 17th International On-Line Testing Symposium, 2011, pp. 13–18.

International Chamber of Commerce, ‘Estimating the global economic and social impacts of counterfeiting and piracy,’ International Chamber of Commerce, Paris, France,Tech. Rep., 2011.

