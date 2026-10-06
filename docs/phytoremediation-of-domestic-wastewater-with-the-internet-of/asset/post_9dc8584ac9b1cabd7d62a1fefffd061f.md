
# Contents

- 10.2.2 Data Processing and Statistical Analysis ................................................ 130
- 10.2.3 Artificial Neural Network (ANN)............................................................ 131
- 10.2.4 Concept of Support Vector Machine (SVM)................................................ 132
- 10.2.5 Concept of Adaptive Neuro-Fuzzy Inference System (ANFIS) ................................................................................................ 132
- 10.2.6 Multilinear Regression (MLR)................................................................... 134
- 10.3 Model Validation and Performance Evaluation ........................................ 134
- 10.4 Results and Discussion ....................................................................... 134
- 10.4.1 Descriptive Statistical Analysis............................................................... 135
- 10.4.2 Results of ORPt (ANN, SVM, ANFIS and MLR).......................................... 137
- 10.5 Conclusion ................................................................................................ 142
- References ....................................................................................... 142
# Index ............................................................................................ 145

![](img/144ee7fe73d0b07144cc2acec5d1c144_10_0.png)

# About the Authors

Hauwa Mohammed Mustafa is an Academic Lecturer in the Department of Pure and Applied Chemistry, Kaduna State University (KASU), Nigeria. She obtained her Doctorate Degree from Universiti Tenaga Nasional (UNITEN), Malaysia. Her research areas focus on Wastewater Treatment, Bioenergy, IoT, Artificial Intelligence, and Material Science.

Gasim Hayder is a Senior Lecturer and the Head of the Water & Environmental Engineering Unit at the Civil Engineering Department, College of Engineering, Universiti Tenaga Nasional (UNITEN), Malaysia. He is also a Chartered Engineer-MIET (CEng) from the Engineering Council (UK). He received his Ph.D. in Civil Engineering from Universiti Teknologi PETRONAS (UTP), Malaysia. His research focus is in the field of Environmental Engineering and Water and Wastewater Assessment, Treatment, Modelling, and Monitoring.

![](img/144ee7fe73d0b07144cc2acec5d1c144_12_0.png)

# 1 Impacts of Sustainable Development Goals (SDGs) in Wastewater Management

## 1.1 INTRODUCTION

Wastewater can be described as water that has been contaminated by anthropogenic activities. Wastewater is water that has been "used" for various purposes, including commercial, industrial, agricultural activities, domestic, storm water or sewer infiltration. The composition of wastewater varies to the source. Similarly, wastewater is made up of biological, chemical and physical compounds that may have a detrimental effect on the water quality, rendering it unfit for human consumption and hazardous to aquatic life. Anthropogenic activities from agricultural and domestic activities release waste product as ammonia (NH₃), phosphorus (P), nitrate (NO₃) and potassium (K) into water bodies. Consequently, this brings eutrophication in the aquatic environment (Sukač et al., 2015). Thus, complete recovery or removal of nutrients from wastewater should be treated as a fundamental and crucial process before disposal into natural bodies to protect natural waters (Hu et al., 2012).

Furthermore, one of the key components of the 2030 sustainable development goals (SDGs) is to improve water quality. The conventional wastewater treatment methods which involve multiple processes fail in the complete removal of water pollutants. These residues contain certain amount of nutrients (nitrogen, phosphorus and heavy metals) and pathogens that cause the spread of diseases such as typhoid, cholera, and skin irritation and promote the rapid growth of aquatic plants in rivers and lakes (Kutty et al., 2009; Meena et al., 2019). Therefore, the search and exploration of affordable and renewable methods of wastewater treatment such as phytoremediation has become crucial. The applications of aquatic plants (macrophytes) in phytoremediation are not new (Akinbile et al., 2015). Phytoremediation technique uses the plant root system in absorbing excess nutrients from wastewater (Nwachukwu & Osuji, 2007; U et al., 2013). However, the potentials of aquatic plants in phytoremediation processes depend on the characteristics and origin of the wastewater (Ng et al., 2017). The diagram of wastewater is presented in Figure 1.1.

# Phytoremediation of Domestic Wastewater

![](img/144ee7fe73d0b07144cc2acec5d1c144_14_0.png)

FIGURE 1.1 Wastewater.

# 1.2 SOURCES OF WASTEWATER IN OUR ENVIRONMENT

Wastewater is classified as industrial, municipal, agricultural and domestic wastewater. Households generate wastewater from showers, dishwashers, laundry and flush toilets. Figure 1.2 depicts the major types of wastewater (Edokpayayi et al., 2017). Additionally, wastewater can be transported through combined sewer or sanitary sewer. In other words, the phrases “water reclamation” and “wastewater reuse” apply to the treatment of wastewater to make it beneficial within the acceptable water quality standards. In general, water reuse is the application of reclaimed water for useful purpose. Additionally, the word “reclaimed” is frequently interchanged with “recycled water” (Asano et al., 2007).

![](img/144ee7fe73d0b07144cc2acec5d1c144_14_1.png)

FIGURE 1.2 Classification of wastewater.

# Impacts of SDGs in Wastewater Management

## 1.2.1 DOMESTIC WASTEWATER

Wastewater from households has been classified into different colours based on their usage (Shi et al., 2018). Wastewater from kitchen and bathroom usage is classified under grey water. Urine with minimal flushing water is classified as yellow water, grey faecal from the toilet is categorized as black water (De Gisi et al., 2015). Grey water is often described as urban wastewater generated from showers, hand basins and kitchen sinks. Additionally, kitchen grey water contains high BOD, variable thermolerant coliforms and cleaning agents (detergents). In contrast, bathroom grey water has a high concentration of suspended particles, hair and turbidity from cleaning chemicals such as toothpaste, soap and shampoo. Furthermore, it has lower BOD concentrations and thermolerant coliforms loads. According to a previous study, laundry and kitchen grey water contain much more organic and physical contaminants than bathroom grey water. All grey water types have a high degree of biodegradability regard to COD (Metcalf & Eddy, 2003). However, phosphorus and nitrogen are deficient due to absence of faeces and urine in bathroom grey water. Similarly, laundry grey water is also deficient in phosphorus due to the application of phosphorous-free detergent. Powdered laundry detergent is the main source of pollution in grey water. Many of them have a high concentration of salts and phosphorus, and they are alkaline in nature. Long-term application of laundry water in gardens may result in shifting of plants and salt build-up in the soil (De Gisi et al., 2015).

## 1.2.2 INDUSTRIAL WASTEWATER

The word "industrial wastewater" refers to wastewater discharged from various industrial processes (Ahmed et al., 2021). Water is used in industries for different purposes, including manufacturing of goods, heating and cooling of industrial processes, firefighting, dissolving of solvents, and transportation of waste matter and raw materials. Pollutants such as zinc (Zn), chromium (Cr), copper (Cu), lead (Pb), iron (Fe), cadmium (Cd), nickel (Ni), arsenic (As) and mercury (Hg) can be present in industrial wastewater depending on the type of manufacturing or commercial activities carried (Wang & Yang, 2016). Furthermore, industrial wastewater is divided into inorganic and organic wastewater. In general, treating wastewater is tough because it necessitates an individual analysis of the set-ups and the construction of specific treatment plants on an industry-specific basis. For example, organic contaminants are maintained in the secondly treated wastewater even after the primary biological treatment has taken place. Power plants, food/beverage industries, steel/iron production plants, industrial laundries, oil and gas fracking plants, metal-finishing and mining are examples of industries that generate wastewater (Liu et al., 2014).

## 1.2.3 MUNICIPAL WASTEWATER

Municipal wastewater is a mixture of domestic and industrial wastewater (Guldhe et al., 2017). The characteristics of municipal wastewater depend on the source, and it
