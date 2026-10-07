# CYBER PHYSICAL SYSTEM—The Gen Z 401

insufficient for expressing the different variety of physical components prevalent in CPS and their interactions with cyber entities. Finding a balance between specification and generalization while developing an architectural style is difficult. We need to define three interrelated families that are concerned with the cyber domain, the physical domain, and their interconnection.

# 19.2.1 Cyber Family

The conventional domain for ADLs is the cyber side of CPS. Standard real-time monitoring and control applications are supported by the components and connectors listed below. The following are the component types:

+   *Data Centers:* These components serve as a data link between the system's computing units. These might simply be memory blocks which are passive in a simplistic system. There may be additional information indicating which elements are able to read and write in the data storage units in a complicated system.
*Computation:* Computation components work with data store components and update it. Filtering, state estimation, and control components are included in this category.
*Interfaces to Input/Output:* Sensing and controlling the physical world is achieved through implementation of timing computations and operational procedures. Smart sensor software that analyses raw sensor data, for example, falls under this category.

In addition to the computing parts of the software, it is necessary to represent the communication elements in the system in order to reason about software element timing and how it influences the physical behavior of the entire system.

# 19.2.2 Physical Family

At the architectural level, there are various obstacles in producing a proper functional replica of the physical side of cyber-physical systems. All of the elements needed to simulate the physical dynamics shouldn't be included in architectural models. Similarly, cyber components and connectors