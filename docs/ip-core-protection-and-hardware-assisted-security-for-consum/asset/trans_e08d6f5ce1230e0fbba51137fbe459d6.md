

**Table 7.4** 多级混淆（[Sengupta et al., 2017a](#Chapter7.html#c07_bib36））设计与单级混淆（[Lao and Parhi, 2015](#Chapter7.html#c07_bib14））设计在面积、延迟和成本方面的对比

![image](OEBPS/images/tab7.4.jpg)

![image](OEBPS/images/PBCS0600-07-f17.jpg)

Figure 7.17 DSP 核心单级与多级混淆的设计成本对比

[Table 7.5](#Chapter7.html#c07_tbl5) 报告了基于多级的混淆技术（[Sengupta *et al.*, 2017a](#Chapter7.html#c07_bib36））与基于单级的混淆技术（[Lao and Parhi, 2015](#Chapter7.html#c07_bib14））在安全性方面的比较研究，该安全性通过*混淆能力*指标衡量。从表中可以看出，基于多级的混淆过程提供了更强的 IP 保护。这是因为对于所有 DSP 应用，基于多级的混淆方法具有更高的 *P*^(obf) 值。例如，对于基于单级的混淆 ARF，*P*^(obf) 为 0.43，而对于基于多级的混淆 ARF，它为 0.55。总结来说，多级混淆方法（[Sengupta *et al.*, 2017a](#Chapter7.html#c07_bib36））平均比单级混淆方法（[Lao and Parhi, 2015](#Chapter7.html#c07_bib14））实现了 29% 更好的鲁棒性。单级与多级混淆之间 *P*^(obf) 比较的图形表示在 [Figure 7.18](#Chapter7.html#c07_fig18) 中显示。

**Table 7.5** 多级混淆（[Sengupta et al., 2017a](#Chapter7.html#c07_bib36））设计与单级混淆（[Lao and Parhi, 2015](#Chapter7.html#c07_bib14））设计在 P^(obf) 方面的对比

![image](OEBPS/images/tab7.5.jpg)

![image](OEBPS/images/PBCS0600-07-f18.jpg)

Figure 7.18 单级与多级混淆之间 P^(obf) 的比较

### 7.7 结论

本章介绍了结构混淆机制，用于保护 DSP IP 核心。这些机制通过多种编译器和基于循环的变换技术执行结构混淆。此外，某些混淆方法比其他方法提供更低的设计成本和更强的鲁棒性。本章讨论的多级混淆机制的鲁棒性可以通过在 DSP IP 核心上添加更多变换技术来提高。此外，结构混淆方法与功能混淆的结合也可以增强 DSP 应用的安全性。这将能够从对手那里隐藏应用程序及其实现。

### 7.8 练习

1. 什么是结构混淆？

2. 结构混淆的优点/缺点是什么？

3. 结构混淆的编译器驱动技术有哪些？

4. DSP 核心的结构混淆在 HLS 的哪个阶段执行？

5. 什么是基于折叠的结构混淆？

6. 结构混淆如何实现设计延迟的降低？

7. 结构混淆如何使 RE 攻击复杂化？

8. 结构混淆的影响在设计的哪里体现？

9. 什么是混淆能力，如何增强它？

10. DSP 核心的其他可能的结构混淆方式有哪些？

11. 实现一个结构混淆的 CODEC IP 核心。

12. 除了高级变换之外，如何优化混淆设计的延迟？

13. 解释结构混淆情况下的威胁模型。

14. 结构混淆与其功能对应物有何不同？

15. PSO-DSE 在混淆中的作用是什么？

16. 在结构混淆过程中，粒子是如何编码的？

17. 解释用于混淆的不同变换。

18. 解释每种变换的优点和缺点。

19. 哪种变换能够提供 DSP 核心的最大混淆？为什么？

20. 如何评估 DSP 核心由于混淆而产生的设计开销？

### 参考文献

Alkabani Y. M. and Koushanfar F., ‘Active hardware metering for intellectual property protection and security,’ Proceedings of USENIX Security Symposium, 2007, pp. 20:1–20:16.

Barria C., Cordero D., Cubillos C., and Osses R., ‘Obfuscation procedure based in dead code insertion into crypter,’ in International Conference on Computers Communications and Control (ICCCC), May 2016, pp. 23–29.

Baumgarten A., Tyagi A., and Zambreno J., ‘Preventing IC piracy using reconfigurable logic barriers,’ *IEEE Design Test of Computers*, 2010, **vol. 27** (1), pp. 66–75.

Benchmark1, 2017, ‘Express Benchmark Suite,’ \[Online\]. Available: [https://www.ece.ucsb.edu/EXPRESS/benchmark/](https://www.ece.ucsb.edu/EXPRESS/benchmark/), University of California Santa Barbara, last accessed on December 2017.

Benchmark2, 2017, ‘Vipul Kumar Mishra, Anirban Sengupta, “Swarm Inspired Exploration of Architecture and Unrolling Factors for Nested Loop Based Application in Architectural Synthesis”,’ IET Electronics Letters, 2015, vol. 51 (2), pp. 157–159.

Brzozowski M. and Yarmolik V. N., ‘Obfuscation as intellectual rights protection in VHDL language,’ Computer Information Systems and Industrial Management Applications (CISIM), June 2007, pp. 337–340.

Castillo E., Meyer-Baese U., Garcia A., Parrilla L., and Lloris A., ‘IPP@HDL: Efficient intellectual property protection scheme for IP cores,’ *IEEE Transactions on Very Large Scale Integration Sys.*, 2007, **vol. 15** (5), pp. 578–591.

Chakraborty R. S. and Bhunia S., ‘HARPOON: An Obfuscation-Based SoC Design Methodology for Hardware Protection,’ *IEEE Transactions on CAD of Integrated Circuits and Systems*, 2009, **vol. 28** (10), pp. 1493–1502.

Desai A.R., Hsiao M.S., Wang C., Nazhandali L., and Hall S., ‘Interlocking obfuscation for anti-tamper hardware,’ Proceedings of Cyber Security and Information Intelligence Research Workshop (CSIIRW), 2013, pp. 8:1–8:4.

Dupuis S., Ba P. S., Di Natale G., Flottes M. L., and Rouzeyre B., ‘A novel hardware logic encryption technique for thwarting illegal overproduction and Hardware Trojans,’ IEEE International Online Testing Symposium (IOLTS), 2014, pp. 49–54.

ExtremeTech, iphone 5 A6 SoC reverse engineered, reveals rare hand-made custom CPU, and tri-core GPU (2012).

Guajardo J., Kumar S. S., Schrijen G. J., and Tuyls P., ‘Brand and IP protection with physical unclonable functions,’ Proceedings of IEEE International Symposium on Circuits and Systems, May 2008, pp. 3186–3189.

Kim J., Jung E. S., Lee Y. T., and Ryu W., ‘Home appliance control framework based on smart TV set-top box,’ *IEEE Transactions on Consumer Electronics*, 2015, **vol. 61** (3), pp. 279–285.

Koushanfar F., *‘Hardware Metering: A Survey’*, New York, NY: Springer New York, 2012, pp. 103–122.

Lao Y. and Parhi K. K., ‘Obfuscating DSP circuits via high-level transformations,’ *IEEE Transactions on Very Large Scale Integration Systems*, 2015, **vol. 23** (5), pp. 819–830.

Lee Y. W. and Touba N. A., ‘Improving logic obfuscation via logic cone analysis,’ Latin-American Test Symposium (LATS), 2015, pp. 1–6.

Li M., Zhang P., Zhu C., *et al.*, ‘High efficiency VLSI implementation of an edge-directed video up-scaler using high level synthesis,’ Proceedings of IEEE International Conference on Consumer Electronics (ICCE), 2015, pp. 92–95.

Mohanty S. P., ‘Energy and transient power minimization during behavioral synthesis,’ Doctoral Dissertation, Department of Computer Science and Engineering, University of South Florida, USA, 2003.

Mohanty S. P., ‘*Nanoelectronic Mixed-Signal System Design*,’ McGraw-Hill Education, New York, 2015, no. 0071825711.

Mohanty S. P., Ranganathan N., Kougianos E., and Patra P., ‘*Low-Power High-Level Synthesis for Nanoscale CMOS Circuits*,’ Springer, New York, 2008, ISBN-10: 0387764739, ISBN-13: 978-0387764733.

NanGate 15 nm open cell library. \[Online\]. Available: [http://www.nangate.com/?pageid=2328](http://www.nangate.com/?pageid=2328), last accessed on June 2017.

