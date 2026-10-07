# XML DTD Representation of the Cognitive Components

```
<LINK>
<frame>
  <tx_pkt_size units="bytes">
    <min>1</min>
    <max>1500</max>
    <step>1</step>
  </tx_pkt_size>
  <tx_access_code>None</tx_access_code>
</frame>
</LINK>
<Tx>
<waveform>
```

# D.2 Objectives Sensor

sensor_objectives.dtd

```
<!ELEMENT sensor>
<!ATTLIST sensor>
<!ELEMENT awgn>
<!ATTLIST awgn type="float" typedef="(phy,mac,sys) "phy"" #CDATA #REQUIRED>
<!ELEMENT fer>
<!ATTLIST fer type="float" typedef="(phy,mac,sys) "mac"" #CDATA #REQUIRED>
<!ELEMENT sinr>
<!ATTLIST sinr type="float" typedef="(phy,mac,sys) "phy"" #CDATA #REQUIRED>
<!ELEMENT throughput>
<!ATTLIST throughput type="float" typedef="(phy,mac,sys) "phy"" #CDATA #REQUIRED>
<!ELEMENT bandwidth>
<!ATTLIST bandwidth type="float" typedef="(phy,mac,sys) "phy"" #CDATA #REQUIRED>
<!ELEMENT spectralefficiency>
<!ATTLIST spectralefficiency type="float" typedef="(phy,mac,sys) "phy"" #CDATA #REQUIRED>
<!ELEMENT interference>
<!ATTLIST interference type="float" typedef="(phy,mac,sys) "phy"" #CDATA #REQUIRED>
<!ELEMENT powerconsumption>
<!ATTLIST powerconsumption type="float" typedef="(phy,mac,sys) "sys"" #CDATA #REQUIRED>
<!ELEMENT computationalcomplexity>
<!ATTLIST computationalcomplexity type="float" typedef="(phy,mac,sys) "sys"" #REQUIRED>
```

sensor_objectives.xml

```
<?xml version="1.0"?>
```