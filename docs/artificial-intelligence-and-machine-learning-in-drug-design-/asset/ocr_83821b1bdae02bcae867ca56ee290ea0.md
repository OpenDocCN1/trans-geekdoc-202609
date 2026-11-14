# 6.2.3.3 Semi-Flexible Docking

Also referred to as induced fit docking, it combines elements of both rigid docking and flexible docking approaches. It aims to capture the induced fit phenomenon, where the binding of a ligand induces conformational changes in the receptor or vice versa. In hybrid docking, an initial docking step is performed with the ligand and receptor assumed to be rigid, similar to rigid docking. The resulting complex is then subjected to energy minimization or molecular dynamics simulations to relax the structure and allow for conformational adjustments. After this step, a refinement stage is carried out, where the ligand and receptor flexibility are considered, and the binding poses are optimized further. Semi-flexible docking provides a balance between computational efficiency and accuracy, capturing the essential flexibility required for accurate binding prediction while avoiding the exhaustive sampling of the entire conformational space [17].

# 6.2.4 Common Tools and Software for Molecular Docking

The search for potential targets using a structural data bank and an evaluation method for ligands is necessary for the practical application of molecular docking. Numerous molecular docking tools and methodologies are available to achieve this. The computational tools are used to rank the potential ligands according to their ability to interact with the particular target candidates [1].

Various search algorithms, including genetic, molecular docking algorithms, Monte Carlo, and fragment-based algorithms, are used by docking tools that are widely used. Additional tools include GOLD, FlexX, DOCK, and ICM, which are primarily employed for the purpose of high-throughput docking simulations (Table 6.1) [18].

Using a hierarchical docking strategy, Glide (Grid-based Ligand Docking with Energetics) generates the top potential combinations or hits after completing its four main steps. These steps are as follows: [19]

+   1. Site point search in the receptor's active site.
+   2. Assigning the rough scores utilizing the greedy scoring, subset test, and diameter test.
+   3. Energy minimization using electrostatic grids and OPLA-AA.
+   4. Use the Glide Score Function.

New algorithms from academia and industry are quickly incorporated into high-end packages. As public domain software advances, it can now functionally compete with some commercial products. Computers double in speed every year and a half, while graphic displays advance in sophistication and usability at the same time. These factors collectively make molecular docking an essential component of drug design. It keeps expanding its function in innovative new methods like computational enzymology, genomics, and proteomic search engines [6].