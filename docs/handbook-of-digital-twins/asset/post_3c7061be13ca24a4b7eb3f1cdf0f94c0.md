
a separate discussion about the frameworks and types of DTs has been done. However, due to the complexity and diversity of built environment parameters and associated interoperability issues, a single model of DTs can’t be adopted. Amalgamation and customization of various DT models are required to develop a model for the DTs. A generic framework for the DT is presented below which is an effort to provide an idea about the different layers a DT can have.

A DT is a combination of several modules, such as a computer model, a physical model, communication services, and data analytics. These modules work in synchronization to monitor, learn, and optimize the complete system operation. However, the implementation of the DT concept may require new processes, methods, and novel platforms to interact with each of these modules. GDT for dynamic sustainability assessment can only be done by integrating the data from various sources for different sustainability parameters. The sources of information collection can be any but not limited to the real-time sensor, BMS, feedback devices at the public service use areas, cloud services, and asset management software. The asset information model is the key in the whole process that can lead to the development of the DT. However, the development of a federated model is highly dependent on the quality and quantity of the data that can be generated. Data are the lifeline for any DT. Considering the nature of this study in which the assessment of the sustainability parameters needs to be done, it is important to identify what kind of databases are required. Usually, there are two types of databases, static and dynamic data.

Static data: Static data represent the information related to the parameters that are fixed and will not change over time or for a longer period. Commonly static data include the characteristics of the material data, physical features like windows, walls, and door information. Furthermore, the metadata in the BIM model can incorporate a lot of information that comes under the static data for the DT. For example, warranty information, material sound absorption value, transmissivity, fire rating, U-value, operation and maintenance schedule, operation manuals, etc. If we further expand the type of static data from a sustainability assessment point of view, then it will be regarding the site information, type of plants on the site, materials HPDs, and EPDs.

Dynamic data: Dynamic data refer to all sorts of data from the building that are not constant and keep changing over time, randomly or periodically. Mainly dynamic data are from the IoT, sensors, and other monitoring devices placed in the buildings. For example, all the data coming from the sensor’s data to monitor the carbon dioxide level in any room, lighting levels monitoring sensors, occupancy sensors, HVAC speed controlling devices data, humidity monitoring data, and energy consumption data at any given time frame. Usually, this dynamic data are processed by simple algorithms or AI for simulations to extrapolate and predict the behavior of certain parameters. The proposed framework for the green DT is shown below. It is a comprehensive framework that defines each layer separately and a bottom-up approach. The framework starts from the basic BIM data or model and relies mostly on the data that is fed to either the BIM model or directly to the server available.

It is highly dependent on the nature of the study or the data collection method that can vary from study to study. Furthermore, sometimes the nature of the parameters under consideration can create problems regarding data interoperability, data recording, security, quality, and quantity of the data. It is a proposed model and has the provision for the nth number of DTs but in a real-case scenario, it depends on the number of credits and parameters associated with those credits are being measured (Figure 36.2).

![](img/0dd4397c67b063014553965e4f1cf7e4_646_0.png)

### FIGURE 36.2 Proposed green digital twin framework.

### 36.4 Case Study

To verify the sustainability assessment through DT, a case study was conducted on the eLUX lab building at the University of Brescia, Italy. There are many parameters related to sustainability. However, for this case study, one parameter from LEED and WELL are tested through DT and then the data is visualized in the virtual reality (VR). The parameters that are measured are related to

- The Material and Resources Category from the LEED V4.1 rating system
- AIR credit category from the WELL V2 building standard.

Recycled content and EPDs belong to the static data category while the CO concentration is a value that is from the dynamic data category. The Revit model for the eLUX lab is used in conjunction with the Enscape VR engine to visualize the result. The complete process is explained in this section.

Our target is the furniture, chairs to be precise, and walls, to measure the two parameters from the material credit category. A Revit family of the chair was generated and placed in the 3D model.

### 36.5 Results

In the next step, an EPD parameter of the Chair Revit element was added and the EPD was linked in the model. The authentic EPD for the chair was selected from the international EPD Portal. In this step, BIM data are linked with the Enscape and turned the models into immersive 3D experiences for the verification of the EPD. For example, the color of the selected chair is yellow and the data confirm that this product is EPD verified.

Similarly, the staircase wall has recycled content and the recycled material is defined as a parameter in the BIM model for that wall. The VR selection of the image confirms the recycled content. The amount of percentage of the recycled material is unknown that’s why it is not showing any value. If we choose the other elements that don’t have EPDs, the data will not show that they are EPD verified.

This is how we conduct the sustainability assessment of the building components by harnessing the potential of the BIM data and then using the VR engine. It is important to remember that the BIM data are the basis of the sustainability assessment. Now moving on to the next scenario in which the same EPD verification is being done but in the BIM environment. Furthermore, by selecting the object in the BIM and using the filter option in BIM schedules, we can see in the following pictures that all the chairs with the EPDs are selected. The purpose of filtering, selecting, or verification within the BIM environment is to highlight the fact that the metadata of the BIM model, objects, or elements is of prime importance. Figure 36.3 shows the EPD metadata of the chair in the BIM model, and then the selection of all chairs that are EPD verified.

From the verification of the material EPD and recycled content, we can say that the establishment of a cyber-physical world connection can help verify the sustainability parameters, hence validating the green DT for the material credit category.

The WELL building standard air category parameter for carbon monoxide concentration was monitored, analyzed, and shown in the BIM model. According to the standard, the concentration of the CO2 must be less than 1,000 PPM in any given space. These data can be monitored in various ways, analyzed, and results can be shown in the model. However, here the results are only shown in the changing colors to show how the color scheme of the spaces will change based on the CO2 concentration levels. In further advanced

| TYPE | QR code | Cost | EPD | Design country | Manufacturer name | Manufacturer country |
|------|---------|------|-----|----------------|-------------------|----------------------|
| One Lounge Chair | https://www.envimode.com/libraryobj36005 | 2145.00 | https://www.envimode.com/libraryobj36005 | Foster + Partners, UK | Benchmark Woodworking Ltd | UK & Europe |
| One Lounge Chair | https://www.envimode.com/libraryobj36006 | 2145.00 | https://www.envimode.com/libraryobj36006 | Foster + Partners, UK | Benchmark Woodworking Ltd | UK & Europe |
| One Lounge Chair | https://www.envimode.com/libraryobj36007 | 2145.00 | https://www.envimode.com/libraryobj36007 | Foster + Partners, UK | Benchmark Woodworking Ltd | UK & Europe |
| One Lounge Chair | https://www.envimode.com/libraryobj36008 | 2145.00 | https://www.envimode.com/libraryobj36008 | Foster + Partners, UK | Benchmark Woodworking Ltd | UK & Europe |
| One Lounge Chair | https://www.envimode.com/libraryobj36009 | 2145.00 | https://www.envimode.com/libraryobj36009 | Foster + Partners, UK | Benchmark Woodworking Ltd | UK & Europe |
| One Lounge Chair | https://www.envimode.com/libraryobj36010 | 2145.00 | https://www.envimode.com/libraryobj36010 | Foster + Partners, UK | Benchmark Woodworking Ltd | UK & Europe |
| One Lounge Chair | https://www.envimode.com/libraryobj36011 | 2145.00 | https://www.envimode.com/libraryobj36011 | Foster + Partners, UK | Benchmark Woodworking Ltd | UK & Europe |
| One Lounge Chair | https://www.envimode.com/libraryobj36012 | 2145.00 | https://www.envimode.com/libraryobj36012 | Foster + Partners, UK | Benchmark Woodworking Ltd | UK & Europe |

![](img/0dd4397c67b063014553965e4f1cf7e4_648_0.png)

### FIGURE 36.3
Selection of the elements with EPDs and recycled content in the cyber-physical world.
