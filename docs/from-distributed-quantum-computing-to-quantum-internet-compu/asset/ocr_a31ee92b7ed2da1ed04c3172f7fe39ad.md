![](bbox=[0.133, 0.108, 0.817, 0.303])

Figure 6.2 Illustration of repeated application of entanglement swapping to generate an entangled pair between qubits A and D at nodes 1 and 5, respectively.

A useful view of entanglement swapping is the teleportation of qubit A’ at node 2 (which has been entangled with A at node 1) to node 3 using the entangled pair between B’ and B as a resource, i.e. B takes on the state of A’, i.e. B is now entangled with A.

A repeated application of such entanglement swapping can be used to create entanglement between a pair of qubits over long distances, as illustrated in Figure 6.2. Although the example shows only five nodes, the same idea can be extended over many more nodes, i.e. across the Internet.

# 6.1.3 Transmission of Qubits Using Tree-Cluster States

We have looked at entanglement swapping as a way to generate entanglement among nodes far apart. We consider another way here.

We mentioned earlier that one way to transfer quantum information is using teleportation (provided we already have entangled pair(s)) and the other way is by direct transmission. For example, to create an entangled pair between qubits on two nodes geographically far apart, we can, in principle, first locally generate a Bell pair at one node, and then transmit one of the qubits to the other node, and so, have an entangled pair between the two nodes. However, transmitting qubits (e.g. via transmitting photons) over long distances can result in losses (e.g. due to attenuation in a fiber-optic channel). One way to deal with this is to use repeater stations between source and destinations nodes. But such repeaters, due to the no-cloning theorem, cannot make copies of arbitrary unknown quantum states (like in the classical case), but we outline here a method to encode information robustly to allow robust transmission and also allow the qubit information to be re-encoded at repeaters to be transmitted further on, due to Borregaard et al. [2020]. This method also allows transmission of qubit information without pre-established