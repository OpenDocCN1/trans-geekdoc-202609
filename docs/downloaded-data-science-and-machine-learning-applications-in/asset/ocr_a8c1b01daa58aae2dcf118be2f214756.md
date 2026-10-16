# 3. Data Collection and Description

This research aims to improve the prediction of drilling fluid loss using data from the onshore Marun oilfield during drilling operations. Fracturing in the reservoir interval is a defining feature of this field in Iran’s Khuzestan province. The data consists of 2,820 data points with 19 features compiled from resources such as final well reports, daily drilling reports (DDRs), literature, and daily mud reports (Sabah et al., 2021; Toreifi et al., 2014). However, after removing the missing data, 2783 points remained. Table 2.2 shows the descriptive statistics of some selected features. The main input features for this research are;

+   1. Drilling operation features: Geographic coordinates, depth where the loss occurred, weight on bit (WOB), hole size, drilling time, penetration rate (RPM), mud-pump pressure, the flow rate of the mud pump, Marsh funnel viscosity (MFVIS), and bit rotational speed.
+   2. Characteristics of drilling mud: Viscosity, shear stresses at shear rates of 600/300 rpm, Gel strength (10-s and 10-min), retort solid per cent, and mud weight (MW).
+   3. Formation characteristics: Formation type, pore pressure, and fracture pressure.

One of the main advantages of applying data analytics and machine learning to data is to find patterns and hidden information in high-dimensional data. As such, some input variables will be deemed irrelevant in predicting drilling fluid lost circulation. For this study, the lithologies were encoded into numeric variables ranging from 1–15 (Table 2.3). The coordinates for each well were also removed.

# 4. Methodology

# 4.1 Data Analysis and Visualisation

Data analysis and visualisation were used to aid in understanding how the input features related to the output. The degree of correlation among each input variable pair and output was quantified using the Spearman rho covariance matrix. From the heatmap, the pump pressure was the only feature to show a moderate correlation to the target. The pair plot also depicted the nonlinear distribution between some of the input and the target. Based on the nonlinear distribution depicted in Fig. 2.1, it is evident that none of the features showed a linear correlation to the target. Hence, nonlinear models were deemed appropriate for this research.