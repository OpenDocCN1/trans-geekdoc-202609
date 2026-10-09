Stress analysis with PINNs outputs a displacement vector for each selected point, which can be transferred to FEMAP for visualization. The presumption in this case is that the mesh has already been defined in FEMAP. Specifically, the file is created as an addition to the data exported from FEMAP as a pre-process. FEMAP reads this file and performs post-processing. The post-processing consists of the following:

+   (4)  NN model output
(5)  NN model visualization

In the NN model output, data are exported in a form that FEMAP can process, and the NN model visualization uses FEMAP functions.