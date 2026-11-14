+   - Safe Learning Integration: directly integrating learning logic into a BT as subtrees, featuring a dedicated BT learning node, and ad hoc safety control logic.

+   - Small-Scale Learning: isolating the scope of learning for each learning model instance to its relevant, local context, to decrease training costs and increase output quality.

# 10.3.2 CONTEXT GUIDANCE

The hierarchical, subsumption architecture of a BT organically directs the flow of behaviour logic. By combining this inherent property of BTs with task decomposition similar to that of hierarchical reinforcement learning (RL), three context layers in a BT can be observed: *macro*, *proxy* and *micro* (Justesen et al., 2020). The *macrolayer* represents strategic decision-making logic and occupies the top of the tree, while the *microlayer* contains low-level agent actions and is located at the bottom of the tree (Colledanchise et al., 2018; Colledanchise & Ögren, 2018). The optional *proxy layer* facilitates connections between the *macro-* and *microlayers*, if required. Such layering provides an organised structure for context-relevant positioning and flow control of learning subtrees. The context-guided structuring of the design is visualised in Image 10.1.

![](bbox=[0.117, 0.46, 0.882, 0.76])

IMAGE 10.1 Context-guided architecture flow with a separation between macro-, micro- and proxy layers.

Macro- and microlayers can feature both ad hoc and learning logic, but if the proxy layer is present, it is expected to use ad hoc nodes exclusively to guarantee expert flow curation. The exact balancing of learning and ad hoc logic is left at the discretion of the designer, and the modularity of the outlined design allows for gradually scaling up the presence of learning subtrees.