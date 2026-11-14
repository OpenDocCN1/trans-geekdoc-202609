

Considering the discussion above, this paper presents an approach to improve the maintenance efficiency through DAS using a morphological approach for the proper hardware selection combined with a process-modeling tool providing the adequate information to fulfill the needed maintenance task. The goal of the proposed process model is to systematically identify functionalities of the emerging technologies on the market and apply the functionalities to requirements in order to find appropriate assistance systems for various industrial applications. Therefore, an overview on present digital assistance solutions is given and a morphological approach for the elicitation of derived requirements on digital assistance solutions is presented.

## 1.2 Digital Assisted Maintenance (DAM)

The emergence of novel wearable technologies (in this paper referred to as a type of DAS) such as smart glasses, smart watches and tablets spurred new concepts of service support systems [9]. DAS combined with Cloud manufacturing concepts provide an opportunity to deal with the increasingly complex maintenance procedures [3], [9]. DAS create the potential to shape new working environments in which modern technology is used to assist workers in activities that are challenging in terms of their cognitive complexity [14]. Via interfaces, corresponding process data are processed and visualized by software components embedded into assistance system to support maintenance operators with relevant information, e.g. by means of head-mounted displays or portable devices. A strong focus of literature is the exploration and identification of application areas for implementing and deploying DAS [5]. To implement DAS, the service-oriented architecture approach has become established. Although innovative technologies, e.g. web services, have already been employed in industrial applications [15], [16], their usage in maintenance support has not been sufficiently well emphasized. A preliminary chronological market and literature analysis with regard to suitability and industrial applicability (i.e. technology readiness) of DAS, in particular wearable devices, is shown in Fig. 1.

![](img/a2f5eed6507498d886a06be86239344b_96_0.png)

Fig. 1. Overview of digital assistance systems on the market and their market entrance.

As a result, the four most common DAS in industrial application are: industrial tablets, smart watches, smart phones and head mounted displays [12], [17], [18], [19]. While the pros and cons of handheld devices (industrial tablets, smart watches, smart phones) are well known and elaborated in literature, the potential of head–mounted displays are disputed. The most value–creating functionalities of head mounted displays lie in information provision, environmental identification and tracking [6]. The opportunity to access information hands free provides additional benefits. However, due to various technical limitations and challenges, such as wear comfort or poor wireless network connections, the question of usefulness in maintenance still arises.

## 2 Selection Methodology

This section explains the methodology of the developed model to select proper DAS for maintenance tasks. The proposed model builds on three integrated elements (see Fig. 2): i) Morphological Approach, ii) Application Layer and iii) Device Selection Layer.

![](img/a2f5eed6507498d886a06be86239344b_97_0.png)

Fig. 2 3-layer model for selecting proper digital assistance systems

The first element represents a morphological box, which has been developed to facilitate and optimize the selection of suitable DAS. The second element represents the application domain. The application layer provides the individual user-specific system requirements as well as application scenarios (i.e. describing and representing maintenance activities). Subsequently, the system and hardware requirements resulting from i) the predefined parameters of the requirement morphology and ii) from the application level are evaluated and, according to their overall systemic meaning, compared with the potential technology solutions. Algorithms and correlation analyses within this system are used to ultimately map the requirements to existing digital assistance solutions. Using the proposed approach, a (combination of) DAS is selected and linked to maintenance activities. Finally, we collect feedback through employing the selected digital assistance system to improve the quality of recommendations and to identify the strengths and weaknesses of each system in association to practical use-cases.

### 2.1 Morphological approach

In order to facilitate and optimize the selection of suitable DAS for supporting maintenance operations in manufacturing industry, a morphological approach has been developed. A Morphological Analysis (MA) represents a method for systematically structuring and analyzing a set of relationships contained in multi-dimensional, non-quantifiable problem complexes [20], [21]. MA usually consists of three steps. First, the problem complexity is categorized into several dimensions. Second, all possible conditions (also referred to as parameters) to each dimension are identified. These parameters represent the characteristics of each dimension. Finally, a morphological matrix is developed based on the identified dimensions and their assigned condition parameters [22]. Figure 3 depicts a morphological matrix, which contains a collection of identified features that are critical to selecting an assistance system. Key features for an adequate assistance system can be categorized into three groups: i) requirements regarding the application (software): How and to what extent maintenance information is presented to maintenance operators and engineers towards increasing their performance in an affordable manner? ii) requirements regarding the information system: How and to what extent maintenance information is tailored to the application? iii) requirements regarding the hardware: which hardware should be applied for the selected case?

| Dimensions | Requirement Morphology Parameters | | | |
|---|---|---|---|---|
| Type of support | Physically | | | Information |
| Type of assistance systems | Stationary | Mobile installation (e.g. on a notebook) | Hand device (for control on a smart phone) | Wearable (smart glasses or watch on other) |
| Two hands are needed to carry out the activity | No | | | Yes |
| Application | Maintenance | Assembly | Logistics | Others |
| Environmental conditions | wet | dusty | Unsafe lighting conditions | noisy environment |
| Operator | Gloves required | Glasses required | | Helmet required |
| Type of use | One-time use (training, education, ...) | Selective use | | Regular use |
| Data transfer | Local via cable | Wireless via private network | | Wireless via public network |
| Human Machine Interaction | Unmodal | | | Multi-modal |
| Type of interaction | Monological (without possibility of interaction) | | Dialogical | Communicating (for example via chat functionality) |
| Support provided | Information | Instruction | Interference | Documentation |
| Method of providing information | Visually | Auditive | | Kinesthetic |
| Type of Visual Information Presentation | On-Screen Display | On-Site Projection | | Augmented Reality |
| Scope of visual presentation | No visual information | Simple presentation (texts, images or animations) | Multimedia presentation (videos, animations, ...) | Advanced presentation (selected from database) |
| Type of information input | Manual (via actuator) | Verbal (via voice control) | Gesture recognition | Automatic (via sensor) |
| Scope of user customization | Predefined configuration with regard to input and output | Individual configuration with regard output possibly also input | | Individual configuration with regard input and output possible |
| User categories | No user groups possible | Different user groups possible | | Individual configuration with regard to input and output |
| User recognition | None | User login and initialization | | Automatic detection and initialization of the user |
| Situation and motion detection | None | Using motion sensors | Using optical sensors | Other technology |
| Flexibility (with regard to reconfiguration) | Substantial adjustments necessary | Adjustments necessary (solvable by specialist) | Adjustments necessary (by specialist on site) | Small adaptation possible for the user itself |

**Fig. 3** Morphological Matrix with defined dimensions and parameters

Based on a literature review and collection of manufacturers’ data, we derived and determined 20 relevant criteria to assess the digital assistance system requirements. These requirements represent the dimensions within the morphological matrix. To further systematize the requirement analysis, the requirement elements are classified below using a morphological matrix in Fig. 3. This morphological matrix contains a collection of general condition parameters of the presented requirements. Based on the individual user-specific system requirements and the application scenario, the characteristic parameters can be identified. Thereby, the requirements are highlighted in color and optional requirements are shaded in color. It should be noticed that each answer can affect more than one choice regarding the hardware, software and visualization method. For the selection of a suitable digital assistance system a decision hierarchy

