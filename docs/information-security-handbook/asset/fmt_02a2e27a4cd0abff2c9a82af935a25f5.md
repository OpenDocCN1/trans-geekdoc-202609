
For the detection of network anomalies/vulnerabilities, protocols and policies related to network security are continuously developed. Many policies and protocols will apply to the planes and architecture of SDN. In SDN, it is, and it will be, essential to impose the implementation of developed policies such as transport layer security (`TLS`). The interface between different components of the network has the possibility to present significant vulnerabilities about interoperability between devices of multiple vendor and communication of control/data across new interfaces. SDN provides the creation of flow rules and policies dynamically, as well as the ability to program the network using `API`. Quite a few solutions have been proposed to the issues relating to a conflict of network policy from multiple applications in the `[19,23,24,[25](#ch02.xhtml#ref2_25),26,27]`. `NICE` `[19]` is proposed, in which the `OF` application is tested by combining the model checking with symbolic execution. The binary decision diagram has been proposed in `[23]` for testing of intra-switch misconfigurations within particular flow tables. Similarly, `[24]` uses modulo theories and assertion sets for the purpose of verifying policies of flow. In `[25]`, authors proposed the approach for diagnosing configuration problems of the network using static analysis. `[26]` has detected the loops in the routing table, paths, etc., by modeling the graph and studying the invariants by interrupting flow rules before reaching the network. `[27]` is also a tool for checking the policies in real time that gradually checks the changing state. Further deployments of experiments could estimate the bond and the gap among network characteristics and theoretical models.

### [2.2.7 Data Leakage](#ch02.xhtml#c_sec2_002_007)

For packet handling, there are diversifications of possible actions explained in OpenFlow switch specification `[2]`. Those actions include packet dropping, forwarding, and sending to the controller. By means of packet-processing timing analysis, an attacker decides the action to apply on specific types of packets. For example, network packet entry and out time would be shorter than a processing time on a controller. This can be done by discovering the proactive and reactive configuration of switches by an attacker. Another open challenge in SDN is storage of credentials that must be secure, e.g., certificates and keys for multiple logical networks. Side-channel attacks and a security mechanism credential management are described in data leakage. Side-channel attack occurs on the data plane of SDN. The attacker can compromise the switches and gain secure information of implementation of any system or from targeted resources. Multiple OpenFlow logical switches are initiated on top of `OF` enabled switch by `OF-Config`. Different customers have assigned logical entity, and those logical networks are linked with credentials, e.g., certificates and keys. If those credentials are not securely contained, then this can be compromised by attacker and lead to data leakage. The solution is to use a strong encryption algorithm to secure the elements and resources of network.

[Table 2.2](#ch02.xhtml#table2_2) illustrate the inappropriate use of security features that can affect all planes of SDN architecture. The table shows categorization of SDN attacks that is associated with SDN planes.

 [Table 2.2 Categorization of Attacks Associated with SDN Planes](#ch02.xhtml#Ttable2_2) 

| SDN Security Attacks || Affected SDN Planes |

| --- | --- |

|  || Application Plane || App-Ctrl Interface || Control Plane || Ctrl-Data Interface || Data Plane |

| Data Modification ||  ||  || **✓** || **✓** || **✓** |

| --- | --- | --- | --- | --- | --- |

| Unauthorized controller access ||  ||  || **✓** || **✓** || **✓** |

| Unauthorized Application || **✓** || **✓** || **✓** ||  ||  |

| Side Channel Attack ||  ||  ||  ||  || **✓** |

| Network Manipulation ||  ||  || **✓** ||  ||  |

| Traffic Diversion ||  ||  ||  ||  || **✓** |

| API Exploitation || **✓** || **✓** ||  ||  ||  |

| Credential Management ||  ||  ||  ||  || **✓** |

| Flow Table Overflow Attack ||  ||  ||  ||  || **✓** |

| Malicious Application || **✓** || **✓** || **✓** ||  ||  |

| Configuration Issues (Lack of secure Provisioning and TLS) || **✓** || **✓** || **✓** || **✓** || **✓** |

| Traffic Sniffing ||  ||  || **✓** || **✓** || **✓** |

|  |

## [2.3 Security Analyses and Research Challenges](#ch02.xhtml#c_sec2_3)

### [2.3.1 SDN Security Analyses](#ch02.xhtml#c_sec2_003_001)

Several SDN security analyses lead this study `[18,31,33,34,35,40,41,46,[60](#ch02.xhtml#ref2_60),[61](#ch02.xhtml#ref2_61),[62](#ch02.xhtml#ref2_62)]`. This literature has established the relationship between the elements in framework of SDN in order to introduce new vulnerabilities. However, the recent analyses identify the enhancement of security in SDN. We know that `OpenFlow` is the protocol and common technology of SDN, and `[34]` an analysis of `OF` protocol is completed by STRIDE threat exploration `[[63](#ch02.xhtml#ref2_63)]`.

The described security analyses are relatively presented in Table 2.1 with respect of SDN layers and their solutions provided in different research work. The `OpenFlow` and SDN framework support application to modify the state of network in switches through protocol. As a result, the issues related to control and data plane, and the data-control interface, while rare `[1,33,60]`, highlight the security threats of application hosting by third parties.

### [2.3.2 Scenarios](#ch02.xhtml#c_sec2_003_002)

#### [2.3.2.1 Scenario 1](#ch02.xhtml#c_sec2_003_002_001)

The network flow is being diverted by malicious application. As it found, the network flow might change the path to reach the destination. It can happen by fraudulent rules insertion through malicious application. `OF`-enabled switches forward the whole traffic using flow rules defined by the controller. The attacker compromised the controller to access the application, making the existing application malicious by adding new rules or modifying existing rules. By those modified rules, flow entries could change in the flow table and direction would be changed due to attack.

#### [2.3.2.2 Scenario 2](#ch02.xhtml#c_sec2_003_002_002)

In the analysis of traffic diversion in the SDN forwarding plane, the network flow traffic can also change its path due to link failure. In the data plane, when the link is a failure or faulty, the `OF`-enabled switches change the path for flow arriving from source. Switches can fail over the flow that is affected due to any reason or link failure to another path. The controller calculates the multiple paths and pre-establishes them; when link failure occurs, it can take a new path to reach destination. This is general failure and take network traffic to other path.

#### [2.3.2.3 Scenario 3](#ch02.xhtml#c_sec2_003_002_003)

In case of congestion, it occurs when the link is carrying too much data when arriving from controller. This can cause network traffic loss and reduction of throughput, and link congestion occurred due to DoS attack. The attacker sends too much malicious traffic to overload the `OF`-enabled switches. In SDN, each switch records the path load information of the outgoing link. If the controller calculates the paths using a proactive approach and congestion occurs on links, the typical effect will be packet loss, but packets might change the path due to a pre-calculated/pre-established path by the controller to reach the destination.

### [2.3.3 Research Challenges](#ch02.xhtml#c_sec2_003_003)
