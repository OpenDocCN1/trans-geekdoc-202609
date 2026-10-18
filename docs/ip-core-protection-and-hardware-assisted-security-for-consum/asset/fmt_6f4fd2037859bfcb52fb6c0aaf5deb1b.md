
3. 对每个出现的 `α` 或 `β` 数字，对排序输出变量对应的 `MixColumn` 硬件结构应用设计更改（重新配置）。例如，签名中的第一个 `α` 或 `β` 数字将影响对应于第一个排序变量 `Z[0]`（因为它是排序列表 `L[k]` 中的第一个）的硬件结构，随后的下一个 `α` 或 `β` 数字将影响对应于下一个排序变量 `Z[1]` 的硬件结构，依此类推。

4. 在修改后的 `MixColumn` 硬件结构中，在每个多路复用器和解多路复用器之后插入寄存器。

#### 10.3.3 Signature detection

签名检测通过以下两个阶段进行：

1. 检查 AES `MixColumn` 结构的数据路径以收集相关硬件信息。

2. 执行签名验证以验证 AES IP 核心设计中供应商签名的存在。首先，通过了解编码规则对编码签名进行解码。随后，在 `MixColumn` 硬件结构中验证作为水印的额外约束的存在。

### 10.4 Case study of a watermarked AES hardware

AES 设计在 Altera Quartus v.13 中使用 VHDL 实现，并在 AMD A8-4500M 和 4 GB DDR3 上运行。所选的目标硬件平台是 Cyclone II—Device EP2C70F896C6。

为了分析，选择了两种不同的水印签名大小，即 8 位数和 16 位数，用于嵌入 AES 硬件设计。进行了三种类型的实验：(a) 不同 8 位数签名组合及其对 AES 硬件综合结果的影响，(b) 不同 16 位数签名组合及其对 AES 硬件综合结果的影响，以及 (c) 与非水印 AES 相比，由于 8 位数签名和 16 位数签名而产生的开销。观察和分析了以下参数：总逻辑单元、总组合功能、专用逻辑寄存器、总寄存器和总引脚。8 位数和 16 位数水印签名以及非水印 AES 硬件的实现结果分别报告在表 [10.5](#Chapter10.html#c10_tbl5) 和 [10.6](#Chapter10.html#c10_tbl6) 中。签名 `ααββααββ` 对应的水印 AES 硬件部分显示在 [Figure 10.13](#Chapter10.html#c10_fig13)。[Figure 10.14](#Chapter10.html#c10_fig14) 显示了非水印 AES128 设计与三种不同的 8 位数水印设计组合在逻辑单元方面的比较。图 [10.14](#Chapter10.html#c10_fig14) 和 [10.15](#Chapter10.html#c10_fig15) 显示了非水印 AES128 硬件与不同组合的 8 位数和 16 位数水印 AES 的比较。

**Table 10.5** Results of implementation of AES (with and without watermark) for 8-digit signature

![image](OEBPS/images/tab10.5.jpg)

**Table 10.6** Implementation data of AES (with and without watermark) for 16-digit signature

![image](OEBPS/images/tab10.6.jpg)

![image](OEBPS/images/PBCS0600-10-f13.jpg)

Figure 10.13 Portion of watermarked AES hardware corresponding to signature `ααββααββ` in Altera Quartus commercial CAD synthesis

![image](OEBPS/images/PBCS0600-10-f14.jpg)

Figure 10.14 Comparison of non-watermarked AES128 design with three different combinations of 8-digit watermarked design

![image](OEBPS/images/PBCS0600-10-f15.jpg)

Figure 10.15 Comparison of non-watermarked AES128 design with three different combinations of 16-digit watermarked design

### 10.5 Conclusion

本章介绍了以下新颖且有趣的方面：(a) AES 算法——每个步骤及其流程图的描述，(b) AES 块密码的相应硬件映射——每个步骤如何映射到特定硬件子块的概述，(c) 密钥调度——每个步骤的描述，(d) AES 中使用的密钥调度的相应硬件映射，(e) AES 硬件的水印编码——保护 AES 硬件免受虚假所有权声明和盗版等威胁，(f) 水印 AES 硬件设计——水印嵌入过程的描述，以及 (g) 几种不同水印签名类型对 AES 硬件及其在 FPGA 上的实现的影响——以突出水印带来的开销。没有一章涉及 AES 算法的设计流程、其硬件设计视角以及针对不同签名位数的数字水印过程。最后，它提供了水印 AES 硬件与非水印 AES 硬件的清晰比较研究。本章内容有助于理解与第 08 章中介绍的数字信号处理核心功能混淆相结合的 AES 详细信息。

### 10.6 Exercises

1. What are the phases of AES?

2. How does S-box work?

3. Differentiate between diffusion layers 1 and 2?

4. How does key scheduling function?

5. What is the different number of rounds for different number of key length?

6. What is the function of modular reduction in AES and how does it perform?

7. How is column transformation performed?

8. How do you implement column transformation using H/W?

9. How modular reduction is implemented using H/W?

10. How is watermark embedded in AES?

11. Which stage of AES process is watermark inserted?

12. What is the impact of signature digits on watermarked AES design overhead?

13. How row-based diffusion is different than column based diffusion?

14. Explain state matrix in case of row-based diffusion?

15. Derive equations for MixColumn diffusion using GF arithmetic?

16. Explain state matrix in case of key addition layer?

17. How is hardware mapping of AEs performed? Explain the flow diagram?

18. Explain the MixColumn (diffusion layer 2) hardware perspective: before and after optimization?

19. How is RC calculated? Explain with example?

20. Explain hardware mapping of AES key schedule?

### References

Bhunia S. and Tehranipoor M. M., ‘Hardware security: A hands-on learning approach,’ Morgan Kaufmann imprint, USA, 2018.

Kosaraju N. M., Varanasi M., and Mohanty S. P., ‘A high-performance VLSI architecture for advanced encryption standard (AES) algorithm,’ Proceedings of the 19th International Conference on VLSI Design (VLSID), 2006, pp. 481–484.

Mishra P., Bhunia S., and Tehranipoor M., ‘Hardware IP security and trust,’ 2017, Springer, New York, USA.

Mohanty S. P., Sheth R., Pinto A., and Chandy M., ‘CryptMark: A novel secure invisible watermarking technique for color images,’ Proceedings of the 11th IEEE International Symposium on Consumer Electronics (ISCE), 2007, pp. 1–6.

Paar C. and Pelzl J., ‘Understanding cryptography – A textbook for students and practitioners,’ Springer-Verlag, Berlin Heidelberg, eBook ISBN 978-3-642-04101-3, Number of Pages: XVIII, **372**, Nov. 2009.

Sengupta A. (co-inventor: Reza Sedaghat), ‘System and methodology for development of a system architecture using optimization parameters,’ US Patent by United Sates Patent and Trademark Office (USPTO), March 12, 2013, Patent no. US 8,397,204.

Sengupta A., ‘Protection of IP-core designs for CE products,’ *IEEE Consumer Electronics Magazine*, 2015, **vol. 5**(1), pp. 83–89.

Sengupta A., ‘Hardware security of CE devices: Threat models and defense against IP Trojans and IP piracy,’ *IEEE Consumer Electronics Magazine*, 2017, **vol. 6** (1), pp. 130–133.

Sengupta A. and Bhadauria S., ‘Exploring low cost optimal watermark for reusable IP cores during high level synthesis,’ *IEEE Access Journal, Invited paper*, 2016, **vol. 4** (99), pp. 2198–2215.

Sengupta A. and Roy D., ‘Antipiracy-aware IP chipset design for CE devices: A robust watermarking approach’, *IEEE Consumer Electronics Magazine*, 2017a, **vol. 6** (2), pp. 118–124.
