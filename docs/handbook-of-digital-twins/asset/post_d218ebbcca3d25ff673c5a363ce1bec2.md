
real-time, based on the bi-directional flow and complete volume of PEI, encapsulating the full lifecycle data to facilitate knowledge sharing and integration.

(Falckas and Karlis 2021)

## 31.2 Digital Twin Characteristics

Definition of the basic idea of the DT branches into the different characteristics an approach should include to be considered as a DT. These characteristics are and should be further discussed, since they comprise the base tools and processes the DT framework (DTF) provides, with the aim of staying true to the definition as it has been embraced by industry.

Four major keywords frequently seen in DT literature, along with their definitions, include:

- Multiphysics – different system descriptions must cooperate with each other;
- Multiscale – simulation must adapt to required accuracy of the application;
- Probabilistic – core purpose is to predict the future of a system, given an initial state;
- Ultrafidelity – offer the application-required precision down to the best achievable level, given the hardware.

These four keywords represent the pillars of any engineering procedure. It is important to keep in mind that representation of any real-world system will never be perfect, owing to physical limitations, and the DT is no exception to the rule. Rather, the DT concept offers a promising paradigm to become the best representor to date. The classic trade-off between time, cost, and precision remains. One novel concept offered is that this trade-off is included under the multiscale and ultrafidelity characteristics of the DT and is able to be included as an input, optimizable parameter to the application.

Information is the basis of the DT. It is retrieved from the physical entity and processed to create the virtual twin through the twinning process. Then, it is constantly, bi-directionally exchanged to maintain the link between the two spaces, enable control of the physical entity, and update the virtual twin. This information can be tapped into at any time to realise ancillary procedures such as condition monitoring or making predictions under varying assumptions. In addition, information is separated and filtered to provide services to end users of varying specialization, while preserving confidentiality according to industry standards. Therefore, sources, handling, and storage are of paramount importance. Information is extracted from raw data retrieved from the physical entity and is stored as structured data in hardware. This data comes from three major sources:

- Historical data;
- Real-time sensors;
- Models.

Historical data temper expectations and aid in setting the information retrieval experiment, calibrating sensory equipment, and making basic predictions. These data are currently included in maintenance reports, time series, or tables, but are aimed to be included in the DT of systems to aid in the advancement of future DTs. Sensors applied on the physical entity feed the DT with real-time information, and constitute the actual links forming one part of the Connections’ dimension. Finally, information simulated from tried-and-tested models can be considered as actual information embedded in the DT.

DTs are ultimately made of components, down to the lowest possible level. Each physical system is analysed to a fidelity. For example, a permanent magnet synchronous electrical machine model may consist of the copper wiring, stator and rotor laminations, permanent magnet blocks, screws and miscellaneous components. These are characterized by their geometric orientation in 3D space, the material properties, physical interactions, and environmental conditions. Depending on the method or quality of information retrieval and modelling, the Black–Grey–White Box paradigm aids in understanding the various approaches in twinning these components in the virtual space, as depicted in Figure 31.1.

![](img/0dd4397c67b063014553965e4f1cf7e4_554_0.png)

**FIGURE 31.1**
The Box paradigm illustration on describing physical components in the virtual space: (a) Black Box, (b) Grey Box, and (c) White Box.

- a. Black Boxes include only inputs and outputs. Inner workings of the component are unknown.
- b. Grey Boxes can model the component’s effects and results, with theoretical knowledge.
- c. White Boxes contain knowledge of all the functionalities and inner workings of the model.

The advancement of technology has improved the amount of information that can be gathered from the virtual space. Today’s simulators can test the virtual model’s performance capabilities to the desired degree, without carrying around unnecessary details. On the physical side, sensory, memory, and bandwidth advancements increase both the availability and quality of data.

To deliver the essential benefits gained from the linkage between virtual and physical models, a Unified Repository that links the two models together is required. Its main purpose is to enable a two-way connection between the virtual and physical models.

On the virtual side, a unique mark in specific areas (such as the centre of the rotor of a machine) can serve as a unique tag for the physical model. These marks can create a lightweight model while highlighting specific areas.

### 31.2.1 Internet of Things in Industry and Effects on Digital Twinning

“Internet of Things (IoT) is a term given to devices connected to the internet, with a sense of intelligence and the ability to collect information on their environment”. This connection between all devices gives their user the ability to watch everything synergistically, and is intrinsically intertwined with the idea of the DT. Furthermore, when considering the DT of a single product or process, the IoT can connect different DTs together and enable data exchange and history comparison, enabling specialized decisions to achieve a specific goal.

A specialized subcategory, the Industrial IoT, is similar but refers to industrial processes. Like its broader counterpart, it can have a huge impact on improving manufacturing processes by providing a specialized scope on the amount of data that can be used for the construction and development of the virtual model. In this way, the performance, production rate, costs, waste, and many other critical deliverables within the industry setting can be improved significantly.

Simplistically, the IoT facilitates data aggregation and filtering. One primary IoT challenge is the effort to control the flow of data in the system, leveraging unstructured data volume. Data filtering is essential since part of it may be useless, slowing and convoluting PEI. Another challenge is the existing infrastructure, especially in smaller industries and less developed countries, where upgrading is even more important. The infrastructure is currently technologically behind the vision of IoT due to its rapid growth in the last decade.

The Digital Twin supports three of the most powerful tools in the human knowledge, Conceptualization, Comparison and Collaboration, as put by Grieves (2014).

When humans look at a problem, they **conceptualize** its context. DT can create different scenarios produced from the virtual model and pinpoint the actual development of the problem and most importantly, provide insight on issues that may have been lost on traditional problem formulation, owing to difficult to discern variables.

**Comparison** of desired and actual results is important in both problem solving and prototype engineering. The DT is surmised to be the best tool in evaluating an ideal characteristic, the tolerance limits around that ideal measurement, actual results, and future predictions. This process can save precious time in the physical space, where failed efforts are both costly and time-consuming.

**Collaboration** between both different parties and approaches is important to achieve highly specific goals. The DT not only facilitates sharing of ideas and existing endeavours but also intelligent approaches such as a human theory and an Artificial Intelligence (AI) machine learning approach. DTs can communicate between each other and selectively extract data and use them as an input in their virtual model. In this way, they share “experience” in a never-before-seen scale and use it to predict more quickly and accurately.

### 31.2.2 Data Sharing Issues in Industrial Internet of Things

One can surmise that the DT depends almost solely on the integrity of the data provided to be built correctly and thus be useful in industry, where immediate results and returns on investment are required. One glaring issue in this chapter’s authors’ relevant work is the low availability of proper form of industrial data when a singular application is concerned. For example, synchronous generator condition monitoring during shutdown is typically made once a year, even less when sensors and previous measurements indicate healthy operation. Furthermore, signals regularly received often are integrated under large intervals, obscuring transient insights where most of the information regarding the inner workings of the system is stored. Finally, high-fidelity monitoring (small interval measurements) is done on a very limited basis and does not cover an indicative portion of the product lifecycle. These factors render case-by-case digital twinning largely ineffective compared to traditional condition-monitoring techniques, especially for smaller industries where usually no predictive maintenance is done at all.

This issue is one not to be taken lightly, as according to a pertinent research, a budget of $2bn with an estimated 12% annual growth is spent on maintenance of the large electrical machines (EMs) annually, $1.4bn of which is spent on plants without a diagnostic procedure. State-of-the-art paradigms
