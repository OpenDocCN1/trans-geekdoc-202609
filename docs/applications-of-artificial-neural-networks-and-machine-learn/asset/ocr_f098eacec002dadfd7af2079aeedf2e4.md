![](bbox=[0.135, 0.085, 0.865, 0.285])

# Fig. 17.3 Initial decomposition of a rectangular domain by an expansion method

where DS2 and DS3 are the number of contours of the trees generated from roots r2 and r3, respectively, and the ‘depth’ and ‘width’ are the same as the height and width of the trees, respectively, as defined in Ref. [2].

The algorithm for the present hybrid method can be summarized as follows:

+   1. Construct the partial clique graph of the finite element model using a suitable topological transformation [2].
+   2. Find two pseudo peripheral nodes of the partial clique graph.
+   3. Generate two SRTs routed from these two nodes and form two subdomains R2 and R3 with equal number of nodes. The remaining subdomain is called R1.
+   4. Use the neural networks method of the next section and decompose R1 into two subdomains.
+   5. Add each part of the bisected R1 to the adjacent R2 and R3 subdomains, resulting in the partitioning of the whole domain.

Neural networks for the bisection of FEMs Combinatorial optimization problems arise in many areas of science and engineering. Unfortunately, due to the NP (non-polynomial) nature of these problems, the computational effort required increases with the size of the problem. Most computational methods that have so far been developed which generally yield good solutions to these problems rely on some form of heuristics. Artificial neural networks (ANNs) make use of highly interconnected networks of simple neurons or processing units which may be programmed to find approximate solutions to these problems. They are also highly parallel systems and have significant potential for parallel hardware implementation.