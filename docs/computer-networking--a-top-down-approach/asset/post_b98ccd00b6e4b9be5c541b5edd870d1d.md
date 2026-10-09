
The RPC message itself spans lines 02–17, has a message ID value of 101, and contains a single NETCONF `<edit-config>` command, spanning lines 04–15. Line 06 indicates that the running device configuration at the managed device will be changed. Lines 11 and 12 specify the MTU size to be set on the Ethernet0/0 interface.

Once the managed device has changed the interface's MTU size in the configuration, it responds back to the managing server with an OK reply (line 04 below), again within an XML document:

```xml
01 <?xml version="1.0" encoding="UTF-8"?>
02 <rpc-reply message-id="101"
03 xmlns="urn:iETF:params:xml:ns:netconf:base:1.0"
04 <ok/>
05 </rpc-reply>
```

## YANG

YANG is the data modeling language used to precisely specify the structure, syntax, and semantics of network management data used by NETCONF, in much the same way that the SMI is used to specify MIBs in SNMP. All YANG definitions are contained in modules, and an XML document describing a device and its capabilities can be generated from a YANG module.

YANG features a small set of built-in data types (as in the case of SMI) and also allows data modelers to express constraints that must be satisfied by a valid NETCONF configuration—a powerful aid in helping ensure that NETCONF configurations satisfy specified correctness and consistency constraints. YANG is also used to specify NETCONF notifications.

A fuller discussion of YANG is beyond our scope here. For more information, we refer the interested reader to the excellent book [Claise 2019].

## 5.8 Summary

We have now completed our two-chapter journey into the network core—a journey that began with our study of the network layer's data plane in Chapter 4 and finished here with our study of the network layer's control plane. We learned that the control plane is the network-wide logic that controls not only how a datagram is forwarded among routers along an end-to-end path from the source host to the destination host, but also how network-layer components and services are configured and managed.

We learned that there are two broad approaches towards building a control plane: traditional *per-router control* (where a routing algorithm runs in each and every router and the routing component in the router communicates with the routing components in other routers) and *software-defined networking* (SDN) control (where a logically centralized controller computes and distributes the forwarding tables to be used by each and every router). We studied two fundamental routing algorithms for computing least cost paths in a graph—link-state routing and distance-vector routing—in Section 5.2; these algorithms find application in both per-router control and in SDN control. These algorithms are the basis for two widely deployed Internet routing protocols, OSPF and BGP, that we covered in Sections 5.3 and 5.4. We covered the SDN approach to the network-layer control plane in Section 5.5, investigating SDN network-control applications, the SDN controller, and the OpenFlow protocol for communicating between the controller and SDN-controlled devices. In Sections 5.6 and 5.7, we covered some of the nuts and bolts of managing an IP network: ICMP (the Internet Control Message Protocol) and network management using SNMP and NETCONF/YANG.

Having completed our study of the network layer, our journey now takes us one step further down the protocol stack, namely, to the link layer. Like the network layer, the link layer is part of each and every network-connected device. But we will see in the next chapter that the link layer has the much more localized task of moving packets between nodes on the same link or LAN. Although this task may appear on the surface to be rather simple compared with that of the network layer's tasks, we will see that the link layer involves a number of important and fascinating issues that can keep us busy for a long time.

# Homework Problems and Questions

## Chapter 5 Review Questions

- **SECTION 5.1**
  R1. What is meant by a control plane that is based on per-router control? In such cases, when we say the network control and data planes are implemented "monolithically", what do we mean?
  R2. What is meant by a control plane that is based on logically centralized control? In such cases, are the data plane and the control plane implemented within the same device or in separate devices? Explain.

- **SECTION 5.2**
  R3. Compare and contrast the properties of a centralized and a distributed routing algorithm. Give an example of a routing protocol that takes a centralized and a decentralized approach.
  R4. Compare and contrast link-state and distance-vector routing algorithms.
  R5. What is the "count to infinity" problem in distance vector routing?
  R6. Is it necessary that every autonomous system use the same intra-AS routing algorithm? Why or why not?

- **SECTIONS 5.3–5.4**
  R7. Why are different inter-AS and intra-AS protocols used in the Internet?
  R8. True or false: When an OSPF router sends its link state information, it is sent only to those nodes that are its directly attached neighbors. Explain.
  R9. What is meant by an *area* in an OSPF autonomous system? Why was the concept of an area introduced?
  R10. Define and contrast the following terms: subnet, prefix, and *BGP route*.
  R11. How does BGP use the NEXT-HOP attribute? How does it use the AS-PATH attribute?
  R12. Describe how a network administrator of an upper-tier ISP can implement policy when configuring BGP.
  R13. True or false: When a BGP router receives an advertised path from its neighbor, it must add its own identity to the received path and then send that new path on to all of its neighbors. Explain.

- **SECTION 5.5**
  R14. Describe the main role of the communication layer, the network-wide state-management layer, and the network-control application layer in an SDN controller.
  R15. Suppose you wanted to implement a new routing protocol in the SDN control plane. At which layer would you implement that protocol? Explain.
  R16. What types of messages flow across an SDN controller's northbound and southbound APIs? Who is the recipient of these messages sent from the controller across the southbound interface, and who sends messages to the controller across the northbound interface?
  R17. Describe the purpose of two types of OpenFlow messages (of your choosing) that are sent from a controlled device to the controller. Describe the purpose of two types of OpenFlow messages (of your choosing) that are sent from the controller to a controlled device.
  R18. What is the purpose of the service abstraction layer in the OpenDaylight SDN controller?

- **SECTIONS 5.6–5.7**
  R19. Name four different types of ICMP messages.
  R20. What two types of ICMP messages are received at the sending host executing the *Traceroute* program?
  R21. Define the following terms in the context of SNMP: *managing server*, *managed device*, *network management agent* and *MIB*.
  R22. What are the purposes of the SNMP GetRequest and SetRequest messages?
  R23. What is the purpose of the SNMP trap message?

## Problems

- P1. Looking at Figure 5.3, enumerate the paths from y to u that do not contain any loops.
- P2. Repeat Problem P1 for paths from x to z, z to u, and z to w.
- P3. Consider the following network. With the indicated link costs, use Dijkstra's shortest-path algorithm to compute the shortest path from x to all network nodes. Show how the algorithm works by computing a table similar to Table 5.1.

![](img/059c6683459cb0a4f802be65ff31bb03_463_0.png)

![](img/059c6683459cb0a4f802be65ff31bb03_463_1.png)

- P4. Consider the network shown in Problem P3. Using Dijkstra's algorithm, and showing your work using a table similar to Table 5.1, do the following:
  a. Compute the shortest path from t to all network nodes.
  b. Compute the shortest path from u to all network nodes.
  c. Compute the shortest path from v to all network nodes.
  d. Compute the shortest path from w to all network nodes.
  e. Compute the shortest path from y to all network nodes.
  f. Compute the shortest path from z to all network nodes.
- P5. Consider the network shown below, and assume that each node initially knows the costs to each of its neighbors. Consider the distance-vector algorithm and show the distance table entries at node z.

![](img/059c6683459cb0a4f802be65ff31bb03_463_2.png)
