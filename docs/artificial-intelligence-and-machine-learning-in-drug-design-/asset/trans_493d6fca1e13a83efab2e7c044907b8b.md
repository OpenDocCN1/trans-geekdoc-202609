

protein or enzyme. This strategy can aid in the discovery of lead compounds that are more likely to bind to the target protein, improving the likelihood of creating medications that work better and have fewer adverse effects.

蛋白质或酶。这种策略有助于发现更有可能与靶标蛋白结合的先导化合物，提高创造疗效更好且不良反应更少的药物的可能性。

X-ray crystallography, a major method in SBDD, is employed to ascertain the target protein's three-dimensional structure. In this method, protein crystals are grown, and then X-rays are used to create a diffraction pattern that can be used to solve the structure. Researchers can utilize computational techniques to build and improve tiny compounds that can interact with the protein in a certain way once the structure is determined.

X射线晶体学是SBDD的主要方法之一，用于确定靶标蛋白的三维结构。在这种方法中，先培养蛋白质晶体，然后利用X射线产生可用于求解结构的衍射图样。一旦结构确定，研究人员就可以利用计算技术构建并改进能以特定方式与蛋白质相互作用的微小化合物。

Molecular docking, which makes use of computer algorithms to forecast the binding mechanism and affinities of small compounds to the target protein, is another crucial SBDD approach. In order to find the optimum match and calculate the binding energy, docking algorithms produce many conformations of the small molecule and dock them into the protein binding site. Large libraries of compounds can be screened using these methods to find those with the highest binding affinity to the target protein.

分子对接是利用计算机算法预测小化合物与靶标蛋白结合机制和亲和力的另一种关键SBDD方法。为了找到最佳匹配并计算结合能，对接算法会生成小分子的多种构象并将其对接到蛋白质结合位点。可以使用这些方法筛选大型化合物库，以找到与靶标蛋白具有最高结合亲和力的化合物。

Another method employed in SBDD is homology modelling, which creates a three-dimensional model of the target protein in the absence of the experimental structure. This method aligns the target protein sequence to a template protein structure made from a known protein structure, then creates a model of the target protein based on the alignment. The creation and improvement of tiny compounds that can interact with the protein can then be done using this paradigm.

SBDD中采用的另一种方法是同源建模，它在没有实验结构的情况下创建靶标蛋白的三维模型。该方法将靶标蛋白序列与由已知蛋白质结构构建的模板蛋白结构进行比对，然后根据比对结果创建靶标蛋白的模型。之后可以使用该范式来创建和改进能与蛋白质相互作用的微小化合物。

Molecular dynamics simulations are also an important technique in SBDD, which can provide insights into protein-ligand binding kinetics and thermodynamics. This technique involves simulating the motion and behavior of the target protein and ligand over time using a force field to simulate the interactions between atoms. This can help researchers understand the dynamics of protein-ligand interactions and identify key features that contribute to binding affinity.

分子动力学模拟也是SBDD中的一种重要技术，可以提供关于蛋白质-配体结合动力学和热力学的见解。该技术涉及使用力场模拟原子间的相互作用，从而随时间模拟靶标蛋白和配体的运动和行为。这可以帮助研究人员了解蛋白质-配体相互作用的动态，并找出有助于结合亲和力的关键特征。

Overall, SBDD as shown in Figure 11.7 is an interdisciplinary field that integrates computational and experimental methods to design and optimize small molecules that can interact with specific target proteins or enzymes. These methods and tools can be used to find and improve drug candidates that have greater binding affinity and lower toxicity, which could ultimately result in the creation of more potent treatments for a number of disorders.

总体而言，如图11.7所示，SBDD是一个跨学科领域，整合计算和实验方法来设计和优化能够与特定靶标蛋白或酶相互作用的小分子。这些方法和工具可用于寻找和改进具有更高结合亲和力和更低毒性的药物候选物，最终可能为多种疾病创造出更有效的治疗方法。

## 11.3.1 X-Ray Crystallography

## 11.3.1 X射线晶体学

A powerful technique for determining the three-dimensional structure of macromolecules like proteins and nucleic acids is X-ray crystallography. This method entails generating crystals of the target macromolecule, subjecting the crystals to X-rays, and studying the diffraction pattern to ascertain the macromolecule's structure.

X射线晶体学是一种用于确定蛋白质和核酸等大分子三维结构的强大技术。该方法包括生成靶标大分子的晶体、将晶体置于X射线照射下，并研究衍射图样以确定大分子的结构。

The first step in X-ray crystallography [11] is to obtain a pure sample of the macromolecule of interest. The sample is then crystallized using methods such as vapor diffusion or liquid-liquid diffusion. The crystals are typically grown in small glass plates or plastic trays and can take several days to several weeks to grow, depending on the molecule and the conditions used.

X射线晶体学的第一步[11]是获得感兴趣的大分子的纯样品。然后使用蒸气扩散或液-液扩散等方法对样品进行结晶。晶体通常在小玻璃板或塑料托盘中生长，生长时间可能需要几天到几周，具体取决于分子和所使用的条件。

Once the crystals are grown, they are mounted on a thin fibre or loop and placed in a beam of X-rays. The X-rays diffract off the atoms in the crystal lattice, creating a diffraction pattern that is captured by a detector. The location of the atoms in the crystal lattice is then determined by examining the diffraction pattern.

晶体生长后，将其安装在细纤维或环上，并置于X射线束中。X射线会从晶格中的原子处衍射，形成由探测器捕获的衍射图样。随后通过检查衍射图样来确定晶格中原子的位置。

![](img/9a8b0347872e9b0be4401898e8cd724c_358_0.png)

Figure 11.7 Workflow of SBDD.

图11.7 SBDD工作流程。

It takes several steps to extract the macromolecule's structure from the diffraction pattern, which is a complicated operation. The intensities of the diffraction spots are first extracted from the diffraction pattern, and these intensities are then utilised to determine the phases of the diffracted waves. The electron density map, which is created by computing the phases and intensities, is then utilised to create a model of the macromolecule.

从衍射图样中提取大分子结构需要几个步骤，这是一个复杂的操作。首先从衍射图样中提取衍射斑点的强度，然后利用这些强度来确定衍射波的相位。接着利用计算得到的相位和强度生成电子密度图，并据此构建大分子模型。

The process can be divided into three main stages:

- Data collection
- Structure determination
- Model refinement

该过程可分为三个主要阶段：

- 数据采集
- 结构确定
- 模型优化

Data collection involves exposing the crystal to a beam of X-rays and collecting the diffraction pattern generated by the X-rays. The diffraction pattern is a complex pattern of spots, each of which corresponds to the scattering of X-rays off the atoms in the crystal. The intensity and position of the spots in the diffraction pattern are recorded using a detector.

数据采集涉及将晶体暴露于X射线束中并收集X射线产生的衍射图样。衍射图样是一组复杂的斑点图案，每个斑点都对应于X射线与晶体中原子的散射。使用探测器记录衍射图样中斑点的强度和位置。

In the next stage, structure determination, the intensities and positions of the spots in the diffraction pattern are used to calculate the electron density of the molecule. The electron density is a three-dimensional map of the distribution of electrons within the crystal lattice, which reflects the positions of the atoms in the molecule.

在下一阶段——结构确定中，利用衍射图样中斑点的强度和位置来计算分子的电子密度。电子密度是晶格内电子分布的三维图谱，反映了分子中原子的位置。

The phases of the diffracted waves must be ascertained in order to calculate the electron density map. However, the phase information cannot be directly measured from the diffraction pattern. Instead, it is inferred by using a mathematical technique called phase determination. There are several methods for phase determination, including molecular replacement, multiple isomorphic replacement, and single-wavelength anomalous dispersion.

为了计算电子密度图，必须确定衍射波的相位。然而，相位信息无法直接从衍射图样中测量。相反，它是通过一种称为相位确定的数学技术推断出来的。相位确定有几种方法，包括分子置换、多同象置换和单波长异常衍射。

The electron density map can be computed using the Fourier transformation once the phases have been identified. The positions of the atoms in the molecule are revealed by the electron density map, but the lengths and angles of the bonds between them are not. The electron density map is analysed using molecular modelling methods to obtain the bond angles and lengths.

一旦确定了相位，就可以使用傅里叶变换计算电子密度图。电子密度图揭示了分子中原子的位置，但并未揭示它们之间化学键的长度和角度。利用分子建模方法分析电子密度图以获取键角和键长。

In the final stage of model refinement [12], the initial model is refined and validated using a variety of methods, including refinement against experimental data, molecular dynamics simulations, and validation against other experimental data. The refined model is then used to study the molecular structure and function of the macromolecule, as well as in the design of small molecules that can interact with the molecule.

在模型优化的最后阶段[12]，初始模型会通过多种方法进行优化和验证，包括针对实验数据的优化、分子动力学模拟以及针对其他实验数据的验证。优化后的模型随后用于研究大分子的分子结构和功能，以及设计能够与该分子相互作用的小分子。

The process requires sophisticated computational methods and can take several months or even years to complete for a complex molecule. However, the results of X-ray crystallography can be utilised to build medications that specifically target particular protein targets and can offer insights into the molecular basis of function.

该过程需要复杂的计算方法，对于复杂分子来说可能需要数月甚至数年才能完成。然而，X射线晶体学的结果可以用于构建专门针对特定蛋白靶点的药物，并能提供关于功能分子基础的见解。

Structural biology and drug development both rely heavily on X-ray crystallography as a technique. Numerous proteins and nucleic acids have had their structures determined, revealing information on their functions and modes of action. X-ray crystallography is frequently employed in structure-based drug design (SBDD) in the drug discovery process to create and improve small molecule inhibitors that can interact with a particular protein target.

结构生物学和药物开发都高度依赖X射线晶体学这一技术。众多蛋白质和核酸的结构已被确定，揭示了它们的功能和作用方式。X射线晶体学在药物发现过程中常用于基于结构的药物设计（SBDD），以创建和改进能够与特定蛋白靶点相互作用的小分子抑制剂。

Despite its power and utility, X-ray crystallography has some limitations. It needs the presence of a pure sample of the targeted macromolecule, and for some compounds, growing crystals might be challenging. Additionally, the technique is limited to static structures and cannot provide information on dynamic processes or conformational changes in the molecule. However, with advances in technology and methodology, X-ray crystallography continues to be a valuable tool in structural biology and drug discovery.

尽管功能强大且实用，X射线晶体学也存在一些局限性。它需要靶标大分子的纯样品，且对于某些化合物，培养晶体可能具有挑战性。此外，该技术仅限于静态结构，无法提供分子中动态过程或构象变化的信息。然而，随着技术和方法的进步，X射线晶体学仍然是结构生物学和药物发现中的宝贵工具。

## 11.3.2 NMR Spectroscopy

## 11.3.2 核磁共振光谱法

The three-dimensional structure of macromolecules in solution can be ascertained using the potent technique of nuclear magnetic resonance (NMR) spectroscopy, which is employed in structural biology and drug development. NMR spectroscopy, which is different from X-ray crystallography in that it doesn’t require the sample to be crystallized, can reveal details on the dynamics and flexibility of the molecule in solution.

核磁共振（NMR）光谱法是一种强大的技术，用于结构生物学和药物开发，可以确定溶液中大分子的三维结构。NMR光谱法不同于X射线晶体学，因为它不需要对样品进行结晶，可以揭示分子在溶液中的动态和灵活性细节。

The magnet, radiofrequency transmitter and receiver, as well as the computer system required to handle and analyze the data, are all shown as parts of an NMR spectrometer.

NMR光谱仪的组成部分包括磁体、射频发射机和接收机，以及用于处理和分析数据所需的计算机系统。

