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

The XML file provides the bounds and step size, and therefore the number of bits required to represent any possible genetic value for the knob in the chromosome. The DTD file provides the minimum representation of the waveform to structure the chromosome and understand how to parse the XML file. A brief slice of the DTD file is shown in Figure 5.8 while the full listing is in Appendix D. The WSGA uses the DTD representation to know what genes are available and builds each gene from the XML file above. The logic to accomplish this first parses the XML and DTD files into trees that can be walked. The algorithm removes and eliminates elements that contain #PCDATA, which indicates that the element contains data (min, max, step element). The algorithm then walks the DTD tree looking for leaf nodes on the tree, which are now the elements that describe the tree after the min, max, and step elements are removed. Each of the leaf nodes are names of genes. Each gene has the minimum and maximum value it can contain as well as a step value between the two endpoints. The range represented is easily calculated as $(max-min)/step$ and a $[log2()]$ of this value provides the