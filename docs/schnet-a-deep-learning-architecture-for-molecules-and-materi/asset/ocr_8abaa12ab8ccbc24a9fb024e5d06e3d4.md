# # SchNet – A deep learning architecture for molecules and materials

K. T. Schicht,1 H. E. Sauceda,2 P.-J. Kindermans,1 A. Tkatchenko,3,4 and K.-R. Müller,1,4,5**
1Machine Learning Group, Technische Universität Berlin, 10623 Berlin, Germany
2Friedrich-Huber Institute of Max-Planck-Gesellschaft, 14195 Berlin, Germany
3Physics and Materials Research Institute, University of Luxembourg, L-1511 Luxembourg, Luxembourg
4Max-Planck-Institut für Informatik
5Department of Brain and Cognitive Engineering, Korea University, Anam-dong, Seongbuk-gu,
Seoul 136-733, South Korea

(Received 16 December 2017; 8 March 2018; published 29 March 2018)

Deep learning has led to a paradigm shift in artificial intelligence, web, text, and image search, speech recognition, as well as bioinformatics, with growing impact in chemical physics. Machine learning, in general, and deep learning, are ideally suitable for representing quantum-mechanical interactions, to model nonlinear potential-energy surfaces or enhancing the exploration of chemical compound space. Here we present the deep learning architecture SchNet that specifically designed to model atomic systems by making use of continuous-filter convolutional layers. We demonstrate the capabilities of SchNet by accurately predicting properties of chemical properties across chemical space for molecules and materials, and where our models learn plausible embeddings of atom types across the periodic table. Finally, we employ SchNet to predict potential-energy surfaces and energy-conserving fields for molecular dynamics simulations of small molecules and perform an exemplary study on the quantum-mechanical properties of C20 fullerane with regard to initial atomic structures. Published by AIP Publishing: https://doi.org/10/

# I INTRODUCTION

Accelerating the discovery of materials with desired properties is a long-standing challenge in computational chemistry and the materials sciences. The computational cost of accurate quantum-chemical calculations proves prohibitive in the exploration of vast chemical space. In recent years, there have been increased efforts to overcome this bottleneck using machine learning, which, unless a reduced set of descriptors allows us to accurately predict chemical properties1–15 or potential-energy surfaces,16–25. While these approaches make use of painstakingly handcrafted descriptors, deep learning has been able to predict properties from molecular structures using graph neural networks.27. However, these are restricted to electronic structures due to the lack of atomic positions in equilibrium. Recently models that learn orientation from atom types and positions have been developed.28–30 While neural networks are often considered a “black box,” there has recently been increased effort to explain their predictions in order to understand how they operate. This can be done by training a model model31 or by directly designing interpretable models. For quantum chemistry, some of us have proposed such an architecture with Deep Tensor

Neural Networks (DNNs) not only learn the representation of atomic environments but also for spatially and chemically relevant insights into quantum-mechanical embeddings.28

Here we build upon this work and present the deep learning architecture SchNet that allows to model complex interactions in order to predict potential-energy surfaces or speeding up the exploration of chemical space. SchNet among DNNs, is also able to represent molecules and materials that follow fundamental symmetries of atomic systems by construction, rotational and translational invariance as well as invariance to atom indexing. These approaches predict thorough conform without further constraints and where the potential energy surface is modeled using continuous-filter (convolutional layers)39, being more interpretable through specifically designed-filter neural networks. We demonstrate that these all allow us to incorporate periodic boundary conditions (PBCs) enabling accurate predictions of forces and energies for a diverse set of bulk crystals. Both SchNet and DNNs provide local chemical potentials and offer new representationsational insights.28 An analysis of the obtained representation shows that SchNet learns chemically plausible embeddings of atom types that capture the structure of the periodic table. Finally, we use a path-integral dynamics (PIMD) simulation using an energy-conserving field learned by SchNet trained on a classical data from a chemical33

4schrost,schuft@tu-ber.de
5alexander.tkatchenko@mu-eller.de
6klaus-muller@tu-ber.de