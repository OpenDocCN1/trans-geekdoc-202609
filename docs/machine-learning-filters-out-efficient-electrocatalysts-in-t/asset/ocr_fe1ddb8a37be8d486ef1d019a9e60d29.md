Y. Park et al.

Appliedget B: 39 (2023) 123128

previous literature [54].

# 2.2. ML model development

For SGNN, the graph was constructed based on the structure of the two layers of dopants and adsorbates. The elements of each $i^{th}$ atom (node) in the system are entered into a vector $v_i$, which contains the information available in the atomic table of elements. In this work, we used a vector $v_i$ that includes atomic features along with their ranges, colors. The edge (bond between $i^{th}$ and $j^{th}$ atom) is denoted by $d_{ij} < r_{\delta}$, where $d_{ij}$ is the distance between $r_i$ and $r_j$, and $\delta$ is the length of the bond. The bond is represented by a vector $u_{ij} = e_k$, where $k$ is the $i^{th}$ center node and $j$ is the neighbor node. We also included the direction $j$ in the message vector. Distance-invariant, the values of $u_{ij}$ and $d_{ij}$ were numerically generated using formulas.

```
$v_i^{(l+1)} = \sigma(W_v^{(l)} \sum_{j \in \mathcal{N}(i)} W_u^{(l)} u_{ij} \odot v_j^{(l)} + b^{(l)})$
```

where the convolutional layer and filters are denoted by $l$ and $f$ respectively, $W_v^{(l)}$, $W_u^{(l)}$, and $b^{(l)}$ are the convolution weights and biases of $l^{th}$ layer and $f^{th}$ filter. $\odot$ denotes element-wise multiplication, $\sigma$ is a sigmoid function, and $EL$ is the exponential linear activation function [40]. The normalized sum of all atom vectors in the $l^{th}$ layer is denoted by $S_i^{(l)} = \sum_{j \in \mathcal{N}(i)} v_j^{(l)}$.

The model was trained using the pooling phase. The pooled vectors were connected with the adsorption energy of the molecule. The optimized values are shown in parentheses: the number of convolutions and filters (1, 2), layers (3), learning rate ($5 \times 10^{-3}$), then decreasing learning rate (0.99 for every 100 epochs), number of filters (4-6), and the number of randomly distributed atoms in each (1000), batch size (31, 64), and total number of epochs (800). The mean squared error (MSE) was used to evaluate the loss function $J$. The Adam optimizer was used to train the model. To minimize over-fitting, $L^2$ regularization techniques were employed. Table S2 includes a list of hyperparameters and parameters for the optimization process.

# 2.3. Experimental fabrication of CuAu by sputtering

The prepared Ni electrodes were placed in a vacuum chamber of a direct-current (DC) sputtering system. To create a CuAu thin film, 99.99% pure 3-Cu target and 99.99% pure Au targets were used. Gold foil was pressed crossed on the cathode, the two targets, and the anode, and then the process was carried out. The pressure of the vacuum chamber was $2.5 \times 10^{-5}$ Torr. The

pressure was maintained at 2.5 mTorr by flowing Ar (15 sccm) gas. DC sputtering power of 150 W was applied to the sputtering target for 30 min, leading to a CuAu nm thick on the substrate (for example, Ni electrodes, Si).

# 2.4. Experimental fabrication of the Pt layer by atomic layer deposition (ALD)

Pt was deposited on the substrate (Au thin film on Ni electrodes, Si) using a pulsed sputtering system (ULVAC, ARJ-300) at room temperature under a temperature of $100^{\circ}C$. In the vacuum chamber, a sputtering cathode of the Pt target and an electrode were placed in the cathode, and a cylindrical chamber was used for the sputtering. A pulsed pulse induced an discharge from the cathode to the target. The average deposition rate of the target was measured, which lasted typically less than 1 min. During this period, the temperature increased by tens of degrees ($^{\circ}C$) by vaporizing the cathode material and generating a high kinetic energy of ions. The controllable parameters in this discharge process were voltage V, the cathode pressure C, and the number of pulses n. The deposition of Pt was controlled

# 2.5. Electrochemical measurement

All electrochemical measurements were performed with a 3-electrode rotating disk electrode system in a potentiostat (Autolab, PGStaty). A nickel disk electrode with an area of 0.196 $cm^2$ was used as the electrode. Ag/AgCl (3 M KCl) were used as the reference and counter electrodes. The potentials were measured to evaluate the reversible hydrogen reaction (HER) using the following equation:

```
$E = E_{Ag/AgCl} + E'_{Ag/AgCl} + 0.0591 V$
```

where E is the converted potential vs. RHE, $E'_{Ag/AgCl} = 0.210 V$ and E is the experimentally measured potential against Ag/AgCl. The currents were recorded at a scan speed of 5 $mV/s$ with 1000 rpm in 0.1 - 0.1 M KOH. The current density is

```
$i = J - j$
```

where j is the experimentally measured current density and J is the diffusion-limiting current density [5].

# 2.6. Characterization

The X-ray diffraction (XRD) results were measured by a DiffractAdvanced instrument (Bruker, Germany) using Cu K as the source. Scanning electron microscopy (SEM) (Inspect F50, FEI USA) and EDS were used to examine the morphology and structures of the samples in this study. All samples were prepared for cross-sectional TEM lamellae using a focused ion beam (FIB, NX5000, Hitachi, Japan).

3