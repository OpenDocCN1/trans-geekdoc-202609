
41. Kohavi, R.; John, G.H. Wrappers for feature subset selection. *Artif. Intell.* **1997**, *97*, 273–324. [CrossRef]

42. Muller, M.P.; Tomlinson, G.; Marrie, T.J.; Tang, P.; McGeer, A.; Low, D.E.; Detsk, A.S.; Gold, W.L. Can Routine Laboratory Tests Discriminate between Severe Acute Respiratory Syndrome and Other Causes of Community-Acquired Pneumonia? *Clin. Infect. Dis.* **2005**, *40*, 1079–1086. [CrossRef]

![](img/601340ca744b738277eef45ff127492a_156_0.png)

© 2019 by the authors. Licensee MDPI, Basel, Switzerland. This article is an open access article distributed under the terms and conditions of the Creative Commons Attribution (CC BY) license (http://creativecommons.org/licenses/by/4.0/).

# Wearables and the Quantified Self: Systematic Benchmark of Physiological Sensors

Günther Sagl 1*, Bernd Resch 1,2*, Andreas Petutschnig 1, Kalliopi Kyriakou 1, Michael Liedberger 3 and Frank H. Wilhelm 3

+ 1 Department of Geophysics–Z, University of Salzburg, 5020 Salzburg, Austria;
Andreas.Petutschnig@sbg.at (AP); Kalliopi Kyriakou@sbg.at (K.K)
2 Center for Geographic Analysis, Harvard University, Cambridge, MA 02138, USA
3 Department of Psychology, University of Salzburg, 5020 Salzburg, Austria;
Michael.Liedberger@sbg.at (M.L); Frank.Wilhelm@sbg.at (F.H.W)
* Correspondence: guunter@gmail.com (G.S); Bernd.Resch@sbg.at (B.R.)

Received: 22 August 2019; Accepted: 10 October 2019; Published: 14 October 2019

**Abstract:** Wearable sensors are increasingly used in research, as as for personal and private purposes. A variety of scientific studies are based on physiological measurements from such as low-cost wearables. The question is to, how are such measurements compared to well-calibrated, high-quality laboratory equipment used in psychological and medical research? This undoubtedly impacts the reliability of a study’s results. In this paper, we demonstrate an approach to quantify the accuracy of low-cost wearables in comparison to high-quality laboratory sensors. We then developed a benchmark framework for physiological sensors that covers the entire workflow from sensor data acquisition to computation and interpretation of correlation and similarity metrics. We evaluated this framework based on two wearables with 18 participants. Each participant was equipped with one high-quality laboratory sensor and two sensors simultaneously measured the physiological parameters such as heart rate and galvanic skin response, while the participant was using an ergometer following a predefined routine. The results of our benchmarking show that cardiovascular parameters (heart rate, inter-beat interval, heart rate variability) yield very high correlations and similarities. Measurement of galvanic skin response, which is more undertaking, but still reasonable correlations and similarities. We conclude that the benchmarked wearables provide physiological measurements such as heart rate and inter-beat interval with an accuracy close to that of the professional high-end sensor, but the accuracy varies more for other parameters, such as galvanic skin response.

**Keywords:** wearable sensors; psychophysiology; sensor data analysis; time series analysis; signal analysis; similarity measures; quantitative analysis; benchmarking

In the last decade, the body of literature about physiological sensing and deriving from physiological parameters has grown significantly. One reason for this rapid increase in variety of affordable wearable sensors that measure a broad range of physiological parameters such as heart rate, galvanic skin response, skin temperature, and others. With this increase, the “Quantified Self” community promotes the data of 24/7 tracking and monitoring has been growing significantly [1–3].

These new-cost wearables are increasingly used in scientific studies in a variety of areas like health research, well-being assessment, disaster management, emotion information extraction and spatial emotion analysis [4–13]. However, some efforts have used wearable physiological sensors without prior investigation of the sensor’s exact quality parameters, i.e., how accurately a sensor measures a given parameter or how reliable a sensor is.

In the context of this research, we aim to investigate the quality of low-cost wearables compared to high-quality laboratory sensors. We are interested in the similarity and correlation between two sensor devices, Zephyr Biolarness and Empatica E4. Our study assesses the parameters heart rate (HR), inter-beat interval (IBI), and galvanic skin response (GSR). The remaining part of the paper is structured as follows: In Section 2, we provide a concise summary of related work, followed by an overview of the physiological parameters and the sensors used (Section 3). The benchmarking methodology is presented in Section 4, where we explain the entire workflow from sensor data acquisition to the analysis results. Section 5 illustrates the results, including a variety of visualisations and correlation patterns. Finally, we discuss the results obtained and close the paper with our conclusions.

## 2. Sensor Methods—Related Work

The analysis of physiological parameters from wearable sensors in order to understand the human emotional response to the immediate surroundings has been investigated for several years. In recent years, variety of affordable wearables that measure well-established physiological parameters, such as heart rate and galvanic skin response, has reached the market. As a logical consequence—and also mentioned in the—“Quantified Self” community is growing faster than ever, and increasing scientific research, especially related to emotion and stress detection [5,7,9–14–17]. In any case, the base for any further advanced analysis is adequate data in terms of accuracy, reliability, and validity [7,9,18]. However, scientific literature about the similarity and correlation of the measurements from affordable wearables compared to well-calibrated sensors from scientific laboratories is.

### 2.1. Similarity

Generally speaking, the term ‘similarity’ is not rigorously defined. A variety of similarity measures exist, from distance-based (e.g., Euclidean distance), feature-based (e.g., Fourier coefficients), model-based (e.g., autoregressive), and elastic measures such as Dynamic Time Warping (DTW) and Edit Distance on real sequence [19–22]. A comprehensive review, however, is out of the scope of this paper—the interested reader may refer to [19,20,23,24], among other work.

In this research, we employ global and linear measures to assess similarity. To uncover local similarity characteristics of time series, we follow a moving window approach combined with more informative distance metrics. Elastic measures, such as DTW and the Frechet distance,
