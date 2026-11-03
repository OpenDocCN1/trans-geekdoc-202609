
3.  [Wang, H., Yan, G., Tag-Eldin, E., Chaturvedi, R., Aryanfar, Y., Alcaraz, J. L. G., et al.](#ch8.xhtml#R_ref8_3) (2023). Thermodynamic investigation of a single flash geothermal power plant powered by carbon dioxide transcritical recovery cycle. Alexandria Engineering Journal, 64, 441–450.

4.  [Cikanek, S. R., and Bailey, K. E.](#ch8.xhtml#R_ref8_4) (2002). Regenerative braking system for a hybrid electric vehicle. In Proceedings of the 2002 American Control Conference (IEEE Cat. No. CH37301), (Vol. 4, pp. 3129–3134). IEEE, 2002.

5.  [Sun, W., Feng, L., Abed, A. M., Sharma, A., and Arsalanloo, A.](#ch8.xhtml#R_ref8_5) (2022). Thermoeconomic assessment of a renewable hybrid RO/PEM electrolyzer integrated with Kalina cycle and solar dryer unit using response surface methodology (RSM). Energy, 260, 124947.

6.  [Jeon, S., Jo, S., Park, Y., and Lee, J.](#ch8.xhtml#R_ref8_6) (2002). Multi-mode driving control of a parallel hybrid electric vehicle using driving pattern recognition. Journal of Dynamic Systems, Measurement, and Control, 124(1), 141–149.

7.  [Saraswat, M., Sharma, K., Chauhan, N. R., and Shukla, R. K.](#ch8.xhtml#R_ref8_7) (2020). Role of automation in energy management and distribution. Journal of Scientific and Industrial Research, 79(10), 951–954.

8.  [Pisu, P., and Rizzoni, G.](#ch8.xhtml#R_ref8_8) (2005). A supervisory control strategy for series hybrid electric vehicles with two energy storage systems. In 2005 IEEE Vehicle Power and Propulsion Conference, (pp. 8). IEEE, 2005.

9.  [Saraswat, M., Garg, M., Bhardwaj, M., Mehrotra, M., and Singhal, R.](#ch8.xhtml#R_ref8_9) (2019). Impact of variables affecting biogas production from biomass. In IOP Conference Series: Materials Science and Engineering, 691(1), pp. 012043). IOP Publishing.

10.  [Piller, S., Perrin, M., and Jossen, A.](#ch8.xhtml#R_ref8_10) (2001). Methods for state-of-charge determination and their applications. Journal of Power Sources, 96(1), 113–120.

11.  [Gao, J. P., Zhu, G. M. G., Strangas, E. G., and Sun, F. C.](#ch8.xhtml#R_ref8_11) (2009). Equivalent fuel consumption optimal control of a series hybrid electric vehicle. Proceedings of the Institution of Mechanical Engineers, Part D: Journal of Automobile Engineering, 223(8), 1003–1018.

12.  [Sharma, K., Kaushalyayan, K. S., and Shukla, M.](#ch8.xhtml#R_ref8_12) (2015). Pull-out simulations of interfacial properties of amine functionalized multi-walled carbon nanotube epoxy composites. Computational Materials Science, 99, 232–241.

13.  [Hu, J., Chen, Y., and Yang, Z.](#ch8.xhtml#R_ref8_13) (2009). Study and simulation of one bi-directional DC/DC converter in hybrid electric vehicle. In 2009 3rd International Conference on Power Electronics Systems and Applications (PESA), (pp. 1–4). IEEE, 2009.

14.  [Yadav, A., Kumar, A., Singh, P. K., and Sharma, K.](#ch8.xhtml#R_ref8_14) (2018). Glass transition temperature of functionalized graphene epoxy composites using molecular dynamics simulation. Integrated Ferroelectrics, 186(1), 106–114.

15.  [Geller, B. M., and Bradley, T. H.](#ch8.xhtml#R_ref8_15) (2015). Analyzing drive cycles for hybrid electric vehicle simulation and optimization. Journal of mechanical design, 137(4), 041401.

# 9 Li-ion battery and its life cycle assessment for hybrid vehicles

Manish Saraswat^([⁸](#fn8))

DOI: [10.1201/9781003534136-9](https://dx.doi.org/10.1201/9781003534136-9)

## Abstract

The cost, safety, size, and general management of the energy storage systems (ESSs) needed for electric vehicles (EVs) are just a few of the challenges they must overcome. On the basis of the energy storage technique, ESS technologies are discussed in this paper. One of the main takeaways from this review is that while the ESS technologies currently in use can be applied to EVs, their full potential for effective EV energy storage applications has not yet been realized. The thermal effect, a crucial component of the battery’s electrical model, is taken into account in this improved modelling technique to produce a comprehensive understanding and, as a result, the Li-ion battery’s distinctive properties. It is essential to have such an accurate thermal-electrical model because the battery cell or pack in a HEV is extremely sensitive to temperature.

**Keywords:** Battery, challenges, energy storage, hybridization, li-ion, modelling, thermal effect

## Introduction

A significant portion of the population has moved from rural to urban areas as a result of the start of rapid urbanization. In the urbanization of cities, mobility is crucial. The number of vehicles on the road has increased as a result of the growth in urban population. Out of all the sectors, the transport industry consumes the most energy \[[1](#ch9.xhtml#ref9_1), [2](#ch9.xhtml#ref9_2) and [3](#ch9.xhtml#ref9_3)\]. It accounts for nearly 27% of global energy consumption \[[4](#ch9.xhtml#ref9_4), [5](#ch9.xhtml#ref9_5) and [6](#ch9.xhtml#ref9_6)\]. The current vehicle mix, which is primarily composed of vehicles powered by conventional internal combustion (IC) engines, contributes significantly to greenhouse gas (GHG) emissions. In 2012, it contributed to 33.7% of GHG emissions. So, we must employ more cuttingedge technologies in the field of mobility to combat climate change and reduce GHG emissions. Due to their low emissions, electric vehicles (EVs) have gained popularity as a solution. The global automobile industry is under constant pressure to replace conventional IC engine vehicles with electric ones and to reduce the percentage of those vehicles \[[7](#ch9.xhtml#ref9_7), [8](#ch9.xhtml#ref9_8) and [9](#ch9.xhtml#ref9_9)\]. The engine efficiency of an electric vehicle is higher, and there are no tailpipe emissions, fuel evaporation, or fuel refinery pollutants to worry about. An essential feature of electric vehicles is their range. EVs should have enough range to travel there on a single charge. Range anxiety, which is the worry that there won’t be enough range in the car to get there, is a result of this. The deployment of extensive charging infrastructure, the development of higher battery capacity at an affordable price, and battery swapping technology are the main methods for easing range anxiety among electric car drivers \[[10](#ch9.xhtml#ref9_10)\]. To extend the range of electric vehicles and improve their dependability, more sophisticated and advanced energy storage and conversion technologies are required.

## Li-Ion Battery Storage Technology

Energy and power density, state-of-charge window and cycle life, charge discharge rate, operating temperature, calendar life, and safety are just some of the challenging requirements for electrified vehicle energy storage systems (ESS) \[[11](#ch9.xhtml#ref9_11)\]. There are many different permutations of the lithiumion chemistry, and an increasing number of those permutations are finding use in applications that are related to automobiles. One example of this trend is the development of rechargeable lithiumion batteries. The manufacturing of lithium-ion batteries is one example of such an application. The roughly observable stages of progression of these chemical processes have been categorized, and the outcomes of this categorization are summarized in [Table 9.1](#ch9.xhtml#R_tab9_1).

[Table 9.1  Different compositions of Li-ion battery with their performance specifications](#ch9.xhtml#R_tab9_1)

| Chemistry || Maturity || Thermal || Performance |

| --- | --- | --- | --- |

| LiNiCoAlO[2] 4.xV/cell || Proven C/x rates || Unstable at high || High energy, good power |

| --- | --- | --- | --- |

| LiNiCoMnO[2] 4.xV/cell || Improving || Limited durability experience || High energy, good power |

| LiFePO[4] 3.6V/cell || Mature || Very stable || Low energy, Relatively high power |

| LiMn[2]O[4] 3.8V/cell || Improving || Limited life at high temperature || High capacity fade, moderate power |
