The basic structure of a behaviour tree consists of a root node, composite nodes and leaf nodes and is depicted in Image 4.1. The elements depicted are as follows:

![](bbox=[0.19, 0.15, 0.8, 0.49])

IMAGE 4.1 Basic layout of a behaviour tree.

+   - The root node is the entry point for the graph, and leaf nodes comprise all actions that can be taken by the AI.
+   - A leaf node, once executed, can opt to either stay within itself for a certain amount of time or return success or failure, which is only relevant to the operation of their parents and principally by the composite nodes.
+   - Composite nodes define how leaf nodes should lead into one another. While other types exist, such as parallel nodes, the two main flavours of composite nodes are selectors and sequencers. Selector nodes run all their child nodes in a sequence (leaf nodes or other composites), until the first node that returns success prompts, the selector itself to return success. If it gets through all its child nodes without any success, it returns failure. Sequence nodes run all their child nodes in sequence until a node returns failure, and then the Sequence node itself returns failure. If it gets through all its child nodes without any failures, it returns success.

That is all there is to behaviour trees really, a very simple tree structure with basic flow control. The tree is run from the root downwards, from left to right, evaluating nodes according to the rules of the composite nodes until it arrives at the end of the tree. Once there, it just restarts the tree and does it all again. Connect this up to an AI character and you can watch them navigate the tree, making decisions and running behaviours.