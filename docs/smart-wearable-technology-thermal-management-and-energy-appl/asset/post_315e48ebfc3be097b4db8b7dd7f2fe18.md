

### (2) Multinode model

The multinode body heat model is an extended and more complex version of the two-node model, as shown in Figure 14 [115]. Various models have been proposed to predict the state of heat regulation in the human body. Perhaps the most influential is the 25-node model proposed by Stolwijk [116], consisting of 24 body “nodes” (six body segments with four compartments each) and a central blood “node”. Each node has a certain amount of metabolic heat generation, convective heat exchange with the central blood chamber, and convective heat exchange with neighboring nodes. Subsequently, some scholars have also improved this human thermal regulation model to make it suitable for application in a wider range of scenarios, such as cold environments, space environments, and so on. Researchers have made various enhancements to the model to accurately forecast the patterns of local responses in different parts of the human body. Munir et al. [117] reassessed the dynamic characteristics of the Stolwijk model and examined several modifications to the model.

![](img/c1925febd7dde400183c23c14d668ef0_29_0.png)

Figure 14. Comparison of the model segmentation, and the two-node and multinode models [115].

Multinode models use partial differential equations to describe the heat transfer problem in the human body. The differential equations are usually discretized using the finite difference method, finite volume method, or finite element method to obtain the linear algebraic equations at each node. The advantage of the multinode model is that it can be divided into sections and nodes as needed, has better flexibility and accuracy, and can be applied to dynamic, nonstationary environments. The disadvantage is that the accuracy is not as good as the multinode model in environments with large temperature gradient changes. The characteristics of the specific model can be seen in Table 8.

Table 8. The characteristic of the specific models [114,118].

| Model Name | Model Classification | Model Characteristics |
| :--- | :--- | :--- |
| Human thermoregulation model | Two-node model Multinode model | When there are large temperature differences in the human body, more accurate simulation results can be obtained by using multinode and multiunit models. |
| Heat and moisture transfer modeling of clothing | Steady-state model Transient model | Simulate the heat and moisture transfer process of garments to derive the heat and moisture properties of garments. |
| Human body-clothing-environment system model | - | The human body-clothing environment as a whole combines a model of human thermoregulation and a model of heat and moisture transfer from clothing. |

### 5.3.2. Evaluation of Thermal and Moisture Management Performance

There is no generalized performance evaluation method that can be used to assess the performance of wearable systems in managing thermal and moisture. The performance assessment of wearable systems involves two main aspects: (i) wearer comfort and safety; (ii) functionality of the wearable system. Ismail et al. [119] investigated the effect of uniform crosswinds on ventilation, heat, and moisture transfer to a clothed human body by simplifying the human body as a vertical cylinder with a uniform annular air layer. However, the existing evaluation methods are not sufficiently developed, especially for the performance evaluation of wearable systems under specific hot and humid conditions. Due to the wide variety of wearable systems and the different functions and technologies involved, specific assessment methods need to be developed for different types of wearable systems. These evaluation methods should be able to comprehensively consider the impact of thermal and moisture on the comfort and safety of wearable systems and accurately assess the performance of thermal and moisture regulation and energy conversion. Existing standard evaluation methods for thermal and moisture management of wearable systems are shown in Table 9 [75].

Table 9. Existing standard evaluation methods for thermal and moisture management of wearable systems.

| Thermal/Moisture Transfer | Thermal/Moisture Transfer | Indexes | Test Equipment |
| :--- | :--- | :--- | :--- |
| Human body → environment | Heat transfer | Thermal resistance | Hot plate; thermal torso; thermal manikin |
| | Moisture transfer | Liquid-water transfer indexes | Moisture management tester |
| | Coupled heat and moisture transfer | Evaporative resistance | Sweating hot plate; sweating torso; sweating thermal manikin |
| Environment → human body | Heat transfer | Water vapor transmission | Test dish, balance |
| | | Absorbed thermal energy | Thermal protective performance tester; radiant protective tester; radiant protective performance tester |

From the perspective of thermal and moisture management, the performance evaluation of wearable systems can include the following aspects: (i) wearable comfort and safety under specific thermal and moisture conditions, taking into account the thermal and moisture regulation performance as well as the thermal and moisture conditions of the human body and the environment; (ii) wearable functionality under specific thermal and moisture conditions, including thermal and moisture energy conversion and physiological sensing. In order to evaluate the performance of wearable systems under such hot and humid conditions, there is a need to provide standardized and repeatable evaluation methods to support the development of wearable systems.

Our research group is currently developing a cooling and dehumidifying garment that uses membrane separation to reduce skin temperature and absorb surface sweat, thereby creating a cool and comfortable microenvironment within the garment. Therefore, future research should further explore technologies that simultaneously regulate temperature and humidity to improve thermal and moisture comfort for the human body and provide better protection.

## 6. Conclusions

The presented analysis provided a comprehensive overview of wearable systems for personal thermal and moisture management, discussing their functions, latest developments, and performance evaluation approaches. The findings contribute to the understanding of the challenges and considerations involved in regulating temperature and humidity within wearable systems. In the light of this study, the main findings derived can be stated as follows:

- (1) Although current cooling methods are effective in regulating the surrounding temperature, condensation can result if the temperature of the cooling medium is below the dew point of the air.

- (2) Moisture removal from textiles is strongly influenced by the humidity of the surrounding environment. In addition, when a desiccant is used to absorb water vapor from around the body, the desiccant absorbs the water vapor, releasing latent heat and leading to an increase in body temperature.

- (3) Temperature and humidity regulation is a complex coupled process, and there are no generalized performance evaluation methods available to assess the performance of wearable systems in managing temperature and moisture.

- (4) Addressing the issues involved requires considering a combination of cooling and dehumidification factors, such as the use of intelligent control systems, which play a vital role in maintaining the delicate balance between effective dehumidification performance and optimal comfort.

Funding: The research work presented in this article was financially supported by the Postgraduate Research & Practice Innovation Program of Jiangsu Province (No. SJCX23_0493).

Data Availability Statement: Further inquiries can be directed to the corresponding authors.

Conflicts of Interest: The authors declare no conflict of interest.

## References

- 1. Song, G.; Wang, F. Firefighters’ Clothing and Equipment: Performance, Protection, and Comfort; CRC Press: Boca Raton, FL, USA, 2019; pp. 217–268.

- 2. Kjellstrom, T.; Kovats, R.S.; Lloyd, S.J.; Holt, T.; Tol, R.S.J. The Direct Impact of Climate Change on Regional Labor Productivity. Arch. Environ. Occup. Health 2009, 64, 217–227. [CrossRef] [PubMed]

- 3. Wang, H.; Xu, Z.; Ge, B.; Li, J. Experimental Study on a Phase Change Cooling Garment to Improve Thermal Comfort of Factory Workers. Build. Environ. 2023, 227, 109819. [CrossRef]

- 4. Wu, G.; Liu, H.; Wu, S.; Liu, Z.; Mi, L.; Gao, L. A Study on the Capacity of a Ventilation Cooling Vest with Pressurized Air in Hot and Humid Environments. Int. J. Ind. Ergon. 2021, 83, 103106. [CrossRef]

- 5. Peng, Y.; Cui, Y. Advanced Textiles for Personal Thermal Management and Energy. Joule 2020, 4, 724–742. [CrossRef]

- 6. Sajjad, U.; Hamid, K.; Tauseef-ur-Rehman; Sultan, M.; Abbas, N.; Ali, H.M.; Imran, M.; Muneeshwaran, M.; Chang, J.-Y.; Wang, C.C. Personal Thermal Management—A Review on Strategies, Progress, and Prospects. Int. Commun. Heat Mass Transf. 2022, 130, 105739. [CrossRef]

- 7. Su, Y.; Tian, M.; Li, J.; Zhang, X.; Zhao, P. Numerical Study of Heat and Moisture Transfer in Thermal Protective Clothing against a Coupled Thermal Hazardous Environment. Int. J. Heat Mass Transf. 2022, 194, 122989. [CrossRef]

- 8. Hu, B.; Shi, X.-L.; Zou, J.; Chen, Z.-G. Thermoelectrics for Medical Applications: Progress, Challenges, and Perspectives. Chem. Eng. J. 2022, 437, 135268. [CrossRef]

- 9. Zhang, Q.; Wang, S.; Wang, X.; Jiang, Y.; Li, J.; Xu, W.; Zhu, B.; Zhu, J. Recent Progress in Daytime Radiative Cooling: Advanced Material Designs and Applications. Small Methods 2022, 6, 2101379. [CrossRef]

- 10. Wu, Q.; Liu, J.; Zhang, L.; Zhang, J.; Jiang, L. Effect of Temperature and Clothing Thermal Resistance on Human Sweat at Low Activity Levels. Build. Environ. 2020, 183, 107117. [CrossRef]

- 11. Yang, J.; Wang, F.; Song, G.; Li, R.; Raj, U. Effects of clothing size and air ventilation rate on cooling performance of air ventilation clothing in a warm condition. Int. J. Occup. Saf. Ergon. 2022, 28, 354–363. [CrossRef]

- 12. Kim, H.A. Moisture Vapor Permeability and Thermal Wear Comfort of Ecofriendly Fiber-Embedded Woven Fabrics for High-Performance Clothing. Materials 2021, 14, 6205. [CrossRef] [PubMed]

- 13. Gao, H.; Deaton, A.S.; Fang, X.; Watson, K.; DenHartog, E.A.; Barker, R. Effects of Environmental Temperature and Humidity on Evaporative Heat Loss through Firefighter Suit Materials Made with Semi-Permeable and Microporous Moisture Barriers. Text. Res. J. 2022, 92, 219–231. [CrossRef]

- 14. Wang, F.; Pang, D.; Liu, X.; Liu, M.; Du, W.; Zhang, Y.; Cheng, X. Progress in Application of Phase-Change Materials to Cooling Clothing. J. Energy Storage 2023, 60, 106606. [CrossRef]

- 15. Ke, Y.; Wang, F.; Xu, P.; Yang, B. On the Use of a Novel Nanoporous Polyethylene (nanoPE) Passive Cooling Material for Personal Thermal Comfort Management under Uniform Indoor Environments. Build. Environ. 2018, 145, 85–95. [CrossRef]

- 16. Liu, B.; Wang, H.; Lin, H.; Su, Y.; Wei, G.; Xu, Z. Effect of Phase Change Cooling Vest on Related Thermal Regulation Factors in Moderately Hot Environments. Build. Environ. 2023, 242, 110566. [CrossRef]

- 17. Zhang, M.; Li, Z.; Wang, Q.; Xu, Y.; Hu, P.; Zhang, X. Performance investigation of a portable liquid cooling garment using thermoelectric cooling. Appl. Therm. Eng. 2022, 214, 118830. [CrossRef]

