Proceeding Paper

# # COVID-19 Data Analysis and Computation with Urban Structure Consideration †

Ryota Goto ¹ and Ari Aharari ²,*

¹ Department of Applied Information Sciences, Graduate School of Engineering, SOJO University, Kumamoto 860-0082, Japan; g2311m05@m.sojo-u.ac.jp
² Faculty of Computer and Information Sciences, SOJO University, Kumamoto 860-0082, Japan
* Correspondence: info@ahary.org
† Presented at the 2024 IEEE 4th International Conference on Electronic Communications, Internet of Things and Big Data, Taipei, Taiwan, 19–21 April 2024.

**Abstract:** In early 2020, the outbreak of COVID-19 brought a global pandemic, challenging healthcare systems worldwide and prompting countries to implement various measures to contain the spread. These measures, while necessary, led to significant socioeconomic disruptions. One of the most pressing concerns was the strain on healthcare systems, which caused shortages of medical supplies, hospital beds, and healthcare personnel. This raised the prospect of a healthcare system collapse. Using data analysis, we studied how to understand the dynamics of COVID-19 transmission in the context of urban structures, focusing on preventing healthcare system collapse.

**Keywords:** COVID-19; data analysis; machine learning

**Citation:** Goto, R.; Aharari, A. COVID-19 Data Analysis and Computation with Urban Structure Consideration. *Eng. Proc.* 2024, 74, 6. https://doi.org/10.3390/engproc2024074006

Academic Editors: Shu-Han Liao, Teen-Hang Meen and Cheng-Fu Yang

Published: 27 August 2024

![](bbox=[0.134, 0.734, 0.214, 0.754])

© 2024 by the authors. Licensee MDPI, Basel, Switzerland. This article is an open access article distributed under the terms and conditions of the Creative Commons Attribution (CC BY) license (https://creativecommons.org/licenses/by/4.0/).

# ## 1. Introduction

In early 2020, the outbreak of COVID-19 rapidly became a global pandemic, putting immense pressure on healthcare systems worldwide and leading to various containment measures being implemented by nations. While these measures were necessary to control the spread of the virus, they also caused significant disruptions to society. One of the most pressing issues was the strain on healthcare systems, which led to shortages of medical supplies, hospital beds, and healthcare personnel and increased the risk of system collapse. Two research studies have been conducted in this area. The first study, conducted by Sato et al., focused on the impact analysis of COVID-19 on hospital bed availability in Shiga Prefecture, Japan, using a mathematical infectious disease model. The second study was conducted by Hirata et al. to predict the spread and convergence of COVID-19 using deep learning techniques. Both studies analyzed related data and predicted COVID-19 effects without considering urban structures.

Urban areas in Japan are classified into diffuse and intensive urban areas. Diffuse urban areas refer to areas where the development of urban structures disperses from the central region to the surrounding areas. On the other hand, intensive urban areas refer to areas where urban structures develop intensively from the central region. In this study, we focused on Kumamoto Prefecture, Japan, which falls into the intensive urban category [1]. There is a risk of inadequate medical services due to a critical shortage in the medical field and the collapse of the healthcare system. The Japanese healthcare system will likely collapse when the hospital bed occupancy rate exceeds 50%. This rate is chosen based on the welfare index of infection status proposed by the Ministry of Health, Labor, and Welfare of Japan in 2020 [2]. The standard changes annually starting in 2020, and starting in 2022, a bed occupancy rate of 50% or less is considered appropriate.

In this research, we explored how COVID-19 spread within various urban structures and focused on maintaining the resilience of the healthcare system by keeping the bed oc-