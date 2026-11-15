
![](img/0dd4397c67b063014553965e4f1cf7e4_102_0.png)

Taylor & Francis

Taylor & Francis Group

http://taylorandfrancis.com

## Part 3

### Digital Twins Technology

## 6 Key Technologies of Digital Twins: A Model-Based Perspective

Serge P. Kovalyov
Russian Academy of Sciences

### 6.1 Introduction

Recall that a digital twin (DT) is a virtual copy of a physical asset that promptly reproduces and alters the state and behavior of the asset [1]. DT intensely employs Industry 4.0 data-driven artificial intelligence technologies and simulations for adaptive monitoring, forecasting, optimization, and controlling asset performance [2]. The most accurate is the DT initiated at the beginning of the asset lifecycle, developed incrementally together with the asset, and put into operation synchronously with it [3]. Computer-aided design (CAD) tools apply to create a DT at the design stage, long before the asset comes into existence. Such an early DT is useful as a virtual testbed for evaluating alternative design decisions and choosing the best one.

Moreover, the initial DT is synthesized fully automatically when advanced artificial intelligence technologies, known as generative design [4], are used. The generative design process consists of the following steps: deriving a multi-objective optimization problem from stakeholder requirements for the asset, the automatic search for the best solution to this problem, and the subsequent physical implementation of the solution through automatic manufacturing. The solution determines the initial DT, so the latter accurately reflects the physical asset at the beginning of their synchronous operation. Later in the lifecycle, the generative design technology can be invoked again to automate planning of an asset upgrade or renovation, with the design space narrowed to a suitable “neighborhood” of the up-to-date DT. For example, generative design has been successfully applied to dependable parts in mechanical engineering, using topological optimization and 3D printing.

We will employ a much more complex asset as a running example: a power energy system. DT-based energy control applications show promising results in load/generation forecasting, power flow analysis, optimal energy storage scheduling, fault diagnosis, electrical machine health monitoring, and other relevant areas [5]. Yet, these applications are difficult to scale to real-world power grids and cost-effectively adapt to everyday operation and maintenance. A full-fledged grid DT requires high-end IT resources and a lot of skilled labor to set up: it has to promptly follow long-running multi-step processes involving numerous widely distributed disparate facilities and affected by hidden technical, social, and economic factors. For similar reasons, generative design technologies are much less productive in the power industry than in mechanical engineering [6].

Major difficulties stem from the complexity and diversity of models that have to be included in the DT to describe the complex asset properly [7]. Models differ from each other both horizontally, by parts/units they describe, and vertically, by concerns/viewpoints/aspects they represent. The integration and coherent operation of numerous disparate models tend to consume a huge amount of computer and human resources. In essence, the DT composition process has to reproduce the asset construction process digitally. Thus, DT development activities belong to the problem domain of model-based systems engineering (MBSE). Any technology should be largely model-based to apply for DT. Figure 6.1 shows relations between DT and MBSE [8].

To date, MBSE is a mature methodology supported by an advanced theoretical basis, a convincing success story, and powerful technologies and tools.

![](img/0dd4397c67b063014553965e4f1cf7e4_106_0.png)

FIGURE 6.1 Relations between digital twin and model-based systems engineering [11].

To fight complexity, the heterogeneous domain is considered as a whole only at the first (architectural design) and the last (integration) phases of a typical development process. At the intermediate phases, models are developed in parallel using different languages and tools, oblivious of each other, yet ready for smooth integration via semantic mediation [9]. To facilitate rigorous description and verification of model composition and integration procedures, MBSE has recently obtained a formal foundation built upon the mathematical framework of category theory [10,11]. Indeed, category theory is a branch of higher algebra specifically aimed at the unified representation of objects of different nature and relations between them [12].

This chapter presents the key technologies that facilitate model-based design and development of the DT. We show that innovative digital technologies empowered by advanced algebraic techniques make DT cost-effective to compose and operate while maintaining sufficient completeness, accuracy, and usability for practical purposes.

This chapter is organized as follows. Section 6.2 presents the model-based DT architecture. Sections 6.3–6.8 provide overviews of the following key technologies: mathematical modeling, Internet of Things (IoT), interactive schematics and augmented reality (AR), electronic document management, master data management, and ontological modeling, respectively. Section 6.9 introduces an algebraic approach to DT composition based on category theory. Some conclusions and directions for further research are outlined in Section 6.10.

### 6.2 The Model-Based Digital Twin Architecture

Different approaches to the DT architectural decomposition exist [1]. For example, a layered architecture is proposed, with the physical asset on the lowest layer, intelligent control services on the upper layer, and various mediating components in-between. Alternatively, the functional decomposition applies to break DT down to data storage, information exchange, calculation, visualization, and other modules. In contrast, the MBSE perspective suggests decomposing by models that differ in kind and viewpoint, highlighting the specifics of DT among other digital systems. The typical DT consists of models of the following kinds [3]:

- ontology model;
- digital diagrams and visuals;
- electronic documentation;
- information model;
- real-time data;
- mathematical and simulation models.

![](img/0dd4397c67b063014553965e4f1cf7e4_108_0.png)

FIGURE 6.2
The model-based digital twin architecture.

To provide convenient access to the models, they are often designed as (micro) services [13]: the service-oriented architecture hides model implementation details from the user and provides flexibility in orchestrating the interaction between models. During the asset operation, the models interact intensively with each other and with the environment. Model interaction use cases include data exchange, data referencing, cross-model data verification, and data structure generation, as shown in Figure 6.2 and described in detail below.

### 6.3 Mathematical Modeling and Simulation

Mathematical (in a broad sense) models of an asset directly implement the purpose of its DT: analyze the asset operational state and determine control commands and/or recommendations necessary to bring it to a (sub)optimal state.

The analysis includes evaluation of unknown or missing state variables and forecasting variable values for some period into the future. The control actions are then determined by solving an optimization problem, targeted to maximize performance and/or minimize losses, over the asset state space.

For a more comprehensive analysis and control, models apply that are capable of simulating (i.e. imitating in a digital environment) the asset behavior in different operational scenarios. The extensive use of simulation is one of the most significant achievements of MBSE. At the design stage, simulation facilitates comparing alternative solutions for a particular design problem. Displayed as an interactive graphical animation, the simulation is useful as an instructional tool to train the asset personnel. When twinning complex multi-step processes, the DT employs simulation of a particular kind called discrete-event [14]. The discrete-event simulation represents the asset behavior as a discrete sequence of typed events that indicate elementary changes in the asset state and environment.

Many tools support composition and execution of mathematical models and simulations, ranging in scale from a smartphone app to a supercomputer suite. Small-scale models may be used for rapid prototyping of a DT or to twin a simple asset. Large-scale assets, like power systems, require more powerful tools. Currently, there are three fundamentally different types of the models:

- “First-principles” (physical, biological, economical, and so on) models based on the numerical solution of equations and optimization problems that describe phenomena involving the asset;
- statistical models based on machine learning on the historical asset state and behavior data, including neural networks;
- asset expert knowledge and decision-making models, such as rule-based and multi-agent systems.

Numerical models based on solving discretized algebraic, differential, and stochastic equations have a long development history in computer-aided engineering (CAE) software. CAE tools include solvers and optimizers for mechanical and multiphysical stress analysis (using finite element method (FEM) or so-called mesh-free methods), computational fracture mechanics, multibody dynamics and kinematics, computational fluid dynamics, computational electromagnetics, and many other areas. Traditionally, CAE tools were intended for use in a design office to evaluate engineers’ decisions, processing manually entered data under very weak time constraints. Recently, widely available computers reach performance sufficient to execute CAE algorithms in soft real time along with the asset operation, processing data that arrive from sensors. This allows using CAE in DT during the asset operation stage.
