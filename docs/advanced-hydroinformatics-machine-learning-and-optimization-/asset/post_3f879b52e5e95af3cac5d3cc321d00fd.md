
et al., 2020; Mosavi et al., 2018; Muñoz et al., 2021, 2018; Orellana-Alvear et al., 2020; Papacharalamous & Tyralis, 2018). This is due to RF’s simplicity (few parameters to calibrate) and higher accuracy when compared with other ML techniques such as Support Vector Machines and Artificial Neural Networks, model robustness, and capacity to deal with small size samples and complex data structures (Biau & Scornet, 2016; Breiman, 2001; Contreras et al., 2021; B. Li et al., 2016; Liu et al., 2020; Muñoz et al., 2018, 2021; Papacharalamous & Tyralis, 2018; Tyralis et al., 2019; Wang et al., 2015).

In terms of data availability, in many regions, ground precipitation networks are either nonexistent or scarce and if available mostly with extremely low areal density. This is especially true for mountainous regions, such as the tropical Andes, where the remoteness of the study areas and monitoring authorities’ budget constraints limits the development of accurate precipitation-runoff models. Fortunately, continuous development of Remote Sensing (RS) products, for example, space-based satellites have dramatically enhanced the quantity (spatiotemporal resolution) and quality of areal precipitation observations. However, RS precipitation obtained from a single sensor (satellite) hardly provides accurate estimations (Hong et al., 2019). This has stimulated the development of multisatellite precipitation products such as the NASA Global Precipitation Measurement (GPM) Integrated Multi-satellitE Retrievals for GPM (IMERG) (Huffman et al., 2015), and the Precipitation Estimation from Remotely Sensed Information using Artificial Neural Networks (PERSIANN) (Hsu et al., 1997). IMERG and PERSIANN products are characterized by quasi-global coverage, free access, high spatiotemporal resolutions, and continuous development (Tang et al., 2016). Given previous, both RS products are nowadays widely used in hydrometeorological applications including tracking of precipitation anomalies (Nguyen et al., 2014; Sakib et al., 2021), precipitation early warning systems (Sorooshian et al., 2014), and flood forecasting and mapping (Belabid et al., 2019; Nguyen et al., 2015). Of particular concern is the determination of the optimal RS product for a given study area, the necessity to combine two or more RS products, or even fuse RS databases to improve precipitation representation and minimize precipitation uncertainties (Soo et al., 2020; Yin et al., 2021; Yu et al., 2020).

Once the issue of data availability is solved, the arising research questions are (1) is precipitation well represented by RS data? and (2) can the assimilation of RS precipitation be improved (in the context of extreme runoff ML models)? The first research question is mandatory for the cases when the interest lies in providing accurate precipitation estimations. This can be achieved by validating RS products with ground precipitation estimations, see for instance the studies of Laverde-Barajas et al. (2019) and Li

![](img/dd2f1e467aed0a84f984e6e656b2cc0f_168_0.png)

**Figure 6.1** The Jubones basin in the tropical Andes of Ecuador, South America (UTM coordinates).

upstream of the Minas-San Francisco hydroelectric dam, with an elevation ranging between 1,250 and 3,920 m above sea level. The climatology of the basin is extremely variable due to the presence of the Andean mountain range, trade winds, and ocean currents from the Pacific Ocean. A distinction can be made between at least four rainfall regions, including a semi-arid region. The basin climate ranges from humid to arid, with average annual rainfall ranging spatially from 350 to 1,170 mm.

## 6.2.2. Data Set

The data set comprises hourly satellite-derived precipitation covering the Jubones basin, and hourly runoff data collected at the hydrological station, situated in the outlet of the basin. Runoff is measured at the entrance of the Minas-San Francisco hydroelectric dam, and although measurements are prone to dam oscillations uncertainties, they are expected to be absorbed/compensated by the use of the RF algorithm. Moreover, since the dam was completed in 2018, the study period is ~2.5 yr, from 18 November 2018 to 31 March 2021.

### Precipitation From Remote Sensing (RS) Products

Precipitation information was retrieved from two near-real-time multisatellite sources, the IMERG-early run, and the PERSIANN-Cloud Classification System (CCS) precipitation subproducts. Data were derived at hourly intervals. The main difference between both precipitation sources is the spatial resolution. The PERSIANN-CCS possesses the highest spatial resolution for the region (0.04° x 0.04°), being the result of infrared imagery processing and cloud classification using artificial neural networks (Hong et al., 2004). Whereas the IMERG-early run approach interpolates various microwave precipitation estimates and delivers data with a spatial resolution of 0.1° x 0.1°.

Figure 6.2 shows the mean annual precipitation of the Jubones basin, measured by the PERSIANN-CCS (728.5 mm) and IMERG-early run (727.2 mm) precipitation satellite subproducts. For this plot, we used hourly information for 2019 and 2020 (see also the precipitation plot in Fig. 6.3). We found differences of 1.3 and 116 mm between the mean and the maximum annual precipitation obtained from the PERSIANN-CCS and the IMERG-early run subproducts, respectively. This is attributed to the spatial resolution difference and the measurement principle of each satellite subproduct.

### Runoff at the Entrance of the MSF Hydropower Dam

Hourly time series of runoff at the outlet of the Jubones basin were derived from the server of the Corporación Eléctrica del Ecuador (CELEC EP, https://www.celec.gob.ec/), the company that manages the Minas-San Francisco hydroelectric dam. Figure 6.3 depicts the runoff information for the study period. Figure 6.3a shows the hourly time series, whereas Figure 6.3b shows the corresponding probability of exceedance from which 55 nearly independent peak flow events were selected based on peak-over-threshold values (dark dots in Fig. 6.3a). The peak flow

![](img/dd2f1e467aed0a84f984e6e656b2cc0f_170_0.png)

**Figure 6.2** Mean annual precipitation in mm (for 2019 and 2020) measured by the PERSIANN-CCS and the IMERG-early run precipitation satellite subproducts.

events, selection was done using the WETSPRO tool (Willems, 2009). Exceedance probability analysis reveals that for the study period, the runoff magnitudes of 103.5 and 159.4 m³.s⁻¹ are exceeded with probabilities of 10% and 5%, respectively. These probabilities, which correspond to the 90% and 95% quartiles, served to determine extreme hydrological runoff events for the development of the extreme precipitation-runoff models.

## 6.3. Methodology

### 6.3.1. Determination of Nearly Independent Peak Hydrological Events

The extreme hydrological events from the complete runoff time series were derived by applying the following two criteria: (1) extreme hydrological events must exceed the 90% quartile values (98.8 m³.s⁻¹), and (2) such events must be nearly independent. For meeting both criteria of independence, we used the WETSPRO time series tool (Willems, 2009), which splits runoff series in nearly independent peak and low flow events following a peak-over-threshold approach. The WETSPRO has two parameters to be calibrated, the interevent time and peak height. In summary, we selected extreme hydrological events with a definition of independence controlled by the recession time and peak height difference of two consecutive runoff events.

package in Python version 3.7 (van der Walt et al., 2014). The approach consists of the following steps (see also Fig. 6.4):

- 1. Clipping of the precipitation imagery to the Jubones basin (Fig. 6.4a).
- 2. Identification and localization of precipitation objects (latitude, longitude, see Fig. 6.4b). For this we defined a precipitation threshold

![](img/dd2f1e467aed0a84f984e6e656b2cc0f_172_0.png)
![](img/dd2f1e467aed0a84f984e6e656b2cc0f_172_1.png)
![](img/dd2f1e467aed0a84f984e6e656b2cc0f_172_2.png)
![](img/dd2f1e467aed0a84f984e6e656b2cc0f_172_3.png)
![](img/dd2f1e467aed0a84f984e6e656b2cc0f_172_4.png)
![](img/dd2f1e467aed0a84f984e6e656b2cc0f_172_5.png)

Figure 6.4 Precipitation identification with an object-based Connected Component Analysis Illustration of the PERSIANN-CCS 2021-12-25 05:00 UTC image: (a) Jubones basin clipping, (b) precipitation identification in mm from PERSIANN-CCS imagery, (c) initial identification of seven precipitation objects with CCA analysis, and (d) selection of two precipitation objects according to object size filtering and morphological closing.
