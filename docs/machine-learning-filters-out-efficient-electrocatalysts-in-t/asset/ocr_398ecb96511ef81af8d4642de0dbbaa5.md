# Y. Park

# Applied Chemistry B: 399 (2023) 123128

Metal alloying using an excellent catalyst strategy [11] can significantly modify the electronic structure and consequently the catalytic properties of metals. Alloys in fuel cells, however, have been limited to bimetallic cases. In various experiments, transitions often differ from those of pure metals. A Pt-based alloy with a Pt skin (Pt$_x$X$_y$, where X-arbitrary element) in the cathode of fuel cells. This Pt$_x$X$_y$ strategy has been extensively explored, and ranges from Pt-transition-metal interfaces (Pt-Co, Ni, Cu, and Fe) to those similar to lanthanides (Y-Sc and Sc) [14]. These alloys have improved performance because the Pt skin ensures stability in harsh environments and offers better tunability of the cathode.

mechanical, performance, and cost effectiveness. We identified 37 candidates for each ORR and OHR electrode, with lower cost and higher performance than Pt. Through experimental verification, we used a CuAgPt alloy, of 10 final candidates for the ORRs, substantially obtaining a Pt film in the cathode with improved current density. Our ML-based screening protocol enabled the identification of an efficient catalyst strategy to address other catalysis problems.

# 2. Experimental section

# 2.1. DFT adsorption

Despite these achievements, Pt-based bimetallic alloys have failed to fully solve the problems in fuel cells with high cost (density of Pt) at the cathode, slow kinetics (ORR activities at the cathode), and CO poisoning (a durability issue that is the main bottleneck). In broader spatial, temporal sense, ternary alloys emerge [18-22]. In this study, we focus on ternary ORR efficiency, the focus of study of the Pt-Au [23, 24] and Pt-Ni-Co [25] alloys, which have been considered promising but not extremely effective due to the massive surface effect. For exploring metal interactions, ternary metal alloys offer numerous candidates with various properties.

Adsorption energies were calculated using the following equation: $\Delta E_{ads} = \Delta E_{ads} - \Delta E_{slab} + \Delta E_{gas}$; where $\Delta E$ indicates the total energy of the adsorbate-surface system. The adsorption energy was referenced to the surface and all the gas species, including H, $H_2O$, and CO [29]. The Vienna Abinitio Simulation Package (VASP) was used for all DFT calculations. The predicted adsorption energies were used to filter the candidate surfaces to be considered.

These difficulties require more efficient routes, namely machine learning (ML) approaches [26-29]. A number of models aimed at predicting adsorption energies on catalytic surfaces were developed based on the density of states (DOS) of the materials [30-36]. Graph neural networks (GNNs) are also used, where atoms and bonds are represented as nodes and edges of a graph respectively, to predict adsorption energy without prior preparation [37-40]. These GNN models were trained for diverse alloy types but have been used in exploring many binary and ternary alloys.

The free energies were calculated under standard conditions (pH = 0, 298 K; P = 1 atm at a potential of U = 0). We calculated the free energy of the solvent protons and electrons (H$^+$) that was equilibrated with hydration of the gas (phase 0.5 h). The thermodynamic free energy was defined as $\Delta E_{ads}$, where $\Delta E_{ads}$ denotes the free energy correction for the adsorption of the adsorbate. The calculations included $H_2O$, H and CO, as in $\Delta E_{ads}$ calculations [49, 52, 53]. Solution effects were considered using constant values (0.5 eV; U = 0.25 eV) obtained from explicit water models as reported in a -

In this work, we present a catalyst design protocol in ML filters out potentially efficient and low-cost materials for the ternary alloy space for fuel cells. Among many structural properties in the ternary space, conventional alloy-metal shells (X,Y,Z) and Pt can differ are the focus of this study [48]. Based on the screening protocol with approximately ten adsorption energy values obtained at the DFT level, a fully ML-screening process with criteria including structural stability (thermodynamic and

2