
![image](OEBPS/images/tab8.4.jpg)

### 8.7.3 Comparative analysis

In this subsection, the comparative analysis between Sengupta *et al.* ([2018](#Chapter8.html#c08_bib35)) and Yasin *et al.* ([2016](#Chapter8.html#c08_bib44)) is shown in terms of leakage power consumption and obfuscated design cost. Additionally, exploration time of PSO and design delay before and after inserting the ILBs are also discussed. The graphical representation of the leakage power consumption of Sengupta *et al.* ([2018](#Chapter8.html#c08_bib35)) and Yasin *et al.* ([2016](#Chapter8.html#c08_bib44)) is shown in [Figure 8.15](#Chapter8.html#c08_fig15). It can be seen that for all the tested DSP benchmarks ([Sengupta *et al.*, 2018](#Chapter8.html#c08_bib35)) achieves lesser power consumption than related approaches. An average reduction of 11.07% in static power consumption is achieved in Sengupta *et al.* ([2018](#Chapter8.html#c08_bib35)) compared to Yasin *et al.* ([2016](#Chapter8.html#c08_bib44)). The graphical representation of the obfuscated design cost of Sengupta *et al.* ([2018](#Chapter8.html#c08_bib35)) and Yasin *et al.* ([2016](#Chapter8.html#c08_bib44)) is shown in [Figure 8.16](#Chapter8.html#c08_fig16). It can be observed that for all the DSP benchmarks ([Sengupta *et al.*, 2018](#Chapter8.html#c08_bib35)) achieves lesser design cost than related approaches. An average reduction of 8.87% in obfuscated design cost is achieved in Sengupta *et al.* ([2018](#Chapter8.html#c08_bib35)) compared to Yasin *et al.* ([2016](#Chapter8.html#c08_bib44)). As both Sengupta *et al.* ([2018](#Chapter8.html#c08_bib35)) and Yasin *et al.* ([2016](#Chapter8.html#c08_bib44)) include AES block to handle (potential) SAT attack, therefore the total power and design cost reduction in Sengupta *et al.* ([2018](#Chapter8.html#c08_bib35)) obtained due to PSO-DSE remains intact.

![image](OEBPS/images/PBCS0600-08-f15.jpg)

Figure 8.15 Comparison of power consumption

![image](OEBPS/images/PBCS0600-08-f16.jpg)

Figure 8.16 Comparison of design cost

[Figure 8.17](#Chapter8.html#c08_fig17) presents the overall design delay overhead due to insertion of ILBs in Sengupta *et al.* ([2018](#Chapter8.html#c08_bib35)). It can be observed from [Figure 8.17](#Chapter8.html#c08_fig17), the delay incurred due to the insertion of ILB is marginal. Moreover, the total delay (including the delay of ILBs) of the obfuscated design is optimized through the PSO-DSE framework. [Figure 8.18](#Chapter8.html#c08_fig18) presents the exploration time (in seconds) of the PSO approach for generating low-cost obfuscated netlist for DSP cores. It can also be noted that for very large size DSP IP cores such as JPEG IDCT and MESA (around 50K plus gates), the exploration time is not too large. Therefore, the optimization framework used in Sengupta *et al.* ([2018](#Chapter8.html#c08_bib35)) does not suffer from scalability issue.

![image](OEBPS/images/PBCS0600-08-f17.jpg)

Figure 8.17 Delay due to the insertion of ILBs

![image](OEBPS/images/PBCS0600-08-f18.jpg)

Figure 8.18 Exploration time of PSO DSE

### 8.8 Conclusion

This chapter presents a low-cost, functional obfuscation mechanism for DSP IP core. This mechanism inserts reconfigured ILBs to lock a netlist of DSP IP core. Moreover, it integrates AES block to prevent SAT attack as a proactive countermeasure. Moreover, it was observed that Sengupta *et al.* ([2018](#Chapter8.html#c08_bib35)) yielded power reduction, design cost reduction, and SoO enhancement over other similar approaches. The research on functional obfuscation is still an open area and more research needs to be conducted for the protection of other hardware circuits such as combinational/sequential circuit benchmarks against SAT attacks. There are new attacks such as approximate SAT and signal probability skew that are being launched to nullify the effect of anti-SAT blocks used in conjunction with combinational/sequential circuit benchmarks. There is significant scope of work in the future in this direction.

### 8.9 Exercises

1. What is functional obfuscation?

2. What is the difference between structural obfuscation and functional obfuscation in the context of DSP cores?

3. What are the disadvantages of functional obfuscation?

4. What is threat model of functional obfuscation?

5. How/where is locking performed?

6. What are the properties of ILBs?

7. Why functional obfuscation is vulnerable to SAT attack for combinational/sequential circuits?

8. Why functional obfuscation is not vulnerable to SAT attack for DSP core?

9. What is CNF?

10. How to find CNF for basic gates?

11. How to determine DIP?

12. How does AES protect against removal attacks of ILBs?

13. How is AES customized during the insertion with obfuscation design?

14. How is AES removal attack prevented?

15. Design an obfuscated FFT (*n* = 8).

16. What are the possible alternatives of AES for functional obfuscation?

17. What is key sensitization attack?

18. Design an ILB with AND, NAND, NOT, XOR, and XNOR gates.

19. What is the difference between pairwise security and multi pair-wise security?

20. What is the role of random variable “µ” in functional obfuscation?

21. What is run of key gates? How is it a drawback in the context of obfuscation?

22. Design a lightweight AES that uses less than 1% FPGA resources.

23. How do you determine the design cost of a FO DSP design?

### References

Alkabani Y. M. and Koushanfar F., ‘Active hardware metering for intellectual property protection and security,’ Proceedings of USENIX Security Symposium, 2007, pp. 20:1–20:16.

Baumgarten A., Tyagi A., and Zambreno J., ‘Preventing IC piracy using reconfigurable logic barriers,’ *IEEE Design Test of Computers*, 2010, **vol. 27** (1), pp. 66–75.

Biggerstaff T. J., ‘Design recovery for maintenance and reuse,’ *Computer*, 1989, **vol. 22** (7), pp. 36–49.

Castillo E., Meyer-Baese U., Garcia A., Parrilla L., and Lloris A., ‘IPP@HDL: Efficient intellectual property protection scheme for IP cores,’ *IEEE Transactions on Very Large Scale Integration Systems*, 2007, **vol. 15** (5), pp. 578–591.

Chakraborty R. S. and Bhunia S., ‘HARPOON: An obfuscation-based SoC design methodology for hardware protection,’ *IEEE Transactions on CAD of Integrated Circuits and Systems*, 2009, **vol. 28** (10), pp. 1493–1502.

Chakraborty S., Gupta A., and Jain R. ‘Matching multiplications in bit-vector formulas,’ Springer International Publishing, Cham, 2017, pp.131–150.

Cyclone II FPGA, Available: [https://www.altera.com/products/fpga/cyclone-series/cyclone-ii/overview.html](https://www.altera.com/products/fpga/cyclone-series/cyclone-ii/overview.html), last accessed on 2018.

DSP Benchmark Suite, Available: [http://www.ece.ucsb.edu/EXPRESS/benchmark/](http://www.ece.ucsb.edu/EXPRESS/benchmark/), 2017. last accessed on June 2017.

Desai A.R., Hsiao M.S., Wang C., Nazhandali L., and Hall S., ‘Interlocking obfuscation for anti-tamper hardware,’ in Proceedings of Cyber Security and Information Intelligence Research Workshop (CSIIRW), 2013, pp. 8:1–8:4.

Dupuis S., Ba P. S., Di Natale G., Flottes M. L. and Rouzeyre B., ‘A novel hardware logic encryption technique for thwarting illegal overproduction and hardware Trojans,’ IEEE InternationalOn-Line Testing Symposium (IOLTS), 2014, pp. 49–54.

Finke M., ‘Equisatisfiable SAT encodings of arithmetical operations’, 2015, Available: [http://www.martin-finke.de/documents/Masterarbeit\_bitblast\_Finke.pdf](http://www.martin-finke.de/documents/Masterarbeit_bitblast_Finke.pdf).

Guajardo J., Kumar S. S., Schrijen G. J., and Tuyls P., ‘Brand and IP protection with physical unclonable functions,’ Proceedings of IEEE International Symposium on Circuits and Systems, 2008, pp. 3186–3189.
