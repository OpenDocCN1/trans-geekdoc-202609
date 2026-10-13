
# Inference Control Using Semantic Web Technologies

Inference is the process of forming conclusions from premises. This process is harmful if the user draws unauthorized conclusions from the legitimate responses he/she receives. This problem has come to be known as the inference problem. An inference controller is the device that prevents a user from drawing unauthorized conclusions. We have studied the inference problem extensively in the past. Specifically, we have defined various types of inference strategies and developed inference controllers that handle certain types of inference strategies [[THUR1993](#ch18.xhtml#ref18_35)].

Previous work to build an inference controller to protect data confidentiality was described in the late 1980s and early 1990s [[THUR1987](#ch18.xhtml#ref18_32), [THUR1993](#ch18.xhtml#ref18_35)]; however, this work was mainly in the area of multi-level secure databases and supported limited reasoning capabilities. Our current work is a substantial improvement over prior efforts with more sophisticated reasoning and policy representation techniques through the use of semantic web technologies [[THUR2014](#ch18.xhtml#ref18_36)]. We use as our data model the `Resource Description Framework (RDF)`, which supports the interoperability of multiple databases having disparate data schemas. In addition, we express policies and rules in terms of semantic web rules and constraints, and we classify data items and relationships between them using semantic web software tools, such as `Pellet`, `Jena`, and `Protégé` [[SIRI2007](#ch18.xhtml#ref18_30), [CARR2004](#ch18.xhtml#ref18_5), [KNUB2004](#ch18.xhtml#ref18_19)].

Our work has focused on classifying and protecting provenance data which is a kind of metadata that captures the origins of single data items of interest, as well as other relevant information such as data manipulation operations and temporal information [THUR2014]. Though it is acceptable to represent provenance in any data format, it is sometimes easier to visualize its structure using a directed graph layout. Therefore, we will refer to the provenance data as a directed graph, because a directed graph structure, besides being popular, has many advantages with respect to data modeling in a semantic web environment. The semantic web extends the `RDF` graph data model to have reasoning capabilities through the use of formal semantics. In our work, we used the reasoning capabilities of the semantic web to support the inference strategies of the inference controller. Furthermore, we presented several new query modification (i.e., rewriting) techniques that can be used to enforce security policies over a provenance graph.

In this chapter, we discuss inference control that employs inference strategies and techniques built around semantic web technologies which can be utilized for inference control in social media. Our work has focused on inference control for provenance data that is represented as `RDF` graphs. Our methods can be adapted for social network data since such data can also be modeled as `RDF` graphs. We have also provided the detailed implementation of the inference controller. It should be noted that access control is at the heart of our work on inference control. That is, not only do we prevent access to unauthorized data directly, but we also prevent access to unauthorized data indirectly via inference.

The organization of this chapter is as follows. Our design is discussed in [Section 18.2](#ch18.xhtml#sec18_2). Query modification is discussed in [Section 18.3](#ch18.xhtml#sec18_3). Our approach to the implementation is discussed in [Section 18.4](#ch18.xhtml#sec18_4). Provenance aspects will be discussed in [Section 18.5](#ch18.xhtml#sec18_5). Implementation details are given in [Section 18.6](#ch18.xhtml#sec18_6). Concepts in generators are discussed in [Section 18.7](#ch18.xhtml#sec18_7). A medical example is given in [Section 18.8](#ch18.xhtml#sec18_8). Constraints are discussed in [Section 18.9](#ch18.xhtml#sec18_9). Next-generation inference controllers are discussed in [Section 18.10](#ch18.xhtml#sec18_10). [Section 18.11](#ch18.xhtml#sec18_11) summarizes this chapter. [Figure 18.1](#ch18.xhtml#fig18_1a) describes an architecture for an inference controller.

![Figure 18.1 Architecture for an inference controller.](images/fig18_1.jpg)

[Figure 18.1 Architecture for an inference controller.](#ch18.xhtml#Ffig18_1)

## 18.2 Design of an Inference Controller

### 18.2.1 Architecture

The unsolvability of the inference problem was proved in [[THUR1990](#ch18.xhtml#ref18_33)]. Its complexity is an open problem. While there is a need to analyze the complexity classes of the inference problem, still a lot of research has been pivoted around the implementations based on traditional databases. However, since provenance has a logical graph structure, it can also be represented and stored in a graph data model; therefore, it is not limited to any particular data format. Although our focus in this design is on building an inference controller over the graph representation of provenance, our inference controller could be used to protect the case with the traditional database as well. Also, the use of an `RDF` data model does not overburden our implementation with restrictions, because other data formats are well served by an `RDF` data model. Furthermore, tools such as the one discussed in [[BIZE2003](#ch18.xhtml#ref18_2)] convert relational data to `RDF` data.

Our architecture takes a user's input query and returns a response which has been pruned using a set of user-defined policy constraints. We assume that a user could interact with our system to obtain both traditional and provenance data. However, as our focus will be on protecting provenance, we will focus more on the design of the inference controller and the provenance data layers.

In our design, we assume that the available information is divided into two parts: the actual data and provenance. Both the data and provenance are represented as `RDF` graphs. The reader should note that we do not make any assumptions about how the actual information is stored. A user may have stored data and provenance in two different triple stores or in the same store. A user application can submit a query for access to the data and its associated provenance or vice versa. [Figure 18.2](#ch18.xhtml#fig18_2a) shows our design and some modules in our prototype implementation of an inference controller over provenance data. We now present a description of the modules in Figure 18.2.

![Figure 18.2 System modules.](images/fig18_2.jpg)

[Figure 18.2 System modules.](#ch18.xhtml#Ffig18_2)

#### 18.2.1.1 User Interface Manager

The user interface manager is responsible for processing the user's requests, authenticating the user and providing suitable responses back to the user. The interface manager also provides an abstraction layer that allows a user to interact with the system. A user can therefore pose either a data query or a provenance query to this layer. The user interface manager also determines whether the query should be evaluated against the traditional data or provenance.

#### 18.2.1.2 Policy Manager

The policy manager is responsible for ensuring that the querying user is authorized to use the system. It evaluates the policies against a user's query and associated query results to ensure that no confidential information is released to unauthorized users. The policy manager may enforce the policies against the traditional data or against the provenance data. Each data type may have its own policy manager; for example, the traditional data may be stored in a different format from the provenance data. Hence, we may require different implementations of each policy manager.

#### 18.2.1.3 Inference Engine
