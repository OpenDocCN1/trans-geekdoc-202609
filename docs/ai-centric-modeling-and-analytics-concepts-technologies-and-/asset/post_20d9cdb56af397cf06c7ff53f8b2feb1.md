
![](img/66ecdb8eb8654ae1c99705e55a45a836_236_0.png)

### FIGURE 12.1 Flow of the Proposed Model.

Source: Khang (2021)

## 12.4 PERFORMANCE ANALYSIS AND RESULTS

The results obtained using the improved forest fire prediction system using a differential approach are presented in this section. All four classes are predicted using the proposed mechanism.

First, the results in terms of classification accuracy were elaborated. The classification accuracy was obtained using Equation 12.1:

$$\text{Classification}_{Acc} = \frac{\text{TrueP} + \text{TrueN}}{\text{TrueP} + \text{TrueN} + \text{FalseP} + \text{FalseN}} \quad (12.1)$$

TrueP indicates true-positive values, and TrueN indicates true-negative values. FalseP indicates false-positive values, and FalseN indicates false-negative values (Table 12.4).

The training dataset values were normalized between 0 and 1 to reduce the complexity of the operation. The visualization corresponding to the classification accuracy differs from the existing work without ARIMA by 5–6%, which is significant and worth studying.

The visualization results corresponding to the forest fire prediction are shown in Figure 12.2.

### TABLE 12.4
Classification Accuracy Result with Varying Dataset Sizes.

| Dataset size | Classification accuracy (%) using forest fire prediction without ARIMA | Classification accuracy (%) using forest fire prediction with ARIMA |
|---|---|---|
| 1000 | 85 | 95 |
| 2000 | 83 | 94.2 |
| 3000 | 82 | 94 |
| 4000 | 79 | 93.5 |
| 5000 | 78 | 93 |

### Classification Accuracy (%)

![](img/66ecdb8eb8654ae1c99705e55a45a836_237_0.png)

### FIGURE 12.2 Visualization Result Corresponding to Classification Accuracy.

The result, in terms of sensitivity, is considered next. This metric indicates the percentage of correctly classified instances positively into any class. The sensitivity result is given by Equation 12.2:

Sensitivity = TrueP / (TrueP + FalseN)  (12.2)

The sensitivity results are listed in Table 12.5.
The visualization results corresponding to the sensitivity are shown in Figure 12.3.

### TABLE 12.5
Sensitivity Results.

| Dataset size | Sensitivity (%) using forest fire prediction without ARIMA | Sensitivity (%) using forest fire prediction with ARIMA |
|---|---|---|
| 1000 | 72 | 75 |
| 2000 | 70 | 73.6 |
| 3000 | 65 | 73.2 |
| 4000 | 64 | 72 |
| 5000 | 63 | 71 |

### Sensitivity (%)

![](img/66ecdb8eb8654ae1c99705e55a45a836_238_0.png)

### FIGURE 12.3 Sensitivity by Varying Dataset Size.

The last result is in the form of specificity, which is the result in terms of correctly negatively classified instances from the dataset. The specificity is given by Equation 12.3:

```
Specificity = TrueN / (TrueN + FalseP)  (12.3)
```

The results corresponding to specificity are given by Table 12.6.

### TABLE 12.6
Results of Specificity Corresponding to the Visualization Results Given in Figure 12.4.

| Dataset size | Specificity (%) using forest fire prediction without ARIMA | Specificity (%) using forest fire prediction with ARIMA |
|---|---|---|
| 1000 | 28 | 25 |
| 2000 | 30 | 27 |
| 3000 | 35 | 27 |
| 4000 | 36 | 28 |
| 5000 | 37 | 29 |

![](img/66ecdb8eb8654ae1c99705e55a45a836_239_0.png)

### FIGURE 12.4 Specificity Results with and without ARIMA.

## 12.5 IMPLEMENTATION

The program was executed by clicking on the main form. The user must fill in the threshold value to check whether the temperature exceeds that limit, as shown in Figure 12.5.

If the temperature exceeds this limit, an alarm is set up. This alarm is indicated with the help of a red light in the form shown in Figure 12.6.

In this case, the initial value of the threshold was taken as 25. After inputting the threshold value, the user must click on the activated sensor options (Hahanov et al., 2022).

![](img/66ecdb8eb8654ae1c99705e55a45a836_241_0.png)

Fire related Information Observation

### FIGURE 12.7 Fire-Related Information Observation.

![](img/66ecdb8eb8654ae1c99705e55a45a836_241_1.png)

### FIGURE 12.8 Results from the Existing Work.

The red bar on the form indicates that heat and smoke were detected because of threshold violations, as shown in Figure 12.9. When the threshold is not violated, a green light is displayed.

The detection process takes the input from JSON file and then performs detection using heat and smoke sensors using fuzzy C means clustering approach. The mechanism uses the existing threshold value of 25, as shown in Figure 12.10.

![](img/66ecdb8eb8654ae1c99705e55a45a836_242_0.png)

### FIGURE 12.9 Fire-Related Information with the Proposed Work.

![](img/66ecdb8eb8654ae1c99705e55a45a836_242_1.png)

### FIGURE 12.10 Results from the Proposed Work.

![](img/66ecdb8eb8654ae1c99705e55a45a836_243_0.png)

### FIGURE 12.11 Comparison between Existing and Proposed Work.

The red bar on the form indicates that heat and smoke were detected because of threshold violations, as shown in Figure 12.11. When the threshold is not violated, a green light is displayed.

On the other hand, the existing approach produced an execution time of 7 ms and classification accuracy of 93%. The results of the proposed approach are certainly better than those of the existing approach.

## 12.6 CONCLUSION

This chapter presented the fog-based model for the prediction of forest fires. The dataset for forest fire prediction was derived from the benchmark website. The dataset pre-processing mechanism within the acquisition layer handles all the abnormalities and finalizes the classification accuracy stored within the cloud layer.

The data acquisition layer is fed into the fog layer. The fog layer contains the mechanism of energy conservation, which is achieved through a reduction mechanism using PCA. The exploratory data analysis mechanism reduces the size based on the correlation calculated using the PCA. The obtained result for the fog layer is entered within the cloud layer (Geetha et al., 2023).

The result from the cloud layer can be extracted by administrators with an account within the cloud layer. The result of the classification accuracy is in the range of 95%, which is almost 7% better than that of the existing model, which proves the worth of the study.

## REFERENCES

Alam M., (2016). “Use of ICT in higher education,” The International Journal of Indian Psychology, 3(4), 68, 162–171. www.ijip.in/Archive/v3i4/18.01.208.20160304.pdf

Amit S. N. K. B., Yoshimitsu A., (2017). “Disaster detection from aerial imagery with convolutional neural network,” In Proceedings—International Electronics Symposium on Knowledge Creation and Intelligent Computing, IES-KCIC 2017 2017-January (December), pp. 239–245. Institute of Electrical and Electronics Engineers Inc. https://doi.org/10.1109/KCIC.2017.8228593

Anderson S. R., (2015). “Mobile technology in complex emergencies: A study of digital data collection in the Norwegian NGO relief sector,” MSc University of Stavanger. https://core.ac.uk/download/pdf/52119484.pdf

Ayalew L., Hiromitsu Y., Norimitsu U., (2004). “Forest fire susceptibility mapping using GIS-based weighted linear combination, the case in Tsugawa area of Agano River, Niigata Prefecture, Japan,” Forest Fires, Vol. 1, No. 1, pp. 73–81. Springer Verlag. https://doi.org/10.1007/s10346-003-0006-9

Azmoon B., Aynaz B., Zhen L., Ye S., (2021). “Image-data-driven temperature stability analysis for preventing forest fires using deep learning,” IEEE Access 9, pp. 150623–150636. Institute of Electrical and Electronics Engineers Inc. https://doi.org/10.1109/ACCESS.2021.3123501

Barmpoutis P., Periklis P., Kosmas D., Nikos G., (2020). “A review on early forest fire detection systems using optical remote sensing,” Sensors, 20(22), 6442. https://doi.org/10.3390/s20226442

Benzekri L., Gauthier Y., “Clinical markers of vitiligo activity,” Am Acad Dermatol. 2017. 76(5):856–862. PMID: 28245942. doi: 10.1016/j.jaad.2016.12.040

Beraja Christian K. Wolf. (Sept 2021). NBER Working Paper Series Demand Composition and the Strength of Recoveries. Working Paper 29304 http://www.nber.org/papers/w29304

Bhambri P., Rani S., Gupta G., Khang A., (2022). Cloud and Fog Computing Platforms for Internet of Things. CRC Press. https://doi.org/10.1201/9781003213888

Bolourchi P., Uysal S., (2013). Forest fire detection in wireless sensor network using fuzzy logic. In IEEE Fifth International Conference on Computational Intelligence, Communication Systems and Networks, pp. 83–87. IEEE: Madrid. https://ieeexplore.ieee.org/abstract/document/6571347/

Bornmann L., Leydesdorff L., (2014). “Scientometrics in a changing research landscape,” EMBO Reports, 15(12), 1228–1232. www.embopress.org/doi/full/10.15252/embr.201439608

Dai L., Mingcang Z., Zhanyong H., Yong H., Zezhong Z., Guoqing Z., Chao W., et al., (2021). “Forest fire risk classification based on ensemble machine learning,” In International Geoscience and Remote Sensing Symposium (IGARSS) 2021 July, pp. 3924–3927. Institute of Electrical and Electronics Engineers Inc. https://doi.org/10.1109/IGARSS47720.2021.9553034.

Dhar S., Rai A. K., Nayak P., (2017). “Estimation of seismic hazard in Odisha by remote sensing and GIS techniques,” Natural Hazards, 86(72), 695–709. https://link.springer.com/article/10.1007/s11069-016-2712-3

ESCAP, (2015). Building E-Resilience: Enhancing the Role of ICTs for Disaster Risk Management (DRM). https://repository.unescap.org/handle/20.500.12870/1132

Geetha C., Neduncheliyan S., Khang A., (Eds.). (2023). “Dual access control for cloud based data storage and sharing,” Smart Cities: IoT Technologies, Big Data Solutions, Cloud Platforms, and Cybersecurity Techniques. CRC Press. https://doi.org/10.1201/9781003376064-17

Giuntini F. T., Beder D. M., Ueyama J., (2017). “Exploiting self-organization and fault tolerance in wireless sensor networks: A case study on wildfire detection application,” International Journal of Distributed Sensor Networks, 13. https://journals.sagepub.com/doi/pdf/10.1177/1550147717704120

Guha-Sapir D., Hoyois P., Below R., (2016). “Annual disaster statistical review 2015: The numbers and trends,” The Centre for Research on the Epidemiology of Disasters. http://lib.riskreductionafrica.org/bitstream/handle/123456789/1010/annual%20disaster%20statistical%20review%202008.pdf?sequence=1
