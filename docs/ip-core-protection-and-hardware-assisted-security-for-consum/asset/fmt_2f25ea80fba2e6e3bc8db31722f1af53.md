
As discussed earlier, at the core of a CE device, several DSP cores used for data intensive or control intensive functions are present. These DSP cores are IP cores in the form of SoC platform which are responsible for data processing of large chunks of data. For example, digital video cameras almost always have a second built-in microprocessor, dedicated to video calculations. This process is called as digital signal processor (DSP)—its role is to perform repetitive mathematical tasks in real time. In simpler terms, while our smart phone’s main microprocessor is checking to see if we have any incoming calls, second processor will simultaneously run the email in the background, manage Wi-Fi signal, check when video is coming through the lens, etc., and all such calculations are taken care by second dedicated processor, DSP core. A thematic example is shown in [Figure 1.4](#Chapter1.html#c01_fig4). As evident from this figure, the multimedia/DSP core (JPEG compression/decompression IP core) plays a significant role in the successful operation of a CE device. Similarly, other DSP cores such as discrete cosine transformation (DCT) core, fast Fourier transform (FFT), digital filters, etc., also play a critical role in CE device design. For example, FIR filter helps to improve the audio quality and the cellular infrastructure in the CE device. Protection of such complex DSP/multimedia cores relies on the high-level synthesis (i.e., architectural synthesis) as backbone design framework. This is because such complex DSP cores that comprise 15K–60K gates never initiates the design process from lower abstraction level. Furthermore, selecting/controlling the architecture of these DSP cores is seamlessly possible through high-level synthesis framework as it includes design space exploration (DSE) module (driven through intelligent evolutionary algorithms). This is not possible if these designs have to start from register-transfer (RT)/gate-level/lower levels.

![image](OEBPS/images/PBCS0600-01-f04.jpg)

Figure 1.4 DSP/multimedia core in CE device: digital camera

A protection/security mechanism of such complex cores is thus intertwined with the high-level synthesis design process. For such hardware, protection is mostly applied during higher levels of abstraction (i.e., during high-level synthesis). On the contrary, security/protection mechanism of less complex hardware such as adder, encoder, decoder, etc., can be performed at lower levels such as RT level/gate level, etc. [Figure 1.5](#Chapter1.html#c01_fig5) shows the classification of different hardware-assisted securities and IP core protection mechanisms at higher and lower levels of abstraction. As discussed, for DSP/multimedia cores such as infinite impulse response (IIR) filter, FIR, JPEG, etc., protection/security algorithms are applied at higher levels of abstraction which enables the constraints of the security algorithms to propagate to the lower levels also through RT level/gate level synthesis.

![image](OEBPS/images/PBCS0600-01-f05.jpg)

Figure 1.5. Hardware protection mechanisms

## 1.4.1 Security and protection methodologies available for IP core/hardware

Some of the recognized protection mechanisms used extensively for DSP IP cores of CE designs that depend on the threat model/vulnerability are watermarking, fingerprinting, hardware metering, computational forensic engineering, Trojan security, structural obfuscation, functional obfuscation, physically unclonable functions (PUF), and patents/copyrights ([Alkabani *et al.*, 2007](#Chapter1.html#c01_bib1); [Castillo *et al.*, 2007](#Chapter1.html#c01_bib3); Christof and Jan, 2009; [Hong and Potkonjak, 1999](#Chapter1.html#c01_bib6); [Koushanfar *et al.*, 2005](#Chapter1.html#c01_bib8); [Marvel, 2005](#Chapter1.html#c01_bib9); [Ni *et al.*, 2006](#Chapter1.html#c01_bib16); [Sengupta and Roy, 2018a](#Chapter1.html#c01_bib24), [2018b](#Chapter1.html#c01_bib25)). [Figure 1.6](#Chapter1.html#c01_fig6) shows an overview of threat models along with its hardware security countermeasures for CE device.

![image](OEBPS/images/PBCS0600-01-f06.jpg)

Figure 1.6 Overview of some common hardware threats and its countermeasures

### (i) IP core/hardware watermarking

This hardware protection mechanism is employed when the hardware threat anticipated to be false claim of ownership. This threat model is basically because of ownership abuse or false claim of IP core ownership or piracy. Although watermarking protects against the aforesaid threats, it can only detect and not prevent the threats. In other words, watermarking approach is capable of providing passive form of protection to an IP core. More details on this protection mechanism are presented in Chapter 4.

### (ii) Computational forensic engineering (digital forensics) for IP cores

This hardware protection mechanism is employed when the hardware threat under question is ownership abuse or false claim of IP core ownership or piracy. It has the same threat model as watermarking and provides the detection of the legal owner in case of ownership conflicts. The objective of computational forensic engineering (CFE) is to recognize the individual that produced the IP. It examines certain properties of a given IP and measures the probability that a particular individual has produced it. The CFE method identifies from a group of synthesis tool, the one which is employed to make a specific IP design. It is to be noted that this approach is also capable of providing passive forms of protection to an IP core. More details on this protection mechanism are presented in Chapter 6.

### (iii) Hardware metering

This is the method of monitoring an IC. Some of the effective methods are to physically identify serial numbers on chips or storing unique identifiers in its memory ([Alkabani and Koushanfar, 2007](#Chapter1.html#c01_bib2); [Roy *et al.*, 2008](#Chapter1.html#c01_bib18)). The taxonomy of hardware metering is shown in [Figure 1.7](#Chapter1.html#c01_fig7). Hardware metering can be broadly classified into two categories: non-functional and functional. In non-functional identification method, a unique ID is created that is separate from the chip functionality. However, it can have the following drawbacks:

1. Vulnerability to cloning and/or removal;
2. Once chip is tagged, foundry can copy same tag on other chips or simply remove tag so chip cannot be traced;
3. Possibility to overproduction;
4. Foundry can produce multiple chips with same tag;
5. Out of millions of chips, probability of finding two matching tags is small.

![image](OEBPS/images/PBCS0600-01-f07.jpg)

Figure 1.7 Taxonomy of hardware metering methods
