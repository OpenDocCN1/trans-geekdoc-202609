This diagram type is created specifically for SecML. The data interface diagram (DID) is used to provide the cybersecurity engineer an understanding of data flow in the system of interest. It models the flow of data into and out of any system. The concept is to look at any system or subsystem and diagram all interfaces for data to flow into and out of the system of interest. Any place that data can flow is an area for security concerns. Data flowing outward can lead to data exfiltration. Data flowing inward can lead to malware being introduced to the system. This is shown in [Figure 15.15](#).

![](bbox=[0.153, 0.287, 0.487, 0.505])

**Figure 15.15** Data interface diagram.

[Figure 15.16](#) shows the specific elements of the data interface diagram.

| Element | Description |
|---|---|
| ← | Direction of communication flow |
| ▯ | A box represents a specific interface to a system or subsystem. |
| ◀▯ | Interface with only outbound communication. |
| ◀▯▶ | Interface with both inbound and outbound communication. |
| ◀▯X▶ | An interface with an X in it is an interface that has some countermeasure implemented for attacks. |
| ² ◀▯X▶ | In interface with a countermeasure and a number indicates that there are multiple counter measures. |

**Figure 15.16** Data interface diagram elements.