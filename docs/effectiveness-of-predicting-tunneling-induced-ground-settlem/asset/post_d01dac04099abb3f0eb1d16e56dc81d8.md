
inspection technique and especially useful for nonlinear or opaque estimators. The permutation feature importance is defined as the decrease in a model score when a single feature value is randomly shuffled (Breiman, 2001), indicating how much the model depends on the feature. Thus, important features will be filtered, selected, and set as network inputs to decrease architecture complexity.

## 3. Description of the study site and collected dataset

### 3.1. Geological conditions

Data used in this study are collected from the Yuji tunnel project constructed in China, which is excavated by a slurry shield TBM. Many boreholes have been drilled to obtain information about the geological condition below the surface. The soil profile of the tunnel horizon is plotted in Fig. 2 based on the Unified Soil Classification System (USCS). The tunnel section with a total length of 1.1 km is investigated. The ground condition encountered by the shield tunnel includes silty sands, silty clays, silts, sands, and artificial fills. The complexity of geological conditions varies. In general, the tunnel is constructed in a mixed silty clay-sand layer. Most areas were found with sands in the crown and silty clays in the invert. Some parts are entirely excavated in sand or silty clay layer. Ten surface settlement markers or settlement arrays are installed along the selected tunnel section (>1 km) to measure surface settlements during excavation. Vertical ground surface displacement is monitored by precise leveling of transverse profiles. Each profile consists of at least 13 monitoring points. A dataset of 187 observed maximum surface displacements is recorded, collected, and used in this study.

### 3.2. Collected dataset for model construction

The ground surface displacements could result from multiple influencing variables fed into ML models as inputs. Based upon case history reviews of urban shield tunnels (Clough and Leca, 1993; Suwansawat and Einstein, 2006; Zhang et al., 2020b) and extensive observations in this tunnel project, the influencing variables can be grouped into three major categories: tunnel geometry, geological conditions and TBM operational parameters. Such classification proposed by Suwansawat and Einstein (2006) is widely accepted by researchers (Ding et al., 2013; Ocak et al., 2013; Wang et al., 2013; Zhou et al., 2017; Chen et al., 2019). Parameters included in every category are mainly derived from measurements before tunneling or observations along with tunnel excavation. Mahmoodzadeh et al. (2020) also mentioned that urban tunneling projects do not always have access to a vast number of parameters, therefore, it is preferable to consider parameters that can be easily achieved.

#### 3.2.1. Input variables

#### (1) Tunnel geometry

Tunnel depth and diameter are considered in the modeling. The tunnel depth of the selected section varies from around 31 m–36 m. The tunnel project has a constant diameter of 12.4 m. A baseline feature selection approach in ML techniques is to remove features with low variance. Zero-variance features, i.e. features that have the same value in all samples, will not affect the changes of output. Thus, the tunnel diameter is not used as an input.

Additionally, the horizontal distance between tunnel face and monitoring points (DTM) is also considered a parameter that might influence the monitored ground settlements, which indicates various excavation stages from before shield approaching till after shielding pass.

#### (2) Geological conditions

Geological conditions considered in ML models include soil types at tunnel invert and crown, groundwater level, and weighted average soil compressible modulus (ACM). All these parameters related to geological conditions are obtained from many drilled boreholes along the tunnel centerline.

Intuitively by the geological profile shown in Fig. 3, there are two geological conditions of tunnel crown and invert, i.e. silty clays or sands. Binary code symbolized by 0 and 1 typically represents two states, “off” and “on”, respectively. Thus, the binary code can be adopted to indicate if a certain soil type is encountered or not (Suwansawat and Einstein, 2006). In this study area, four geological conditions are summarized, as listed in Table 2.

Although geological complexity can be roughly determined intuitively by the geological profile, quantitative characteristics of soil consolidation are unknown, which may serve as a vital factor affecting the ground settlements. From the soil mechanics perspective, since the soil is a compressible material, the ground surface experiences downward settlements. Five hundred and seventy-six soil samples have been collected from 75 drilled boreholes along the tunnel alignment. These collected soil samples have been used to conduct laboratory soil consolidation tests to study compression properties.

![](img/3dd1490767e1ddfc7ef0e1a1ad6f2726_4_0.png)

Fig. 2. The geological profile of the study area.

![](img/3dd1490767e1ddfc7ef0e1a1ad6f2726_5_0.png)

**Fig. 3.** Distribution of weighted average compressible modulus (ACM).

Plots of soil void ratio *e* vs. effective pressure *p* can be drawn according to results of laboratory compression test. Based on the *e-p* curve, the coefficient of compressibility (*a_v*) expressed as Eq. (11) can be calculated, representing the change of void ratio concerning the applied effective pressure during compression.

Given the initial void ratio of the consolidation layer (*e_0*), the coefficient of volume compressibility (*m_v*) is obtained according to Eq. (12). The parameter *m_v* represents the compression of soil per unit due to a unit increase of pressure. The modulus of soil compressibility (*E_s*) expressed in Eq. (13) is eventually selected as the parameter to represent the soil compressibility. Results of the calculated modulus of compressibility are plotted in Fig. 3. The ACM along drilled borehole can be calculated to represent the overall soil compressibility for every monitoring point using Eq. (14), where *E_si* is the modulus of soil compressibility of the ith soil layer, and *h_i* represents the height of the ith soil layer.

```
a_v = -\Delta e / \Delta p  (11)
m_v = a_v / (1 + e_0)  (12)
E_s = 1 / m_v  (13)
ACM = \sum E_s_i h_i / \sum h_i  (14)
```

#### (3) TBM operational parameters

In soft ground with high water content, the slurry shield TBM is suitable. This TBM is equipped with a slurry system that controls the pressure in the excavation face by injecting pressurized slurry into the cutter chamber. Given a TBM, its specifications depend on and reflect soil conditions. The criterion of selecting TBM-related parameters is that parameters directly affect face stability, ground volume loss, etc. and further affect ground settlement (Mony et al., 2016; Chen et al., 2019; Zhang et al., 2020c). Additionally, real-time collection in the shield system is suggested to ensure the accuracy of these parameters. Based on the TBM parameters related to ground settlements suggested by Zhang et al. (2020b), eight features are selected, including rotational speed of cutterhead, penetrating rate, thrust force, torque, roller displacement, grouting pressure, grouting injection rate, and discharge flow rate. Controlling these parameters well may effectively reduce the surface settlement caused by shield construction.

**Table 2**
Geological conditions of tunnel crown and invert represented by binary code.

| Type | Geology at tunnel crown |  | Geology at tunnel invert |  |
|------|--------------------------|---|--------------------------|---|
|  | Silty clay | Sand | Silty clay | Sand |
| 1 | 1 | 0 | 1 | 0 |
| 2 | 1 | 0 | 0 | 1 |
| 3 | 0 | 1 | 1 | 0 |
| 4 | 0 | 1 | 0 | 1 |

TBM parameters, such as cutterhead rotational speed and penetrating rate, significantly influence TBM vibration. The thrust force of soft ground TBMs is controlled by earth pressure. Torque factor times the cube of tunnel diameter describes the torque of soft ground TBMs. TBM torque is governed by the friction between shield cutters and the ground or by the shear strength. This friction is caused by a few factors, such as earth pressure, chamber pressure acting on a bulkhead, driving force generated by direction changes in curved alignments, frictional force acting between the segments and tail seals, and hauling force of trailing units (Ates et al., 2014). In slurry shield TBM operations, the slurry circuit is a pipeline loop that connects the TBM to the slurry treatment plant (STP) at the surface. Pumps in the slurry discharge pipeline transport the loaded slurry to the STP. In the slurry feed line and discharge line, sensors are installed to determine the flow rate and density. Densities of slurry injection flow and discharge flow are almost constant. Thus, three parameters are selected to represent the slurry circuit condition: grouting pressure, grouting injection rate, and discharge flow rate.

#### 3.2.2. Output variables

Ground settlement induced by tunneling excavations is set as the output variable in ML models, which is influenced by multiple input factors. Given that data are collected during the excavation process, ground settlements within eight times of the tunnel diameter at the excavation face are considered, with a measurement accuracy of 0.3 mm/km.
