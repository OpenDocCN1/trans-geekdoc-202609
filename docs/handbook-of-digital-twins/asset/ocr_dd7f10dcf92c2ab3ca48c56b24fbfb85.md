To describe the structures of objects and processes, the set-theoretic representation and the mathematical apparatus of graph theory are used, and to model semantics the language of predicate calculus is used.

The basic entities of the model are represented by sets, and the tree of goals and the structures of business processes are described with the use of graphs. Using the predicates of the first order allowed to develop the basic structures of the language of representation and manipulation of data in the object-process model (Shchekochikhin, 2017).

A reference model of the information system based on the object-process data model is proposed. The basic idea is that the construction of the information system (IS) is top-down—from the goal tree to the stages of business processes. And the movement of data during the operation of the information system is bottom-up—from IIoT data providers and controllers. The data is processed and aggregated during the execution of business processes, taking into account the business functions inherent in each stage of the business process. The aggregated data is further transferred to the leaves of the goal tree as the actual values of the cyber-physical system state indicators.

This way of organizing information flows involves the use of digital twins in the aggregation of data and the formation of predictive values.

The way the digital twin is implemented in this case is not decisive. The main factor will be the prediction accuracy and the time period for which the aggregated values will coincide with the predicted values with a given accuracy.

This is the main function of the digital twin metrology. The digital twin metrology provides a highly accurate measurement of the characteristics of a technical object and physical environment and supplies this data to the information system database.

To perform typical calculations, we will use a hierarchy of classes of objects of the subject area. As well as three types of polymorphism: structural, parametric and interclass, as detailed in Shvedenko (2019a, b).

One manifestation of polymorphism can be considered methods for calculating the probability of failure of objects of cyber-physical system.

One of the functions of the digital twin metrology should be the adjustment of the digital model depending on the primary data obtained, as detailed in Shvedenko and Shchekochikhin (2022).

The time to update the digital model must be justified by the costs of development, storage, measurement, transmission, adequacy assessment and other overheads.

Two options for implementing digital twin model transactions are proposed. The first approach is based on a constant time cycle of updating the digital model. The second approach is based on the idea of changing the digital model with periodicity, which depends on the value of the probability of occurrence of one or another event, for example, the probability of failure of one of the system objects.