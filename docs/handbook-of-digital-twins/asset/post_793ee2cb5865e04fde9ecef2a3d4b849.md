
![](img/0dd4397c67b063014553965e4f1cf7e4_40_0.png)

FIGURE 2.4
Spring model: four forces shaping a digital twin.

While going with practitioner’s “best-suited option”, without evaluating other possibilities, can be a viable option in the cases where the practitioner happens to be creative and visionary, in most cases, it risks: (1) selecting a sub-optimal or an overly optimistic solution that might later have to be altered or disposed-off completely (Fjeld 2020) and (2) misaligning with other project stakeholders who might have a totally different conceptualization about the digital capabilities a DT would deliver (Agrawal, Fischer, and Singh 2022). Therefore, to alleviate the above challenge, our framework forces the practitioners to ask themselves before deploying DTs: What does digital mean for their use case?

Twinning Perspective (What Are We twinning?): Even if the ambition in many cases is to create a so-called “most comprehensive DT”, where all entities across the lifecycle are fully digital, the reality is that most work systems today and in the foreseeable future will only be partially digital. Feng et al. (2020) note that the idea to have a DT that is a comprehensive virtual replica of all physical and functional activities can result in huge costs (West and Blackburn 2017) and make it difficult for manufacturers to adopt, invest, and implement DT. Therefore, to alleviate this challenge, our framework asks the practitioners a second fundamental question: What are they planning to twin for their use case?

The digital perspective aids practitioners in selecting the technological capabilities in a DT, while the twinning perspective forces them to identify the right scope of digitally twinned entities. The digital perspective anchors on the elements: (1) type of digitalization and (2) extent of digitalization. Together, these two elements can help practitioners understand what digital means to them. Similarly, the twinning perspective anchors on the elements: (1) system boundary and (2) types of entities twinned. The following paragraphs describe these elements in detail:

### Type of Digitalization

All digital capabilities are not created equal. While some provide more benefits, they are difficult for the practitioners to adapt, invest, and deploy (Agrawal et al. 2022). On the other hand, relatively basic capabilities may provide fewer benefits, but reduce the necessary efforts for adoption (Lu et al. 2020). Therefore, it becomes important for practitioners to select the right type of digitalization for their use case.

To choose the right type of digitalization, it is important to first understand the types of digitalization available, and then select the one that meets the needs of practitioners. But what are the types of digitalization available? Types of digitalization, a four-step hierarchy by Gartner (2013), provide this categorization for digitalization. The hierarchy is as follows: Description (“What is happening”) → Diagnostic (“Why is it happening?”) → Prediction (“What will happen?”) → Prescription (“What should be done?”). To complete any task, humans start by gathering the required information and understanding what is happening (i.e., description), explain why it might be happening (i.e., diagnostic), predict what may happen next based on this understanding (i.e., prediction), and finally decide what to do next (i.e., prescription).

The IoT, wireless monitoring, augmented reality/virtual reality, drones, and 3D scans are a few examples of current technologies that are essentially trying to improve the description level. The diagnostic level includes technologies and techniques such as confirmatory data analysis, statistical tests, and causal inference, as they help to diagnose why certain things are happening. Design simulations, AI methods, and predictive analytics fall in the prediction category.

### Extent of Digitalization

Following the type of digitalization, practitioners must decide on how much to digitalize. Any digitalization type is not all or none, but varies across a continuum of levels, from no automation to full automation. At a higher level, DT would have more autonomy and would be able to handle more difficult tasks. While this would provide more benefits, it would also be challenging to achieve. On the other hand, at a lower level, most of the work would still be completed by the human operator with some assistance from DTs. Therefore, the extent of digitalization forces practitioners to consider which scenarios should be handled by humans and which situations by DT.

### System Boundary

Many DT deployment errors emanate from people failing to define the exact boundaries for DTs and expecting anything and everything from it. Some people argue that DT should be made for the whole lifecycle of an asset to produce maximum value. Even if this is true, practitioners might not have direct control over many parts of the asset lifecycle due to contractual or legal structures. As a result, practitioners should consider the following two factors when defining the appropriate system boundaries for DT deployment:

- 1. Local versus global optimization: Although a global optimization (end-to-end optimization) of an asset or an entity would be ideal, in most real-world scenarios, this is not possible due to practical, legal, and financial considerations. Due to this, practitioners do not have control over the entire lifecycle, thus emphasizing the need to define the appropriate system boundaries for twinning before creating a DT.

For example, in a building construction project, an ideal situation would be to use DTs to produce a building that is optimized together for design, construction, operations, maintenance, and sustainability. As these are interdependent functions, like design affects construction and maintenance, an ideal or globally optimized DT would require all disciplines to work together from the start of the project. But this rarely occurs in real life, and usually different disciplines are handled by independent contractors. Therefore, a global DT for the whole lifecycle of the asset is out of question. In the best-case scenario, each contractor would locally use their own DTs to optimize the function that they are responsible for without thinking of the other disciplines (or global optimization).

- 2. Level of detail of insights: DTs can provide insights at different scales, from fine details to large systems. Therefore, practitioners should determine the scale of insights they want and define the system boundaries accordingly because this will impact the data required for DTs and algorithms they use. Defining the scale too broadly obscures any relevant operational insights and defining the scale too narrowly makes the problem less worthwhile for solving. For example, let us consider a DT that analyzes productivity on a project. If DT provides the insights just on an aggregate level, like productivity was down 10% last month, then practitioners cannot understand where to improve. More detailed insights reflecting the change on a component level would have been better.

### Types of Entities Twinned

Typically, all production activities can be viewed as delivering a ‘Product’ (or service) by an ‘Organization’ following a certain ‘Process’ to make the delivery possible. Therefore, the aspects of a project that the project delivery team or a company can, at least to some extent, control, fall into three categories: Product, Organization, and Process (POP) (Fischer et al. 2017). Hence, each element of POP can be improved digitally or, in a way, digitally twinned. As discussed in Section 2.3, limiting the twinning to only one element (most people restrict it to product) can limit the benefits of DT.

For example, on a manufacturing project, a practitioner makes a DT that predicts whether an equipment needs to be shut down for maintenance. While DT could detect the need for repair if the equipment (or product) is only twinned, it would not be intelligent enough to know that shutting down for repairs would cause production delays and bottlenecks because it does not understand the process or the organization in which the equipment functions. Therefore, the decision to shut down would still have to be made by the engineering team.

A practitioner must therefore decide which elements they would like to twin. Of course, the natural instinct is to start with the product, but we recommend thinking further ahead like twinning the process in the manner of (Papacharalampopoulos and Stavropoulos 2019) who optimizes processes using DT, as well as (Parmar, Leiponen, and Thomas 2020) who optimizes organization with DTs.

### Why a Spring Representation

In Figure 2.4, we use a spring representation to connect the four elements to show that ‘Digital’ and ‘Twin’ components of a DT are greatly intertwined with one another, and a change in one affects the other. Further, the model emphasizes that finding the appropriate DT is an iterative process, where the practitioner answers the question one observes the effects on other parts, and repeats the process.

For example, if a practitioner decides to implement “prediction” type of digitalization on a construction project, they will have to reduce the system boundaries if they did not have appropriate data for the whole project. Similarly, it would be difficult to make accurate predictions if the practitioner only twins the asset (or the building) without considering the process or the organization behind it as discussed above. Agrawal, Fischer, and Singh (2022) also observe the impact of the digital element on the twinning element in a highway maintenance case study.

## 2.5 Case Study

We demonstrate the framework’s application in a real-life case study to illustrate how practitioners find it useful in practice. Below we first describe the situation, and then detail how the framework was used in this case study.
