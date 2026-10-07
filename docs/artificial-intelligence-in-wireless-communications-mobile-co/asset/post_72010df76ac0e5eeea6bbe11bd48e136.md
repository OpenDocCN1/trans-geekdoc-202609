
for a number of nodes, and discussion about distributing the processing throughout the network are discussed in Chapter 7.

## 5.4.1 Details of Chromosome Structure

The WSGA's chromosome structure differs from most traditional GAs because of the variable number of bits used to represent any gene. Most GAs use a single data type or number of bits per gene, but to better represent various radio capabilities, the WSGA uses a flexible representation. For example, a radio might be capable of thousands of center frequencies over multiple gigahertz but has only a few modulations from which to choose. The chromosome can therefore give a large number of bits to the frequency gene and a small number to the modulation and the transmit power genes, as shown in Figure 5.6. A key result of this structure is that it makes the GA independent of what radio it is optimizing.

| 20 genes = 1x10⁶ values |
| :--- | :--- |
| Center Frequency | ... |
| 4 genes = 16 values | 6 genes = 64 values |
| ... | Modulation | Transmit Power |

**Figure 5.6** Representation of the WSGA's chromosome with variable bit representations of genes.

The variable bit representation is a result of the SDR platform definition file [18]. The platform definition file includes an XML file that looks very similar to the XML listing in Section 2.3.5 to represent the waveform bounds, as well as a DTD file to represent the basic waveform order. Instead of providing an explicit value for each knob, though, the definition XML file provides the range of values each knob may have. The definition file can be thought of representing the possible genes in the chromosome while the waveform XML file represents the specific gene. As an example, Figure 5.7 is the representation of the frequency range for a radio capable of transmitting from 400 to 500 MHz in steps of 1 kHz and from 2.3 to 2.5 GHz in steps of 100 kHz. It also says that the radio can transmit in the 400 MHz range from 0 to 100 dBm in steps of 0.1 dBm and at 2.3 GHz from 0 to 20 dBm in steps of 0.1 dBm. This XML example shows how both continuous values well as discrete jumps in values can be represented. The full XML listing is located in Appendix D.

# Genetic Algorithms for Radio Optimization

```
...
<Tx>
  <PHY>
    <tx_freq>
      <min unit="kHz">400000</min>
      <max unit="kHz">500000</max>
      <step unit="kHz">1</step>
    </tx_freq>
    <tx_power>
      <min unit="dBm">0</min>
      <max unit="dBm">100</max>
      <step unit="dBm">0.1</step>
    </tx_power>
  </rf>
  <rf>
    <tx_freq>
      <min unit="kHz">2300000</min>
      <max unit="kHz">2500000</max>
      <step unit="kHz">100</step>
    </tx_freq>
    <tx_power>
      <min unit="dBm">0</min>
      <max unit="dBm">20</max>
      <step unit="dBm">0.1</step>
    </tx_power>
  </rf>
...
```

**Figure 5.7** Waveform representation in XML.

The XML file provides the bounds and step size, and therefore the number of bits required to represent any possible genetic value for the knob in the chromosome. The DTD file provides the minimum representation of the waveform to structure the chromosome and understand how to parse the XML file. A brief slice of the DTD file is shown in Figure 5.8 while the full listing is in Appendix D. The WSGA uses the DTD representation to know what genes are available and builds each gene from the XML file above. The logic to accomplish this first parses the XML and DTD files into trees that can be walked. The algorithm removes and eliminates elements that contain #PCDATA, which indicates that the element contains data (min, max, step element). The algorithm then walks the DTD tree looking for leaf nodes on the tree, which are now the elements that describe the tree after the min, max, and step elements are removed. Each of the leaf nodes are names of genes. Each gene has the minimum and maximum value it can contain as well as a step value between the two endpoints. The range represented is easily calculated as $(max-min)/step$ and a $[log2()]$ of this value provides the minimum number of bits required to represent the possible values of the gene.

# Artificial Intelligence in Wireless Communications

```
<!ELEMENT waveform (Tx,Rx)>
<!ATLLIST waveform type #CDATA "analog/digital">
<!ELEMENT Tx (PHY,LINK)>
<!ELEMENT PHY (rf,mod)>
<!ELEMENT rf (tx_freq+,tx_power+)>
<!ELEMENT tx_freq (min,max,step)>
<!ELEMENT min (#PCDATA)>
<!ELEMENT max (#PCDATA)>
<!ELEMENT step (min,max,step)>
<!ELEMENT tx_power (#PCDATA)>
<!ELEMENT min (#PCDATA)>
<!ELEMENT max (#PCDATA)>
<!ELEMENT step (#PCDATA)>
```

Figure 5.8 DTD of waveform representation.

Likewise, this information is used in reverse to decrypt the genetic code; the bits representing the gene are an index of *step* steps above the *min* value. As long as the result is less than *max*, the gene representation is valid.

When more than one node of the same name exists, an index is used to address the gene. Multiple nodes of this sort are used when continuous ranges do not exist in a radio, as support for different frequency bands. The number of nodes is indexed into a set of bits and of the rest of the gene is made up of the minimum number of bits required to represent the maximum range of any of the nodes. The position index identifies which range should be used to decrypt the gene.

This method to build chromosomes allows easy representation of a radio's capabilities in XML. The genetic algorithm behaves exactly the same regardless of the radio attached as long as the description is valid in the XML file. The XML and DTD are powerful tools to represent the radio that effectively allow the genetic algorithm to design itself around the radio system, making it platform-independent.

## 5.4.2 Objective Function Definition

XML and DTD files provide the mechanism for generic representation of radio platform capabilities. The next part of the cognitive engine GA implementation is the definition of the objective functions. As discussed in the previous chapter, there are many objective functions and different implementations. We presented a few of the objective functions so far.

Genetic Algorithms for Radio Optimization 91

of looking at the functions. The objective functions, like the radio platform, are likely to improve mathematically and representationally over time. It is important, then, the cognitive engine can be easily adapted to new objective functions.

Again, DTD and XML play their role in this problem along with the use of shared object libraries. The GA is fed the objective functions in the form of an XML file that describes what the library holds. The library is compiled as a shared object that allows dynamic, run-time linking. The GA can then link to the library, pull out the required objectives, and close the library as required. Then, when new objectives are introduced or better mathematical representations are found for the existing objectives, the library can be compiled separately from the rest of the engine and uploaded to the cognitive radios for the next optimization process. The XML file that the GA receives contains the list of available, so during evaluation, the objective functions are referenced by name in the library. The library processes the objective and returns a solution. The important aspect of this is in the function prototype. Each function representation is in the form:

```
float <function_name>(radio_hw_def *knobs, radio_meters *meters)
```

The radio_hw_def data structure is a class that contains the information to map the chromosome representation to the radio platform capabilities. The structure is built from the XML and DTD files that define the chromosome as discussed previously. The radio_meters is a simple data structure that holds the results of the objective calculation. Each function returns a number as part of its result. The WSGA solves a maximization problem, and to allow the generic, dynamic representation of fitness values, this value is a representation of the performance of the objective function as a maximization metric. Simply put, when an objective function should be maximized (e.g., throughput, SINR), the returned fitness is the objective itself. when the objective is minimized the inverse. These fitness values are then stored as credits to represent an individuals fitness. The ranking and selection is based off the values of the credits, which, again, are designed to be compared in a maximization problem. Meanwhile, each member holds a copy of the meters data structure used in the post analysis of the algorithm's performance.

## 5.4.3 Optimal Individual Selection

Pareto ranking only goes far to provide a population of optimal/near-optimal and nondominated individuals. However, from this point, the algorithm needs to return a single, final individual as the solution to the
