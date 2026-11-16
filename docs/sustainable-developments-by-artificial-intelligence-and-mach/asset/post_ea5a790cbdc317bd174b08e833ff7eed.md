
## Optimal allocation of renewable energy sources in electrical distribution systems based on technical and economic indices

Mohamed Zellaguiᵃᵇ, Samir Settoulᶜ, and Heba Ahmed Hassanᵈ

ᵃDepartment of Electrical Engineering, University of Quebec, Montreal, QC, Canada, ᵇDepartment of Electrical Engineering, University of Batna 2, Batna, Algeria, ᶜDepartment of Electrotechnic, Mentouri University of Constantine 1, Constantine, Algeria, ᵈElectrical Power Engineering Department, Cairo University, Giza, Egypt

## 6.1 Introduction

### 6.1.1 Motivation

The rapid development of distributed generators (DGs) in different forms and capacities is transforming the image of classical planning of electrical distribution systems (EDSs). Despite the benefits offered by renewable DG technologies, several economic and technical challenges can result from the inappropriate integration of DG into the existing EDS. As a result, optimizing DG preparation is critical to ensuring that the EDS’s output meets the expected power efficiency, voltage stability, power loss reduction, durability, and profitability (Abdmouleh, Gastli, Ben-Brahim, Haouari, & Al-Emadi, 2017; Ehsan & Yang, 2018).

Decentralized power generation from renewable energy sources (RESs) is a long-term solution that addresses the present environmental threats because of its widespread availability, sustainability, nonpolluting generation, and eco-friendliness. The most widely used renewable DG types are the photovoltaic (PV) and wind turbine (WT) systems, where generation is intermittent.

Because of its universal affordability, reliability, nonpolluting generation, and eco-friendliness, decentralized power generation from RESs is a long-term approach that addresses current environmental challenges. PV and WT systems, which generate intermittently, are the most commonly used renewable DG forms. DGs are a secure and cost-effective way to deliver power to consumers, and they are usually wired either to the distribution network or on the customer's premises. As a result, it is critical to plan and distribute DGs optimally, in terms of scale, placement, and form, in order to achieve the expected economic, technological, environmental, and regulatory benefits of power systems (Zubo et al., 2017).

### 6.1.2 Literature review

There are numerous techniques and algorithms to address the optimal DG planning problem. In 2017, determination of optimal location of DG using analytical methods (AMs) was used for the minimization of active power loss (APL), cost of energy losses, and annual investment cost of DG units with a new voltage stability index (VSI) (Kazmi & Shin, 2017). These methods include the particle swarm optimization (PSO) algorithm for various techno-economic and environmental indices (Tanwar & Khatod, 2017), PSO for the maximization of profit and initial investments for distribution companies (Kansal, Tyagi, & Kumar, 2017), symbiotic organism search (SOS) algorithm to minimize APL (Nguyen-Phuoc, Vo-Ngoc, & Tran-The, 2017), flower pollination algorithm (FPA) approach in order to minimize APL and improve the bus voltage (Oda, Abdelsalam, Abdel-Wahab, & El-Saadawi, 2017), krill herd algorithm (KHA) in order to minimize line losses (Chithra Devi, Lakshminarasimman, & Balamurugan, 2017), ant lion optimization algorithm (ALOA) to reduce APL and improve voltage deviation (VD) and VSI (Ali, Elazim, & Abdelaziz, 2017), and the applied gray wolf optimizer (GWO) algorithm for the minimization of active and reactive energy indexes (Sultana, Khairuddin, Mokhtar, Qazi, & Sultana, 2017).

In 2018, a new and effective stochastic fractal search algorithm (SFSA) was applied based on three objectives involving APL, VD, and VSI (Nguyen & Ngoc Vo, 2018). Ant lion optimization algorithm (ALOA) was proposed for reduction of APL and VD (Hadidian-Moghaddam, Arabi-Nowdeh, Bigdeli, & Azizian, 2018), and ALOA for reducing APL and consequently maximizing the net saving (Ali, Elazim, & Abdelaziz, 2018). A new AM was applied for the optimization of DG-based wind farms (WFs) considering the voltage stability of the system and minimizing the cost components of WFs (Nikkhah & Rabiee, 2018), grasshopper optimizer algorithm (GOA) to minimize the energy VSI (Sultana et al., 2018), population-based incremental learning (PBIL) algorithm to reduce APL and VD (Grisales-Noreña, Montoya, & Ramos-Paja, 2018), differential learning with biogeography-based optimization (DLBBO) algorithm to minimize the APL (Ravindran & Victoire, 2018), dragonfly algorithm (DA) approach to reduce the APL-based loss sensitivity factors (LSF) (Suresh & Belwin, 2018), a comprehensive teaching-learning-based optimization (CTLBO) technique to minimize APL and maximize VSI (Quadri, Bhowmick, & Joshi, 2018), human opinion dynamics (HOD) technique to minimize APL and VD (Mahajan & Vadherva, 2018), and moth-flame optimization (MFO) algorithm to minimize APL (Tolba, Diab, Tulsky, & Abdelaziz, 2018).

In 2019, the chaotic differential evolution (CDE) technique was applied for minimizing various objectives including yearly economic loss, maintenance cost, and APL (Kumar, Mandal, & Chakraborty, 2019a). Opposition-based tuned-chaotic differential evolution (OTCDE) technique was applied considering cost index, voltage deviation index, and line flow capacity index (Kumar, Mandal, & Chakraborty, 2019b), and elephant herding optimization (EHO) algorithm for the reduction of APL and reactive power loss (QPL) for all the buses (Prasad, Subbaramaiah, & Sujatha, 2019). A discrete-continuous hyper-spherical search (DC-HSS) algorithm was applied to minimize APL in EDS with allocated soft open points and DG (Diaeldin, Abdel Aleem, El-Rafei, Abdelaziz, & Zobaa, 2019), spider monkey optimization (SMO) algorithm to minimize voltage deviation (Deb, Chakraborty, & Deb, 2019), heuristic moment matching (HMM) technique applied for a multiobjective index for minimizing APL and VD (Ehsan, Cheng, & Yang, 2019), moth-flame optimization (MFO) algorithm to reduce the APL and augmented VSI in practical Algerian EDS (Settoul, Zellagui, Abdelaziz, & Chenni, 2019), and MFO algorithm to minimize the ALP (Settoul, Chenni, Hassan, Zellagui, & Kraimia, 2019). Biogeography-based optimization (BBO) algorithm was applied to reduce APL while maintaining voltage harmonic distortion at the limits (Duong, Pham, Nguyen, Doan, & Tran, 2019), unified particle swarm optimization (UPSO) to minimize the APL (Gkaidatzis et al., 2019), and hybrid PSO algorithm considering APL minimization as an objective (Yaprakdal, Baysal, & Anvari-Moghaddam, 2019).

Recently, in 2020, improved Harris Hawks optimization (HHO) algorithm was used with the aim of minimizing the APL, reducing VD, and increasing the VSI (Selim, Kamel, Alghamdi, & Jurado, 2020), improved estimation of distribution algorithm (IEDA) to minimize the APL (Yang, Yang, Wu, & Liu, 2018), modified moth-flame optimization (MMFO) algorithm to minimize the total operating cost, APL, VD, and pollution emission (Elattar & Elsayed, 2020), backtracking search optimization (BTSO) algorithm for minimizing the active and reactive power flows in the lines and maximized microgrid success indicator (Osama, Zobaa, & Abdelaziz, 2020), craziness-based PSO (CRPSO) algorithm based on the game-theoretic strategy to minimize the cost of buying power, and APL (Karimizadeh, Soleymani, & Faghihi, 2020), coyote optimization algorithm (COA) with considerations include the APL and voltage regulator tap changes at different load levels (Chang & Chinh, 2020), and applied spring search algorithm (SSA) to minimize the emissions, VD, APL, and energy cost (Dehghani, Montazeri, & Malik, 2020).

### 6.1.3 Contribution and chapter organization

This chapter presents a new approach to optimal integration of RES-based DG in electrical power systems using the modified WOA approach called cosine adapted WOA algorithm (CAWOA) for techno-economic profits. The salient contributions and findings of this study can be summarized as follows:

- Optimal integration of various DG-based RES: solar photovoltaic PV-DG and wind WT-DG using CAWOA techniques.
- The CAWOA approach is applied to the standard IEEE 33-, 69-, and 118-bus EDS.
- The optimal integration has been selected to minimize various technical and economic indexes: the total APL, TVV, and TOC for test systems.
- The validity of the proposed algorithm is demonstrated by comparing with existing optimization techniques.
- The chapter studies the impact of different types of DGs on active and reactive branch currents in the distribution lines.
- It studies the impact of voltages profile and power losses under different loadability that varied between 60% and 120% to reflect load uncertainty.

This chapter contains five sections along with references list, and is organized as follows: Section 6.2 presents the mathematical problem formulation; Section 6.3 introduces the CAWOA algorithm applied; Section 6.4 provides the simulation results, discussions, and comparisons of the result; and Section 6.5 presents the conclusions.

## 6.2 Problem formulation

### 6.2.1 Multiobjective function

In this chapter, the authors proposed a multiobjective function (MOF) for the EDS and represented by the following equations:

$$MOF = \min \sum_{i=1}^{Nbus} \sum_{j=2}^{Nbus} \alpha_1 \cdot \Delta APL_{ij} + \alpha_2 \cdot \Delta TVV_i + \alpha_3 \cdot \Delta TOC_{ij}$$ (6.1)

$$\sum_{m=1}^{3} \alpha_m = |\alpha_1| + |\alpha_2| + |\alpha_3| = 1$$ (6.2)

In this chapter, $\alpha_1$ is taken as 0.5, while $\alpha_2$ and $\alpha_3$ are taken as 0.25, based on the practical, technical, and economic indicators. The three indices are presented by:

$$\Delta APL = \frac{P_{Loss}^{After DG}}{P_{Loss}^{Before DG}}$$ (6.3)

and:

$$P_{Loss} = \sum_{i=1}^{Nbus} \sum_{j=2}^{Nbus} R_{ij} \frac{(P_{ij}^2 + Q_{ij}^2)}{V_i^2}$$ (6.4)
