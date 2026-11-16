# The Development and Optimization of a Textile Image Processing Algorithm (TIPA) for Defect Detection in Conductive Textiles

Sang-Un Kim ¹ and Joo-Yong Kim ²,*

¹ Department of Smart Wearable Engineering, Soongsil University, Seoul 06978, Republic of Korea; tkddns10723@naver.com
² Department of Materials Science and Engineering, Soongsil University, Seoul 06978, Republic of Korea
* Correspondence: jykim@ssu.ac.kr; Tel.: +82-10-8720-0631

Abstract: This study introduces a Textile Image Processing Algorithm (TIPA) designed to detect defects in conductive textiles, a crucial element of wearable technology. TIPAs employ image preprocessing, filtering, and classification to identify issues like uneven distribution of conductive particles. When applied to fabrics produced via dip-coating, our TIPA was optimized using a threshold ratio, achieving over 85% accuracy, with a maximum of 100% under ideal conditions. However, detection challenges were noted in fabrics with large, diffuse stains, particularly at extreme threshold ratios. This TIPA proves to be a valuable tool for improving quality control in smart textiles, with potential for further optimization.

Keywords: conductive textiles; textile image processing algorithm (TIPA); defect detection; dip-coating process; image filtering; algorithm optimization

# 1. Introduction

Conductive textiles, which have gained attention as soft smart materials [1,2], are fusion materials used in various wearable products due to their ability to measure a range of biometric data [3,4], including heart rate [5], respiration [6,7], movement [6], voice [8], and pulse [9]. The mechanical properties of conductive textiles maintain the physical characteristics of traditional textiles, making them flexible [10], lightweight [11], and stretchable [12]. Conductive particles that are processed in textiles determine their electrical properties [10]. When they mechanically deform under external forces, their electrical properties are changed by changes in the distribution of conductive particles and the structure of the circuits. This property enables the measurement of parameters such as pressure and strain, facilitating the acquisition of diverse biometric information in the wearable technology field.

The manufacturing process of conductive textiles typically involves two main approaches. The first involves treating fibers with conductive particles at the fiber scale to produce the textile, or imparting conductivity by treating a textile with suitable mechanical properties using conductive particles [13]. The second approach, particularly the dip-coating method, which involves using a solution with dispersed conductive particles, is advantageous as it allows for the use of textiles with appropriate physical properties and can be applied in continuous processes such as roll-to-roll manufacturing [3,14]. However, textiles produced through this method may suffer from defects similar to those observed in dyeing processes, where uneven distribution of particles can result in blemishes or streaks (Figure 1).

Academic Editor: Jie Zhang
Received: 14 January 2025
Revised: 5 February 2025
Accepted: 9 February 2025
Published: 10 February 2025

Citation: Kim, S.-U.; Kim, J.-Y. The Development and Optimization of a Textile Image Processing Algorithm (TIPA) for Defect Detection in Conductive Textiles. Processes 2025, 13, 486. https://doi.org/10.3390/pr13020486

Copyright: © 2025 by the authors. Licensee MDPI, Basel, Switzerland. This article is an open access article distributed under the terms and conditions of the Creative Commons Attribution (CC BY) license (https://creativecommons.org/licenses/by/4.0/).