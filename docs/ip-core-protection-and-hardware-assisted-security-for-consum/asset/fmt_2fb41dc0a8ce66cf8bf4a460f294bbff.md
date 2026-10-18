
## 1. Hardware Obfuscation

Obfuscation is the process of transforming an original application or design into its functionally equivalent form to make the reverse engineering process significantly more challenging ([Chakraborty and Bhunia, 2009](#Chapter5.html#c05_bib28)). It can protect an IP core either by obscuring the IP design/code, known as structural obfuscation ([Hada, 2000](#Chapter5.html#c05_bib27); [Sengupta *et al.*, 2017](#Chapter5.html#c05_bib31)) or by generating a locked netlist ([Chakraborty and Bhunia, 2009](#Chapter5.html#c05_bib28)). A person who has the proper knowledge of the design of the correct key combination can only use it. In other words, structural obfuscation hides the functionality of an IP core whereas functional obfuscation hides the implementation of an IP core.

## 2. Computational Forensic Engineering

Computational forensic engineering (CFE) is a signature-free driven process which can be performed in three steps, feature collection, feature extraction, and IP validation ([Sengupta and Kachave, 2018](#Chapter5.html#c05_bib30)). It tries to identify a list of features that can be used to identify an IP core uniquely ([Wong *et al.*, 2004](#Chapter5.html#c05_bib29)). In case of ownership conflict, these features can be used to recognize the real owner of the IP core.

## 3. Watermark

IP protection of a single entity (for IP seller only) can be achieved by embedding a seller watermark in to the IP core design. Watermark can be inserted either at lower design abstraction level (Ziener and Teich, [2006](#Chapter5.html#c05_bib20), [2008](#Chapter5.html#c05_bib22); [Nie *et al.*, 2013](#Chapter5.html#c05_bib21)) or at higher design abstraction level ([Sengupta and Bhadauria, 2016](#Chapter5.html#c05_bib14); [Koushanfar *et al.*, 2005](#Chapter5.html#c05_bib18); [Hong and Potkonjak, 1999](#Chapter5.html#c05_bib23); [Le Gal and Bossuet, 2012](#Chapter5.html#c05_bib24); [Sengupta *et al.*, 2016](#Chapter5.html#c05_bib25)). Watermark at lower design level can be detected from the power supply pins of field programmable gate array (FPGA) ([Ziener and Teich, 2006](#Chapter5.html#c05_bib20)), or from the bit-stream of the IP core design ([Nie *et al.*, 2013](#Chapter5.html#c05_bib21)), or by tracing the voltage ([Ziener and Teich, 2008](#Chapter5.html#c05_bib22)), etc. On the other hand, watermark at higher design level be identified from the datapath and/or the control path of the IP design.

## 5.2.2 Overview on Symmetric IP Core Protection Techniques

The main goal of symmetrical IP core protection is to generating unique one to one mapped IP core between IP user and IP seller. From the seller side, it will not only protect the ownership of the IP seller but also he can identify the traitors among the list of IP buyers. If all the buyers get identical IP from the seller and one of them may unlawfully redistribute it identifying the actual dishonest buyer will become insurmountable ([Gang and Potkonjak, 2007](#Chapter5.html#c05_bib3)). There are only two approaches in the literature which have presented symmetrical IP core protection techniques. In the approach presented in Lach *et al.* ([2001](#Chapter5.html#c05_bib26)), a hidden encrypted mark is embedded into the physical layout of a digital circuit when it is placed and routed onto the FPGA. This mark uniquely identifies both the source of the circuit and original recipient of the circuit, which is also difficult to remove. Thus, the approach provides protection for both the entities (IP buyer and IP seller) but in lower design abstraction level, i.e. layout level, not in higher design abstraction level. On the other hand, the approach presented in Roy and Sengupta ([2017](#Chapter5.html#c05_bib32)) provides symmetrical protection during HLS. This approach embeds hidden buyer’s and seller’s signature constraints as multi-variable fingerprint and watermark during register allocation and scheduling stages of architectural synthesis. Signature embedding process is not time consuming and less complex; additionally, overhead generated due to additional constraints is significantly low. Furthermore, detail explanation of this approach is discussed in the next section.

## 5.3 Symmetrical IP Core Protection for DSP Core

The symmetrical protection approach presented in Roy and Sengupta ([2017](#Chapter5.html#c05_bib32)) covertly inserts fingerprinting and watermarking constraints to protect the IP buyer as well as the IP seller during HLS. Based on the signature constraints provided by a buyer, an IP seller inserts buyer fingerprint with his own watermark; thus, safeguards the privileges of seller and buyer against popular IP threats like IP piracy, IP cloning, false claim of ownership, etc. (discussed in Section 5.1). Both buyer fingerprint and seller watermark taken as input from the respective entities are decoded to obtain the corresponding signature constraints. Firstly, the fingerprinting constraints are embedded in scheduling and register allocation phase within HLS (shown in [Figure 5.3](#Chapter5.html#c05_fig3)). Once the fingerprint implanted design is obtained; then, lastly the watermarking constraints are implanted in register allocation phase. Thus, a DSP IP core design has both fingerprinted and watermarked constraints, in addition to its normal design constraints (i.e. module library, resource configurations, etc.). The multiplexing process for each resource is generated to identify the resource interconnectivity, multiplexer size, and inputs/outputs of the watermarked and fingerprinted design. Using generated multiplexing scheme of each resource, the complete datapath and timing description of the control unit of the DSP IP core are developed. Thus, the final output of a symmetrically protected RTL design of an IP core is created as datapath and controller where each component is designed using hardware description language (HDL).

![image](OEBPS/images/PBCS0600-05-f03.jpg)

Figure 5.3 Symmetrical IP core protection mechanism for DSP cores

Thereafter, these HDL files are fed into computer-aided design (CAD) software for RTL synthesis. It produces optimal gate level description of the respective design. This is then subsequently verified and transformed to corresponding bitstreams for the validation on a programmable hardware. After being validated, it is then fed into CAD tools for physical designing. Lastly, the GDS design file generated is sent to the fab.

### 5.3.1 Problem Formulation

To determine an optimal symmetrically protected design solution for a particular data flow graph (DFG) within user specified area-delay constraints. It may be expressed as:

**Minimize:** Embedding cost (`A[total]`, `L[total]`) for an optimal design solution (`X[i]`), where (`X[i]`) = `N(R[1])`, `N(R[2])`,…, `N(R[D])`; and `N(R[D])` is the number of resource type `R[D]`.

**Subject to:** `A[total]` ≤ `A[cons]` and `L[total]` ≤ `L[cons]` to symmetrically protect an IP core, where `A[total]` and `L[total]` are total area and latency of the symmetrically protected design and `A[cons]` and `L[cons]` are user provided area and latency constraints respectively.

### 5.3.2 Symmetrically Protected Design—Area Evaluation Model

Total design area (`A[total]`) consumed by a symmetrically protected reusable IP core is formulated by the following model ([Roy and Sengupta, 2017](#Chapter5.html#c05_bib32)):

![image](OEBPS/images/c05_eqn1.gif)

Total design area is evaluated by adding total area of hardware resource units (like adder, subtractor, multiplier, etc.), interconnecting units (such as multiplexer and de-multiplexer), and storage units (such as register). The total design area is evaluated for module library of 15-nm NanGate-based technology ([NanGate, 2017](#Chapter5.html#c05_bib33)).

### 5.3.3 Symmetrically Protected Design—Delay Evaluation Model
