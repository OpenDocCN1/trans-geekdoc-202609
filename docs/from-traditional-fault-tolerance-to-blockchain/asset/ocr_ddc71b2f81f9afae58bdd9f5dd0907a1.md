+   - Forth, two error conditions are checked in this step. If the ommer block’s parent is not one of the ancestors, then it means that the ommer block’s parent is also a stale block (i.e., there are two stale blocks linked together). Furthermore, if the ommer block and the current block share the same parent, then the ommer block is in fact a sibling block in the same generation of the current block, which is not allowed. In both cases, an errDanglingUncle error is returned.

+   - The final step is to verify that the ommer block’s header is valid.

While not explicitly programmed, it is a concern when the first loop is broken due to the ancestor not being on the main blockchain. First, if the current block’s parent is not on the main blockchain (could happen during the very first iteration when i=0). The loop is terminated without throwing an error at this stage. Please note that in this case, the ancestors set contains only the current block itself. Assume that at least one ommer block is provided by the current block. During the ommer block verification, the check for dangling uncle would fail because the current block cannot possibly be the parent of the ommer block provided (i.e., ancestors[uncle.ParentHash] == nil would be evaluated to true). The only scenario that the parent of some ancestor in certain generation is not on the main blockchain is the loop has gone back to the genesis block and that ancestor is the genesis block itself. In this case, there is no error. Put it another way, it is impossible for a block that is on the main blockchain that has a parent that is not on the main blockchain (i.e., being a stale block).

![](bbox=[0.12, 0.69, 0.87, 0.77])

Figure 8.15 An example on what kind of stale blocks may be chosen as an ommer block.

# EXAMPLE 8.2

We illustrate what kind of stale blocks are eligible to be selected as an ommer block using an example shown in Figure 8.15.