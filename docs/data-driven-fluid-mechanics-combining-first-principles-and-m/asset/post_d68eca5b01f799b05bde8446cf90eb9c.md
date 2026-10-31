
![](img/ddadb1d3eaa6f9576eea68f95d453bca_168_0.png)

![](img/ddadb1d3eaa6f9576eea68f95d453bca_168_1.png)

![](img/ddadb1d3eaa6f9576eea68f95d453bca_168_2.png)

![](img/ddadb1d3eaa6f9576eea68f95d453bca_168_3.png)

Figure 7.7 Composite analysis of a compressible axisymmetric jet at Ma = 0.9. Two dynamic modes (left and right) from the higher-frequency peak, with the top corresponding to the hydrodynamic vorticity component and the bottom visualizing the acoustic dilatation component. Significant acoustic activity is observed in both cases.

Temporal dynamics and spatial structure may be appropriate for many applications, there are just as many configurations where an alternative dynamics-structure division seems more fitting. An example is given by a jet in cross-flow.

A jet in cross-flow (or transverse jet) is generated when a flow exiting an orifice on a wall is subjected to a second flow parallel to the wall. Situations like this arise, for example, in smoke stacks or every time a fluid is injected into a cross-stream, such as in fuel injectors. The corresponding flow is rather complex and develops a great many instabilities that interact in a nontrivial manner. Among the main instabilities is the roll-up of the vortex sheet, which is initially axisymmetric at the orifice quickly deforms into two counterrotating vortex pairs that follow a bent trajectory. Along this bent, rolled up vortex sheet instabilities develop quickly: initiated a short distance from the orifice, vortex ring-like structures amplify before they break down into smaller and less coherent fluid elements.

The description of the principal instability for a jet in cross-flow clearly shows that the evolution of the instability is more aptly expressed as a spatial evolution along the bent vortex sheet of the base flow. This realization immediately sways the analysis of this physical process toward a data-driven (Koopman) approach, rather than a traditional state-space description that would require the formulation of the governing equations for the spatial evolution of disturbances along curved paths.

![](img/ddadb1d3eaa6f9576eea68f95d453bca_169_0.png)

Figure 7.8 Streamline-based analysis of a jet in cross-flow. A base streamline, emanating from the jet nozzle, serves as the spatial evolution direction. Flow fields are sampled in n planes orthogonal to the streamline and equispaced in arclength along the streamline. Figure reproduced with permission from Henningson (2010).

In our data-driven approach, we simply have to sample the flow fields in planes orthogonal to a chosen evolution direction and stack the data matrix accordingly. To this end, we determine a streamline emanating from the center of the orifice and following the base flow. This streamline will serve as our spatial evolution direction. We then partition the streamline into n = 110 equispaced (in arclength) intervals between the location of instability onset and the location of ultimate instability breakdown. For each point along the streamline, we define a plane normal to its tangent, and interpolate the three-dimensional velocity field into this plane. These planes (when reshaped into vectors) will form the columns of our data matrix D. Figure 7.8 illustrates the aforementioned procedure.

Once we have established the evolution direction of our observables and formed the data matrix, a standard DMD/Koopman analysis can be performed. It is worth noting that the “spatial” direction, that is, the row direction of the data matrix, contains the coordinates in the cross-planes (normal to the base-flow streamline tangent) as well as the time coordinate. In order to reduce the size of the problem, we Fourier transform in time and focus on the Strouhal number (nondimensional frequency) associated with the Kelvin–Helmholtz instability of the vortex sheet.

Evaluating the dynamic modes from the analysis of our data matrix, we capture the spatial breakdown of the vortex sheet. The identified instabilities are localized on the base-flow counterrotating vortex sheet and describe vortical structures of increasing complexity and scale; see Figure 7.9.

![](img/ddadb1d3eaa6f9576eea68f95d453bca_170_0.png)

Figure 7.9 Streamline-based analysis of a jet in cross-flow. Dominant dynamic modes displaying the structures causing the spatial breakdown of the base vortex sheet along the base streamline. The approximate location of the base vortex sheet is indicated in red. Reproduced with permission from Henningson (2010).

The dynamic modes consist of vortical structures that align with the counterrotating vortex sheet of the base flow. Higher-order modes display more vortical elements that progressively concentrate on the flanks of the base-flow vortex sheet. This is consistent with the findings from direct numerical simulations as well as physical experiments. The amplitude distribution of the modes (not shown) shows a broad peak, which suggests that a superposition of a few dominant modes may best capture the pertinent dynamics of the spatial instability and may provide a reduced-order description of the Kelvin–Helmholtz-type breakdown of the base-flow’s counterrotating vortex sheet.

This final example demonstrates the capability of Koopman/DMD analysis to identify coherent fluid motion directly from data snapshots in situations where the relevant evolution direction is not aligned with a coordinate direction, but is instead given by a curved base-flow streamline. With a projection and rearrangement of the data fields, the dynamic characteristics of complex instabilities can be readily computed.

## 7.6 Extensions and Generalizations

Since its introduction, the DMD and the underlying Koopman analysis have gained in popularity as a tool for quantitative flow analysis. Both fields have spawned a great deal of improvements, extensions, and generalizations – both from an algorithmic and conceptual point of view. Only a few of them shall be mentioned here.

The choice of observables is a key issue in Koopman analysis. In the above exposition, we use the raw snapshots, assuming that their evolution contains the necessary information to embed the dynamics in a linear fashion. However, extended DMD (Williams et al. 2015) aims at explicitly including observables that are higher powers of the original snapshots. This follows the original idea of supplementing the observables by selected nonlinearities. Alas, extended DMD quickly becomes computationally expensive; a reduction in dimensionality using a kernel trick is possible (Williams et al. 2015), but only provides temporary relief.

It has quickly been noted that, while equispaced snapshots are advantageous in the motivation of the DMD algorithm, they are not required for a more general formulation. In fact, only the snapshots in equal column position in D₁ⁿ and D₂ⁿ⁺¹ have to be separated by a constant Δt. Within either snapshot sequence, non-equispaced data can be accommodated.

An SVD is a core element of the DMD algorithm, which allows for a great deal of improvements from an algorithmic standpoint. An incremental formulation of the SVD allows the design of an efficient DMD algorithm for streaming data (Hemati et al. 2017), where new data snapshots get incorporated into an already existing decomposition by a perturbative adjustment of the modes and spectrum. This type of algorithm permits the analysis of experimental data in real time. In addition, recent developments in randomized algorithms for the SVD can also be incorporated into the overall DMD algorithm and lead to higher efficiencies, while sacrificing little in terms of accuracy.

Using delay-embedding techniques (related to the Ruelle-Takens methodology), the predictive horizon of a reduced description of a dynamical system via DMD can be substantially enhanced. In essence, the data sequence is transformed into a phase-space description and decomposed there. The data matrix is block-Hankelized and processed by the standard DMD algorithm (Arbabi & Mezić 2017, Brunton et al. 2017).

Finally, the recent popularity of machine learning and artificial neural network techniques has also influenced data decompositions and model reduction methods. By proposing a neural net in the form of an auto-encoder, a nonlinear Koopman embedding can be learned directly from the data (Takeishi et al. 2017, Lusch et al. 2018, Mardt et al. 2018, Otto & Rowley 2019, Yeung et al. 2017), by imposing linearity of the mapping over one time step between the final step of the encoder portion and the first layer of the decoder part. More advances in this direction are expected over the coming years.
