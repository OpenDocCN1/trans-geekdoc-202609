```
< \sensor>
<sensor>
  <name>psd</name>
interface information
<\sensor>
<optimizer>
interface information
<\optimizer>
<radio>
interface information
<\radio>
<user-interface>
interface information
<\user-interface>
<policy-engine>
interface information
<\policy-engine>
<\cognitive-controller>
```

In this listing, each type of component is defined. Because a cognitive radio will likely have multiple input methods for gathering information, the cognitive controller can define and connect to multiple sensors. Here, the cognitive radio has a sensor to collect the PSD of the radio environment as well as a sensor that collects radio performance meters. Each is described by a specific name that the cognitive controller uses to identify the sensor when collecting information.

# 2.4 Artificial Intelligence in Wireless Communications

Successful cognitive radios are aware, can learn, and can take action for any situation that might arise. Applications range from voice communications under low power conditions to communications in high interference zones to more complex, critical, and hostile military networks of interoperating vehicles and soldiers with many different network needs. A radio must respond to these scenarios and adapt the many parameters that define their waveform and protocols. These radios do not require learning; instead, they need highly sophisticated learning and decision-making capabilities.

Machine learning has been well documented and received both criticisms [13] and praise [14]. Successful applications of AI are often limited to narrowly defined, well-bounded applications. While waveform adaptation is a bounded problem, the technical demands for intelligence in a radio exceed those normally associated with successful applications of classic intelligence techniques, such as expert systems or neural networks. Waveform