# Article

https://doi.org/10.1038/s41586-025-01070-2

![](bbox=[0.075, 0.065, 0.465, 0.33])

![](bbox=[0.535, 0.065, 0.917, 0.33])

![](bbox=[0.075, 0.375, 0.465, 0.64])

![](bbox=[0.535, 0.375, 0.917, 0.64])

**Fig. 2:** Dismantling performance of synthetic and real-world interdependent networks under the metrics AUDC and C. For synthetic networks, we consider two layers with 100 nodes each, power-law degree distribution ($\gamma$) and expected mean ($\langle k \rangle$). We tune one parameter while keeping the other two invariant for 20 interconnected networks with various properties (see Supplementary Table 3 for the parameter setting of the GMM model). To generate networks under condition ($i=0,1$), $N=1024$, we set $\gamma=2.5$ and $\langle k \rangle=6$.

generate g from 0 to 1, a dismantling performance of unit removal cost under AUDC, which quantifies the vulnerability, and C, which measures the cost of removing nodes until the giant component of the MCC disappears. For real-world interdependent networks from various domains, we observe the dismantling performance differences under both unit cost (a) and removal cost (b). See Supplementary Tables 10–12 for the detailed numerical results.

We utilize multilayer networks to design immunization strategies for spreading over social networks; we seek to take advantage of Multilayer Dismantler to mitigate spread in interdependent networks. In all applications, Multilayer Dismantler demonstrates superior performance compared with all other algorithms.

# Dissecting networks

We consider a network consisting of two layers of interactions. In the layers they are one-to-one interdependent. For simplicity of description thus without loss of generality, we do not make a formal decomposition between one node and its replica in the other layer; instead, as we

the two layers share a set of nodes. Dismantling in the context of networks, with layers, but indistinguishable nodes across the layers, are also represented as multiplex networks or edge-coloured networks$^{13,14}$. Two nodes are in the same mutually connected component (MCC) if there are paths between them along the layers and such mutually connected components are also in the same MCC. The network dismantling problem involves identifying a sequence of nodes whose effectively increases the fragmentation of the network into mutually connected components of non-extensive size$^{15}$ (see Problem formulation section in the Methods). The removal of

Nature Intelligence | Volume 7 | 2025 | 1266–1277