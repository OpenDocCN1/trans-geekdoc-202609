# 6.4.3 Covering strategy and implementation of molecular docking

In the case of flexible molecular docking, the ligand molecule undergoes a translational and rotational operation at the docking site of the receptor until an optimal conformation is found. The translational rotation of the ligand constitutes the Lie group, in which the rotatable bond is used to probe the ligand. In the case of flexible conformational spaces, the efficiency of a global search is acceptable for relatively small ligand molecules. However, if the rotatable bonds are relatively large, the orientation and conformational spaces of the ligand are searched globally. Thus, a considerable amount of calculation is required, which is time-consuming, and it is often difficult to get the desired results.

At the active site of the receptor, the ligand molecules are constantly aligned. The conformational search space is very large owing to the presence of the rotatable bond. Hence, the conformational space must be reduced.

This can be achieved by the following operations when considering the conformational changes of the flexible molecules. First, we need to determine rigid segments and search constants. For a flexible molecule, its rotatable dihedral angle can be changed. Hence, in the docking process, we consider a flexible molecule that can be regarded as a combination of multiple rigid fragments. Each rigid segment consists of a set of atoms connected by non-rotatable bonds, while the rigid segments are connected by rotatable bonds.

The first step in determining the rigid segment is the judgment of the ring, and the keys in all the rings can be regarded as rigid. The second step is to determine the rotation of the key. We can identify the type of key on both sides of the key type. In general, double bonds are regarded as rigid keys. Each rigid segment contains only non-rotatable keys. Figure 6.7 shows a basic schematic diagram for dividing a molecule according to a rotatable key.

![](bbox=[0.1, 0.62, 0.52, 0.68])

**Fig. 6.7:** Schematic diagram of flexible molecular division.

Then, the nature of the flexible molecule can be decomposed as in Figure 6.8:

![](bbox=[0.1, 0.77, 0.57, 0.85])

**Fig. 6.8:** Exploded map of Flexible Molecules.