
## 5 Memristors and Their Applications 115

to the attacker, while the other read pulse is private and is known only to the authorized user. Thus, an attacker cannot restore the memristance value to its original, which was created by the second pulse with its nonpublic parameters, even though they can revert the drift created by the first pulse. This memristance drift can be detected by an authorized user and thus help in determining possible tampering.

### 5.8.6 Nanoelectronics-Based Forensics (NanoForensics)

Digital forensics involve the recovery of data from hardware. For forensic applications, digital logic gates based on memristors utilize the run-time drift property of memristors.

When logic 0 is applied to an input, there will be no change in memristance value. But when logic 1 is applied, there is a drift in the memristance value of that particular memristor. The number of logic 1s applied to the input determines the amount of drift. Consider a memristor-based threshold logic (MTL) (Figure 5.18), realizing an AND function. The location of the gate within the circuit determines the number of 1s received by its input. Thus, the memristance drift at the inputs of different gates will differ.

The number of 1s that are received by input is determined by measuring the memristance drift of that particular memristor and, in the same way, can be determined for all the memristors in the circuit. These measurements can help make a forensic analysis. If no memristance drift was observed in any of the memristors, then it can be concluded that the hardware was not used at all.

![](img/f43fc2d88fdf77da6ccf8abfe605d6a7_127_0.png)

## Nanoelectronic Devices for Security

## 5.9 LIMITATIONS AND FUTURE SCOPE OF MEMRISTORS

The main challenges regarding the use of memristors are that they have low speed, and at high frequency, major changes can occur in the memristor's characteristics. Also, because this is a new circuit element, designers need to learn how to build circuits using memristors. Besides this, a standard memristor model is needed that can be used for the purpose of fabrication and simulation.

The use of memristors in NVRAM can greatly revolutionize memory storage systems. In the field of neural network systems, the use of memristors could reveal crucial information about how the human brain works.

## 5.10 CONCLUSION

Research is going on explore different aspects of the memristor, its other applications, and efforts to overcome its limitations. Since the need for an ultimate source for nonvolatile memory storage system is increasing every day, the application of memristors in NVRAM may bring another era in computer systems.

## REFERENCES

- [1] L. O. Chua, "Memristors – The missing circuit element," IEEE Transactions on Circuit Theory, vol. CT18, no. 5, pp. 507–519, Sep. 1971.
- [2] D. B. Strukov, G. S. Snider, R. D. Stewart & R. S. Williams, "The missing memristor found," Nature, vol. 453, pp. 80–83, 2008.
- [3] R. Waser & M. Aomo, "Nanoionics-based resistive switching motions," Nature Materials, vol. 6, pp. 833–840, 2007.
- [4] Aloon Ascelli, Corinto Ravessa, Vanessa Senger & Ronald Teetzblatt, "Memristor model comparison," IEEE Circuits and Systems Magazine, pp. 89–105, May 2013; doi:10.1109/MCAS.2013.2256272.
- [5] Valeri Mladenov, Advanced Memristor Modeling, Memristor Circuits and Networks Memristor Modeling, Memristor Devices, Circuits and Networks; MDPI: Basel, Switzerland, p. 4–840, 2019.
- [6] T. Proodmazou, "A review on memristive devices and applications," in Proceedings of 17th International Conference on Electronics, Circuits and Systems (IECS 2010), pp. 934–937, 2010.
- [7] Kuk-Hwan Kim, Siddharth Gul, Dana Wheeler, Jose C.Albrecht, Tahir Hussain, Narayan Srinivasa & Wei Lei, "A functional hybrid memristor crossbar array for data storage and neuromorphic applications," IEEE International Society, pp. 389–395, 2012.
- [8] Y. Yuanfang, "Memory with memristor base-autonomous application to pattern recognition," Proceedings of 12th International Conference on Signal Processing (ICSP), pp. 1463–1468, 2014.
- [9] M.D. Gregory & D.H. Wenner, "The application of memristor in reconfigurable electronic devices," IEEE Antenna and Propagation Magazine, vol. 57, no. 1, pp. 239–248.
- [10] Q. Xia et al., "Memrist-CMOS integrated circuits for reconfigurable logic," IEEE Letters, vol. 9, no. 10, pp. 3640–3645, 2009.
- [11] R. Williams, N. McDonald, L.-K. Yan & B. Wysocki, "A write-time memristor hardware for security," in Proceedings of International Conference on Computer-Aided Design, 2013, pp. 823–833.
- [12] J. Rajander, G. Rose, R. Karri, & M. Potkanjak, "NanoPUF: A memristor-based security primitive," in Proceedings of IEEE Symposium on VLSI, 2012, pp. 84–87.
- [14] C. Huang, W. Shen, Y. Tseng, C. King & Y. Lin, "A resistive random-access-memory-based true number generator," Electronic Device Letters, vol. 33, no. 8, pp. 1108–1110, 2002.
- [15] N. McDonald, "Al/CuOx/Cu memristive devices: Fabrication, characterization, and modeling," M.S. Thesis, College of Nanoscale Science and Engineering, Albany, NY, 2012, vol. 153.
- [16] X. Wang & Y. Chen, "Spintronic memristor devices and application," in Proceedings of IEEE/ACM Design, Automation and Test in Europe Conference Exhibition, 2010, pp. 667–672.
- [17] J. Rajendran, H. Manem, R. Karri & G. Rose, "An energy-efficient memristive logic circuit," IEEE Transactions on Computers, vol. 61, pp. 474–487, 2012.

![](img/f43fc2d88fdf77da6ccf8abfe605d6a7_130_0.png)

# Memristor A Novel Device for Better Hardware/Software Security
Ms Chhaya Verma and Jeetendra Singh

## Contents
6.1 Introduction 120
6.1.1 Device Structure and Basic Model 120
6.1.2 Memristors Operations 121
6.1.3 Various Characteristics of Memristors 122
6.1.3.1 Nonvolatility 122
6.1.3.2 Nonlinearity 122
6.1.3.3 Bidirectionality 122
6.1.3.4 Formation Process 122
6.1.3.5 Memristance Drift 123
6.1.3.6 Process Variations 123
6.1.3.7 Radiation-Hardness 123
6.1.3.8 Temperature Stability 123
6.2 Memristor-Based PUF and PUFAF 123
6.2.1 Physically Unclonable Function (PUF) 123
6.2.2 Memristor-Based PUF (NanoPUF/M-PUF) Architecture 124
6.2.3 Operation of Memristor-Dependent PUF 125
6.2.4 Security Analysis 125
6.2.5 Memristor-Based PUF (M-PUF/Memristor NanoPUF) 126
6.2.6 The Architecture of Memristor NanoPUF 126
6.2.7 Operation of Memristor NanoPUF 126
6.2.7.1 Characterization Phase 127
6.2.7.2 Refresh Phase 127
6.2.7.3 Challenge–Response Phase 127
6.2.7.4 Measurement Phase 127
6.2.8 Protocols 127
6.3 Memristor-Dependent True Random Number Generators (NanoTRNGs) 128
6.3.1 True Random Number Generators 128

## Nanoelectronic Devices for Security
6.4 Memristor-Based Tamper Detection Circuit 130
6.4.1 The Architecture of Tamper Detection Circuit 130
6.4.2 Manufacture-Time Tamper Detection 130
6.4.3 Run-Time Tamper Detection 131
6.5 Memristor-Based Forensics 131
6.5.1 The Architecture of Memristor-Based Forensics 131
6.5.2 Operation of Memristor-Based Forensics 132
6.6 Memristor-Based Cryptography 132
6.6.1 Architecture Memristor-Based Cryptography 133
6.6.2 Operation Memristor-Based Cryptography 134
6.7 Memristor-Based Neuromorphic Security System 134
6.8 Memristor-Based Chaotic Circuit for Secure Communication 134
6.9 Conclusion 135
6.9 References 135

## 6.1 INTRODUCTION

The memristors are the fourth fundamental and volatile electrical two-terminal devices. These behave as nonlinear resistors with memory, hence named memristors [1]. Memristors are axially defined by a relationship between electric charge and magnetic flux [1, 2]. It is known to be flux controlled or charge controlled, depending on whether this relationship can be expressed as a single-valued function of the flux-linkage ($\phi$) or charge ($q$).
