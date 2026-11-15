The specification of the MDB structure is illustrated in detail in Figure 15.2, it is the base to implement a tool that can comprehend the creation and storage of OOM model-based DTs through a standard procedure (starting also from existing OOM libraries, such as Modelica). We focus on the OOM-based DT structure inside an MDB, to which we will refer from now on as the Model root of an MDB. All the model-based DTs contained in the MDB must have this structure to be stored, exported locally and imported to the storage. The UML classes included in the model root of an MDB (Figure 15.2) are the ones prescribed by (Cimino et al., 2021), the long-term research to which this paper belongs. Each model root is related to an MDB indicating the MDB_ID code and includes all the major classes detailed in the following.

![](bbox=[0.11, 0.34, 0.88, 0.89])

FIGURE 15.2
Structure of the Model root of an MDB – UML Class Diagram