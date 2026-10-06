# 5 Memristors and Their Applications 115

to the attacker, while the other read pulse is private and is known only to the authorized user. Thus, an attacker cannot restore the memristance value to its original, which was created by the second pulse with its nonpublic parameters, even though they can revert the drift created by the first pulse. This memristance drift can be detected by an authorized user and thus help in determining possible tampering.

# 5.8.6 Nanoelectronics-Based Forensics (NanoForensics)

Digital forensics involve the recovery of data from hardware. For forensic applications, digital logic gates based on memristors utilize the run-time drift property of memristors.

When logic 0 is applied to an input, there will be no change in memristance value. But when logic 1 is applied, there is a drift in the memristance value of that particular memristor. The number of logic 1s applied to the input determines the amount of drift. Consider a memristor-based threshold logic (MTL) (Figure 5.18), realizing an AND function. The location of the gate within the circuit determines the number of 1s received by its input. Thus, the memristance drift at the inputs of different gates will differ.

The number of 1s that are received by input is determined by measuring the memristance drift of that particular memristor and, in the same way, can be determined for all the memristors in the circuit. These measurements can help make a forensic analysis. If no memristance drift was observed in any of the memristors, then it can be concluded that the hardware was not used at all.

![](bbox=[0.135, 0.503, 0.855, 0.888])