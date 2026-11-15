
![](img/0dd4397c67b063014553965e4f1cf7e4_687_0.png)

![](img/0dd4397c67b063014553965e4f1cf7e4_687_1.png)

FIGURE 39.2 (a) The three clusters and most representative words attached to each cluster for the k=3 implementation of the K-means algorithm applied to the abstracts of the 113 reviewed papers. (b) The ten clusters and most representative words attached to each cluster for the k=10 implementation of the K-means algorithm applied to the abstracts of the 113 reviewed papers.

On a space scale, there are studies on (1) building elements (such as elevators/electrical installations) or structural elements (studying the behavior of materials and structures under stress), (2) entire buildings, (3) regions in cities, and (4) urban-scale digital twins (Figure 39.3a). On a time scale, studies deal with different moments in a building's lifecycle: from (a) understanding the existing conditions on a site that should be furnished, to (b) design and conceptualization, (c) building or construction phase, and (d) building management. None of the studies we found deals with (e) buildings' retirement/ end of life, although we suggest this is an important aspect to consider when designing digital twins (Figure 39.3b).

These two scales are merged into one map (see Figure 39.4). For each level on the space scale, studies can deal with a level on the time scale in the life cycle of a built project. The only space level that includes all time levels is the building scale. As architecture does not typically deal with designing and building elements, these two aspects of the time scale are not included in the map. While none of the studies we found deal with the end of life or retirement of a built project, we suggest that research should go into creating digital twins that inform what should happen to a building or its parts once they are demolished. The district and urban scale do not have a retirement/end-of-life stage, as their lifespans cannot be foreseen. We structure the remaining of this section based on this map and on these two axes.

## 39.3.2.1 Studies about Building Parts, Building Elements, and Structural Elements

### 39.3.2.1.1 Existing Built Conditions/Built Heritage

A significant portion of the literature deals with ways to create digital representations of the built heritage or existing infrastructure. For example, Ref. [69] presents a study where they laser scan interior environments and gather point clouds, enrich them with semantic data, and propose to use this as a basis for a digital twin. Before adding semantic data to the point cloud, it is preprocessed and segmented marking homogeneous regions to identify physical features.

### 39.3.2.1.2 Management of Existing Building Elements or Structures

Some of the studies about digital twins include modeling and simulating heating, ventilation and air conditioning (HVAC) systems, or looking at building components such as elevators or escalators usage. For example, Ref. [76] develops a digital twin using the software Modelica [55] for an energy recovery ventilation unit to predict physical system behavior. Reference [12] reports on a post-occupancy study analyzing elevator usage. They establish an elevator operation simulation model, predict elevator usage under different conditions, and optimize operation measures.

material behaviour under different types of stress /energy use of a building component (i.e. ventilation unit)

CAD, BIM models detailing the buildings + IoT sensors monitoring different aspects: studies on indoor air quality, /water use use of building elements (i.e. elevators) /energy use

studies about /mobility, traffic /energy use /solar radiation /air quality /visibility

studies about mobility, traffic /people in cities /district energy use

> a digital representation is: cyber-physical

> a digital representation is: cyber-physical-social

Existing (Analysis of existing conditions) Built heritage Understand(ing)

Design(ing)

Simulation (of the new design in the existing context)

Construction site Fabrication / Production of built environment

Management of built environment

Retirement / end of life

FIGURE 39.3 (a) On a space scale, projects range from creating digital twins of buildings or structural elements, to twins for entire buildings, to studies on block scale, district, or city scale. (b) Studies can deal with different moments in a built project's life time: from understanding existing conditions about a site, to designing new buildings, construction, and facility management.

![](img/0dd4397c67b063014553965e4f1cf7e4_690_0.png)

FIGURE 39.4
Digital twins in architecture can be placed on a space-time map where the space axis represents the space scale of a digital twin, ranging from building element to urban scale, and the time refers to the point in a built element's life cycle.

## 39.3.2.2 Studies on Entire Buildings

### 39.3.2.2.1 Existing Conditions/Built Heritage

In the case of mapping the built heritage, the most used tools and practices involve using 3D laser scanning technology, and mobile phone technology producing point cloud data. Sometimes these are corroborated with aerial or eye-level photo imagery.

For example, Ref. [59] presents a method and case study of integrating point cloud data with annotated imagery. They create digital representations for the building that include: geometric information, semantic information such as object categories and text information. Reference [65] presents a method to create digital copies for heritage buildings as conservation tools to understand the structural properties and behavior of the built heritage. They create 3D surfaces produced by combining 3D point clouds obtained from laser scanning and photogrammetry and propose that 3D finite element models (FEM) can be developed based on the geometries derived from the 3D models.

In the case of structural maintenance, the most used tools include aerial imagery, open map data, and finite element analysis (FEA) tools. Reference [47] presents a method to automate the creation of a digital twin for an existing bridge, using annotated point clouds. The method follows a slicing strategy to generate 3D shapes using the Industry Foundation Classes (IFC), followed by fitting them to the labeled bridge point clusters.

Reference [37] proposes a systematic approach for making a digital representation of a highway based on Open Street Map data and their own engineering expertise. Reference [68] presents a study on a digital twin for a bridge that is used for preventive maintenance containing two elements: a maintenance information management system based on a 3D information model and a digital inspection system using image processing. Reference [1] presents a case study of a digital twin of an automated highway maintenance project. Based on interviews, they find that AEC practitioners face difficulties in (1) creating a shared understanding due to the lack of consensus on what a digital twin is, (2) adapting and investing in digital twin due to inability to exhaustively evaluate and select the appropriate capabilities in a digital twin, and (3) allocation of resources for digital twin development due to the inability to assess the impact of digital twin on the organizational conditions and processes. Practitioners used terms such as BIM, IoT, or BIM+IoT when asked to describe what a digital twin is and concluded that *the reality is that in the current practice and the foreseeable future, digital twins should still have limited technological capabilities*. Further, finding out what changes should be made in the organization in order to create, maintain, and generate value from a digital twin is still unclear.

### 39.3.2.2.2 Design of New Buildings

BIM acts as the shared platform for architecture, structural engineering, and HVAC work and is often referred as the basis for digital twins [6,31,38,41,79]. In the design of new buildings, the BIM is one of the first steps in creating a digital twin, after the digitalization of existing conditions for where a building should be inserted. However, there are sometimes problems and discrepancies between a building as designed (as it should be) and the building-as built, as pointed out by Ref. [38].

BIM can be easily integrated with VR systems, yet it still faces integration problems with other building management systems (BMS), geographic information systems (GIS), and IoT sensor data. BIM adoption is still strongly correlated to country GDP, with countries from the Global North leading the way, but it is expected that BIM and the IFC will become mandatory in public contracts for countries around the world in the future [3,78,82].

Apart from BIM creation as a basis for digital twins, many studies describe projects where the behavior of a structure or a part of a structure is simulated to understand material behavior under different types of stress. In Ref. [18], a digital twin for a structure containing a scaled physical model and its digital simulation is presented and automated decision-making for structural integrity is discussed. Similarly, Ref. [44] presents a case study for a digital twin of a long-span cable-stayed bridge. They assess the collapse fragility under
