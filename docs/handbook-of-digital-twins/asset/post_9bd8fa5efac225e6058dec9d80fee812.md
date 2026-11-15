
different subject areas and revealing new connections and forms of influence on subordinate or otherwise connected elements of the system.

It is characterized by the presence of a set of rules and a language of interaction of PS elements through built-in mechanisms of cleansing, aggregation, routing and synchronization of input and output data flows.

- 3. Represents a system of objects, processes, functions and links between them, the depth of decomposition of which is determined by the type of tasks being solved and the details of which can be expanded.
- 4. The vector of target development of each PS element is represented in the form of a tree of goals and a set of indicators assessing the state of its objects and processes.
- 5. The structure and complexity of each element of PS, as well as its relationships with other elements of PS and systems that are not part of it, can be transformed under the influence of external and internal factors, which requires the presence in PS of a system for monitoring and forecasting of emerging deviations, the mechanism for their adjustment.
- 6. The object state indicators of each PS element, as well as their transformed values form the data bank of PS indicators, and through the integrating PS element can be available to each other.
- 7. The life cycle of the PS is defined by the objectives facing it.
- 8. The presence of the integrating element PS, which we will hereinafter refer to as body of the polystructure (hereinafter—BPS). BPS performs the functions of developing, adjusting and programming the orchestral score of interaction of PS elements, coordinating their target benchmarks and jointly used resources to obtain a positive result and level out the emerging risks. At the same time, BPS supports multi-level PS management within the information space of the PS and organizes the interaction procedures of PS elements without affecting the independence of their systems of indicators, measurements and thesauri.

Each PS element (EPS) has its own organizational form and uses process or functional management, as well as their combination (Shvedenko, 2019).

A distinctive feature of the proposed PS model is the way it organizes the integrating element—BPS, whose functions are focused on synchronizing or reducing the divergence of the target settings of PS elements to achieve a common goal.

## 20.3 Organization of Information Flows in a Polystructured System

The BPS information space is subdivided into segments of the outer and inner layers. Each PS element corresponds to a segment of the outer layer. The internal integrating layer of BPS consists of the domain ontology, the goal tree and the information model.

The structural components of PS, which form its basic functions, are the following aggregates:

- polimetric system of the polystructure body (PMS_BPS),
- metric system of a polystructure element (MS_EPS),
- target tree of the polystructure body (GT_BPS),
- target tree of the polystructural system element (GT_EPS),
- validator of filtering, grouping and data transformation (V_PMS_BPS-MS_EPS).

A schematic diagram of the relationships of these units is shown in Figure 20.1.

![](img/0dd4397c67b063014553965e4f1cf7e4_360_0.png)

- 1. Polymetric system for collecting, processing, storing and transmitting data of the polystructure body PMS_BPS
- 2. Polystructure body BPS
- 3. Validator for filtering, grouping and data conversion V_BPS_EPSi
- 4. Polystructure system element EPS_i,
- 5. Metric system of collection, processing, storage and transfer of data of the polystructure system element MS_EPS_i,
- 6. Polystructural System PS
- 7,8. Bidirectional information links
- 9. Data flow channel of the polystructural system element EPS_i (IoT, Internet, microprocessors, etc.)

FIGURE 20.1 An enlarged scheme of organization of information flows between the elements of a polystructured system and the body of a polystructure.

PMS_BPS acts as a tool for forming and coordinating the information data flows both in BPS and between BPS and PS elements and performs the following functions:

- assigning conditions for “cleaning” and completeness of a set of input data streams based on the specified business logic;
- defining the rules for translating input data into a single measurement system and their further processing (conversion, aggregation) to obtain metrics—key indicators used in decision-making at the operational, tactical and strategic levels of PS management;
- monitoring of deviations for specified time intervals of actual values of metrics from their target values, which are normative values of the objectives tree PS;
- calculation of the size of deviations of actual metric values to determine the type of management action;
- establishment of rules for transmitting signals on the emergence of an abnormal situation;
- routing of data on existing or predicted deviations of metrics values to relevant decision-making centers.

PMS_BPS includes the following:

- a set of metrics—aggregated and transformed metrics reflecting the state of PS objects and processes, which are managed in accordance with the BPS goal tree;
- a set of methods of aggregation and transformation of MS_EPS input metrics into PMS_BPS metrics;
- a set of methods to compare actual and predicted values of PMS_BPS metrics and their normative values;
- conditions and rules for routing PMS_BPS metrics deviation values to decision-making centers (points of active influence on changes in the properties of the managed system objects) to effectively achieve the specified PS goals.

Metrics are formed from the number of indicators that characterize the state of a property or group of properties of the system objects. Each metric is paired with a goal tree sheet to evaluate the deviation from the normative indicators of the system. Depending on the deviation, a signal is formed to be sent to the appropriate decision-making center. A distinction is made between the magnitude of deviations for sending a signal to the areas of operational, tactical and strategic centers of formation and decision-making. The ranges of these critical deviations are set for each control object.

The connection between BPS and the metric systems of its elements MS_EPS is established through the validators of filtering, grouping and data conversion V_PMS_BPS-MS_EPS;

Depending on the types of tasks to be solved, BPS can interact with two or more PS elements. Any interaction implies the adjustment of management parameters, which implies the adjustment of

- the structure of the goal tree;
- the system for measuring changes in the state of the objects under study, as well as deviations of their values from the established standards;
- values of normative indicators, which correspond to the values of the leaves of the objectives tree.

The construction of GT_BPS is carried out in accordance with the goal facing PS, and may change over time, depending on environmental conditions, the parameters of resource availability of one or more of its elements, as well as a number of other factors.

The hierarchical structure of GT_EPS contains the branches of the goal tree corresponding to the functions of the EPS objects, and its leaves are the normative values of indicators characterizing the state of individual properties of objects, when performing one or more processes. Each object of the managed system can correspond to several leaves in the goal tree structure.

Like GT_BPS, GT_EPS can be periodically restructured, which is associated with the change of PS targets or PS elements. Similarly, their alignment methods may change. The parameters of the BPS goal tree are set in relation to the goal trees of PS elements. Each GT_BPS sheet corresponds to a subset of the BPS indicators.

The schematic diagram of the information interaction of GT_BPS, GT_EPS, PMS_BPS, and MS_EPS is shown in Figure 20.2.

PS control depends on the accuracy of its state prediction for a given time lag.

The most promising technologies for the realization of this function have become digital twins.

Therefore, the digital twin is an important element of PS.

Figure 20.3 shows a scheme of interaction of digital twins with other PS components.

The GT_BPS configuration component sets the hierarchy of PS goals and subgoals, as well as the links between them, and sets the normative values of the GT_BPS leaf indicators. It consists of several modules:

- a module for constructing the goal tree and defining the rules and conditions for its decomposition;
