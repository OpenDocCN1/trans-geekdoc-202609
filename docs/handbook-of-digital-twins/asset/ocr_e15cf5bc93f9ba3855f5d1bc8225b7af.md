and decision-making. The ranges of these critical deviations are set for each control object.

The connection between BPS and the metric systems of its elements MS\_EPS is established through the validators of filtering, grouping and data conversion V_PMS_BPS-MS_EPS;

Depending on the types of tasks to be solved, BPS can interact with two or more PS elements. Any interaction implies the adjustment of management parameters, which implies the adjustment of

+   - the structure of the goal tree;
+   - the system for measuring changes in the state of the objects under study, as well as deviations of their values from the established standards;
+   - values of normative indicators, which correspond to the values of the leaves of the objectives tree.

The construction of GT_BPS is carried out in accordance with the goal facing PS, and may change over time, depending on environmental conditions, the parameters of resource availability of one or more of its elements, as well as a number of other factors.

The hierarchical structure of GT_EPS contains the branches of the goal tree corresponding to the functions of the EPS objects, and its leaves are the normative values of indicators characterizing the state of individual properties of objects, when performing one or more processes. Each object of the managed system can correspond to several leaves in the goal tree structure.

Like GT_BPS, GT_EPS can be periodically restructured, which is associated with the change of PS targets or PS elements. Similarly, their alignment methods may change. The parameters of the BPS goal tree are set in relation to the goal trees of PS elements. Each GT_BPS sheet corresponds to a subset of the BPS indicators.

The schematic diagram of the information interaction of GT_BPS, GT_EPS, PMS_BPS, and MS_EPS is shown in Figure 20.2.

PS control depends on the accuracy of its state prediction for a given time lag.

The most promising technologies for the realization of this function have become digital twins.

Therefore, the digital twin is an important element of PS.

Figure 20.3 shows a scheme of interaction of digital twins with other PS components.

The GT_BPS configuration component sets the hierarchy of PS goals and subgoals, as well as the links between them, and sets the normative values of the GT_BPS leaf indicators. It consists of several modules:

+   - a module for constructing the goal tree and defining the rules and conditions for its decomposition;