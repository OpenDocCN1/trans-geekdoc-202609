![](bbox=[0.358, 0.88, 0.642, 0.198])

**FIGURE 6.9** The idea of dual read pulses to detect run-time tampering in a memristor device; the dotted line represents the current resistance state of the memristor.

and then the complement of the known value is written in the memristor, and these values are then read back. The compared results suggest its trustworthiness. The compared results would be the same if there is no formation occurring in the memristor, and this will facilitate writing in the memristor [39]. The compared read output will be different if the memristor is already formed, which means that the circuit has been tampered with. Its like making a mirror image of information and overlapping to check whether they match or not; if overlapped, the device is not formed, but if, then it might have formed, that is, used.

# # 6.4.3 Run-Time Tamper Detection

The main idea to detect an unauthorized read operation in memristor-based memories is to observe the unauthorized drift in memristance. To hide an unauthorized read, the attackers would try to reinstate the memristance of the memristor back to its actual state by ‘un-reading’; this can be achieved by applying an opposite polarity read with a pulse of the same magnitude and duration [40]. To prevent such restoring of memristance, the read operation is corrected, as shown in Figure 6.9. In this modified operation, two consecutive read pulses are used. Out of these two pulses, the first is public (known to the attacker as well) and the second is private (only known to the authorized user) [41, 62, 63, 64]. In such a case, the attacker will not be able to restore the memristance after reading, the second pulse is unknown. Since the memristance value due to an unauthorized read will differ from the original value before reading, the authorized user can monitor this difference and become aware of it tampering.

# ## 6.5 MEMRISTOR-BASED FORENSICS

In this digital world, the evidence for any crime could also be seen in the form of 0s and 1s. This digital evident may get tampered with the culprit. To retrieve these shards of evidence, forensics research is done on those devices. Devices made from CMOSs are sometimes in a condition that retrieval of data is either impossible or time-consuming. A Memristor-based memory of the digital device is relatively easier and less time-consuming compared to a CMOS-based device [42].

# ### 6.5.1 The Architecture of Memristor-Based Forensics

The run-time drift property of memristors can be used in memristor-dependent digital logic gates. The drift in the memristance will provide the sets of the inputs applied in the past to the memristor with the help of forensics. Memristor-dependent threshold gates were proposed by Rajendran in 2012 [43]. In this memristor-dependent threshold logic (MTL), memristors are utilized as weights for the input of the gates. A three-input