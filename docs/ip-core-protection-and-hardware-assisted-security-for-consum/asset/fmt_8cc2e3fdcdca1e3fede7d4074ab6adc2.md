
Koushanfar *et al.* ([2005](#Chapter4.html#c04_bib8)) devised a dynamic watermarking process to shield a DSP IP core ([Coussy *et al.*, 2009](#Chapter4.html#c04_bib3)). A set of design and timing constraints in the form of vendor watermark is embedded in the IP core. In this approach, a vendor’s signature is transformed into its equivalent binary form where each digit (0 or 1) indicates a watermarking constraint. More specifically, these watermarking constraints are embedded in register allocation and binding phase. This is achieved by adding additional edges in the equivalent colored interval graph (CIG) of the IP design. In a CIG, each node indicates a storage variable. The lifetime of a storage variable lies between the time it is created (value written into it) and the last use (value read from it). An edge between two nodes indicates there is an overlap in lifetime between those storage variables. The color of the node indicates the allocated register of that corresponding storage variable. Therefore, two storage variables whose lifetimes overlap cannot be stored in the same register. In other words, two nodes having a common edge between them cannot have same node color. Thus, adding additional edges in the CIG as watermarking constraints will force to execute two storage variables in two different registers. The overview of Koushanfar *et al.* ([2005](#Chapter4.html#c04_bib8)) approach is shown in [Figure 4.3](#Chapter4.html#c04_fig3).

![image](OEBPS/images/PBCS0600-04-f03.jpg)

Figure 4.3 Top level diagram of watermarking process of Koushanfar et al. ([2005](#Chapter4.html#c04_bib8))

Unlike dual variable (0 and 1) signature encoding rule in Koushanfar *et al.* ([2005](#Chapter4.html#c04_bib8)), Sengupta and Bhadauria (2016) devised a single phase multi-variable (combination of four) watermarking methodology to protect a reusable IP core. Each variable which carries a unique encoding rule (unknown to an attacker) adds an additional edge between two node pair in the CIG. Thus, Sengupta *et al.* (2016) embed a more robust and tamper-proof watermark compared with Koushanfar *et al.* ([2005](#Chapter4.html#c04_bib8)). Due to insertion of watermarking constraints in both Sengupta *et al.* (2016) and Koushanfar *et al.* ([2005](#Chapter4.html#c04_bib8)) area overhead may occur. Therefore, to minimize the design cost, a low-cost design solution is explored through particle swarm optimization in Sengupta *et al.* (2016). The embedded signature can be detected by inspecting the datapath hardware description language (HDL) file of the watermarked IP. As the encoding rules are hidden to an attacker, it is almost impossible to identify the watermarking constraints from its datapath. The overview of Sengupta *et al.* (2016) approach is shown in [Figure 4.4](#Chapter4.html#c04_fig4).

![image](OEBPS/images/PBCS0600-04-f04.jpg)

Figure 4.4 Top level diagram of watermarking process of Sengupta et al. (2016)

Sengupta *et al.* ([2018](#Chapter4.html#c04_bib22)) devised a triple-phase watermarking process to secure a DSP IP core (Sengupta and Sedaghat, 2011). In this approach, vendor signature consists of 7-variables. The IP owner signature as watermarking constraints is embedded in three dissimilar (but interconnected) phases of HLS, i.e., scheduling phase, hardware allocation phase, and register allocation phase. Due to insertion of watermarking constraints in three different phases, vendor signature is distributed throughout the IP core design. Thus, complete removal or malicious alteration of the watermark is extremely difficult. Besides, embedding 7-variable encoding makes this approach tremendously strong. Additionally, the watermark in scheduling phase is independent of the watermark in hardware allocation and register allocation phase. Similarly, the watermark in register allocation phase is independent of both scheduling and hardware allocation phase watermarks. Due to these benefits, the triple-phase watermarking approach is tremendously robust as well as tamper resistant. The embedded signature can be detected by inspecting the datapath and controller HDL file of the watermarked IP. As the watermarking constraints are well dispersed in the IP design and the encoding rules are hidden to an attacker, it is extremely difficult to identify the watermarking constraints from its datapath and controller by an adversary. The overview of Sengupta *et al.* ([2018](#Chapter4.html#c04_bib22)) approach is shown in [Figure 4.5](#Chapter4.html#c04_fig5).

![image](OEBPS/images/PBCS0600-04-f05.jpg)

Figure 4.5 Top level diagram of watermarking process of Sengupta et al. ([2018](#Chapter4.html#c04_bib22))

### 4.3 Design process of watermarked IP core/hardware

As mentioned earlier, IP/hardware watermarking is a process of embedding owner’s signature covertly in the design of an IP/hardware to proof his/her ownership in case of any conflict ([Sengupta *et al.*, 2017](#Chapter4.html#c04_bib21)). In this section, we discuss problem formulation and design process of two (i.e., single-phase and triple-phase) IP core watermarking processes in detail. Both the approaches are demonstrated through a motivational example.

#### 4.3.1 Problem formulation

**Inputs:** (i) DSP application, (ii) resource configuration, (iii) module library, and (iv) vendor signature.

**Output:** Watermarked IP core design.

Sengupta *et al.* (2016, [2018](#Chapter4.html#c04_bib22)) accepted DSP application in the form of data flow graph (DFG), module library in the form of NanGate 15-nm technology ([NanGate Open Cell Library, 2018](#Chapter4.html#c04_bib12)) or 90-nm library/other library, and user-specified resource configuration (*R*). Here, *R* is represented as: *N(X*[1])*, N*(*X*[2])*, …, N*(*X*[*D*]), and *N*(*X*[*D*]) indicating the number of resources of type *X*[*D*]. Sengupta *et al.* (2016) proposed a vendor signature that contains four encoding variables used for generating watermarking constraints. These watermarking constraints are embedded in a single HLS phase of a DSP IP core design process. On the other hand, [Sengupta *et al.* (2018](#Chapter4.html#c04_bib22)) proposed a vendor signature that contains seven encoding variables. These watermarking constraints are embedded in three different HLS design phases of a DSP IP core design process. [Figure 4.6](#Chapter4.html#c04_fig6) depicts the inputs and output of an IP core watermarking process.

![image](OEBPS/images/PBCS0600-04-f06.jpg)

Figure 4.6 Inputs and output for watermarked IP core

**Target platform:** The targeted platform for Sengupta *et al.* (2016, [2018](#Chapter4.html#c04_bib22)) watermarking approach is any modern computer-aided design (CAD) tool. Both watermarking approaches generate the final watermarked DSP IP core design in HDL; therefore, any HDL-based CAD tool used for generating IP core can easily adopt these watermarking algorithms.

#### 4.3.2 Design process of single-phase watermarked IP core/hardware

In this section, we describe the design of a watermarked DSP IP core/hardware (especially for DSP/multimedia applications).

##### 4.3.2.1 Process of generating DFG from a DSP function

In this section, as an example, we discuss how to obtain DFG of a digital signal processing filter from its corresponding transfer function. We demonstrate the process through a popular DSP application, i.e., finite impulse response (FIR) filter. The generic equation of FIR filter can be expressed as follows:

![image](OEBPS/images/c04_eqn2.gif)

where *M* is the filter order of a digital FIR, *h*[*i*] is the FIR coefficient, *x*(*n*) is input impulse, and *y*(*n*) is output impulse.

Using the above expression, a 7th order (8-tap) FIR filter can be represented as:

![image](OEBPS/images/c04_eqn3.gif)
