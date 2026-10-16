
![](img/80b94770dd572ad559c67fa9921bb887_137_0.png)

Fig. 6.13. Comparison of actual and predicted upper zonal ICV rates against ICV position.

![](img/80b94770dd572ad559c67fa9921bb887_137_1.png)

Fig. 6.14. Comparison of actual and predicted middle zonal ICV rates against ICV position.

![](img/80b94770dd572ad559c67fa9921bb887_137_2.png)

Fig. 6.15. Comparison of actual and predicted lower zonal ICV rates against ICV position.

They make predictions based on ICV positions. This is to confirm that all the predicted zonal rates went to the actual zone where the ICV was opened.

## 5. Conclusions

In summary, eight supervised machine learning models were employed to predict multi-zonal rates for a smart water injection well in an oil and gas production setting. The machine learning models were trained and evaluated using PFI, a model-agnostic metric, to identify relevant features. Seven of the features were relevant and used as input to further train the top six models from the previous evaluation where all features were used. The Extra Trees model achieved the highest precision and consistency of 708 bbls RMSE and 68 bbls MAE compared to the test data. The Extra Trees predicted zonal rates were also visualised using KDE and joint plots to confirm their accuracy. Upon satisfactory results, the Extra Trees model was deployed on a new well with five months of hourly data, and the combined predicted zonal rates matched the total injected rate. Additionally, the model could predict zonal rates in instances where the ICVs were in the closed and fully opened positions. Overall, the results of this research demonstrate the potential of machine learning in predicting multi-zonal rates in oil and gas production and highlight the use of the Extra Trees model as a robust and effective tool for this task.

This research provides preliminary results for the approach employed in water injection wells. When used in producer wells, this method could provide a simple and accurate data-driven approach to estimating each reservoir unit’s volume of produced fluids based on downhole parameters. The method can also provide real-time estimates of produced volumes, aiding advanced formulation of a reservoir management plan, daily production operational changes to meet critical targets, and the operator’s policy of developing domestic oil resources responsibly. This project’s success will not end ICV mapping but will drastically reduce the number of mappings performed in the life of the field. One limitation of this study is that the model is as good as the data used to train it. When new data is introduced that falls out of the range of the model, ICV mapping will be required, and the model will be retrained with the new data to fine-tune its prediction. This limitation, however, does not downplay the immense advantages this study provides. This approach is recommended to save time and money during production using a smart well completion.

## Code Availability

The Jupyter Notebook used in this study is hosted at https://github.com/ascotjnr/Smart-Well-Completion.

## Acknowledgement

The authors wish to thank the Universiti Teknologi Petronas and the Centre for Subsurface Seismic Imaging and Hydrocarbon Prediction for supporting this work.

## References

Alhuthali, A.H., Datta-Gupta, A., Yuen, B. and Fontanilla, J.P. 2010. Field applications of waterflood optimisation via optimal rate control with smart wells. SPE Reservoir Evaluation & Engineering 13: 406–422. https://doi.org/10.2118/118948-PA.

Behrouz, T., Rasaei, M.R. and Masoudi, R. 2016. A novel integrated approach to oil production optimisation and limiting the water cut using intelligent well concept: using case studies. Iranian Journal of Oil and Gas Science and Technology 5: 27–41. https://doi.org/10.22050/IJOGST.2016.13827.

Breiman, L. 1996. Bagging predictors. Mach Learn. 24: 123–140. https://doi.org/10.1007/bf00058655.

Breiman, L. 2001. Random forests. Mach. Learn. 45: 5–32. https://doi.org/10.1023/A:1010933404324.

Brouwer, D.R. and Jansen, J.D. 2002. Dynamic optimisation of water flooding with smart wells using optimal control theory. In: European Petroleum Conference. SPE, Aberdeen. https://doi.org/10.2118/78278-MS.

Chen, T. and Guestrin, C. 2016. XGBoost: A scalable tree boosting system. pp. 785–794. In: Proceedings of the ACM SIGKDD International Conference on Knowledge Discovery and Data Mining. ACM, New York, NY, USA. https://doi.org/10.1145/2939672.2939785.

Geurts, P., Ernst, D. and Wehenkel, L. 2006. Extremely randomised trees. Mach. Learn. 63: 3–42. https://doi.org/10.1007/s10994-006-6226-1.

Gordon, A.D., Breiman, L., Friedman, J.H., Olshen, R.A. and Stone, C.J. 1984. Classification and regression trees. Biometrics 40: 874. https://doi.org/10.2307/2530946.

Huang, Z., Li, Y., Peng, Y., Shen, Z., Zhang, W. and Wang, M. 2011. Study of the intelligent completion system for Liaohe oil field. Procedia Eng. 15: 739–746. https://doi.org/10.1016/j.proeng.2011.08.138.

Jalali, Y., Bussear, T. and Sharma, S. 1998. Intelligent completion systems: the reservoir rationale. In: All Days. SPE. https://doi.org/10.2118/50587-MS.

Kuhn, M. and Johnson, K. 2013. Applied Predictive Modeling. New York, NY: Springer New York, https://doi.org/10.1007/978-1-4614-6849-3.

Malakooti, R., Ayop, A.Z., Maulianda, B., Muradov, K. and Davies, D. 2020. Integrated production optimisation and monitoring of multi-zone intelligent wells. J. Pet. Explor. Prod. Technol. 10: 159–170. https://doi.org/10.1007/s13202-019-0719-5.

Mubarak, S.M., Pham, T.R., Shamrani, S.S. and Shafiq, M. 2008. Case study: the use of downhole control valves to sustain oil production from the first maximum reservoir contact, multilateral, and smart completion well in ghawar field. SPE Production & Operations 23: 427–430. https://doi.org/10.2118/120744-PA.

Naus, N.M.J.J., Dolle, N. and Jansen, J.-D. 2006. Optimisation of commingled production using infinitely variable inflow control valves. SPE Production & Operations 21: 293–301. https://doi.org/10.2118/90959-PA.

Otchere, D.A., Arbi Ganat, T.O., Gholami, R. and Lawal, M. 2021. A novel custom ensemble learning model for an improved reservoir permeability and water saturation prediction. J. Nat. Gas Sci. Eng. 91: 103962. https://doi.org/10.1016/j.jngse.2021.103962.

## CHAPTER 7

## Carbon Dioxide Low Salinity Water Alternating Gas (CO₂ LSWAG) Oil Recovery Factor Prediction in Carbonate Reservoir

## Using Supervised Machine Learning Models

Eric Thompson Brantson,1,* Zainab Ololade Iyiola,1 Yao Yevenyo Ziggah,2 Alexander Ofori Mensah,1 Daniel Asante Otchere,3,4 Efua Eduamba Abakah-Paintsil1 and Emmanuel Karikari Duodu1

1 Department of Petroleum and Natural Gas Engineering, School of Petroleum Studies, University of Mines and Technology, Tarkwa, Ghana.

2 Department of Geomatic Engineering, Faculty of Geosciences and Environmental Studies, University of Mines and Technology, Tarkwa, Ghana.

3 Centre of Research for Subsurface Seismic Imaging, Universiti Teknologi PETRONAS, 32610, Seri Iskandar, Perak Darul Ridzuan, Malaysia.

4 Institute for Computational and Data Sciences, Pennsylvania State University, University Park, PA, USA.

* Corresponding author: etbrantson@umat.edu.gh

## 1. Introduction

With rising global energy demand and diminishing oil reserves, enhanced oil recovery (EOR) from existing brownfields is becoming increasingly important (Sheng, 2011). As production from the petroleum reservoir increases, the reservoir’s inherent primary energy depletes, resulting in insufficient reservoir pressure to drive the oil to the surface. As a result, secondary recovery methods (water or gas injection) are needed to boost production output. The oil recovered through both primary and secondary processes ranges from about 20%–40% of the original oil in place (OOIP) (Stalkup, 1984). Following the application of primary and secondary oil recovery techniques, two-thirds of the OOIP remains in the reservoir (Gbadamosi et al., 2019).

According to Brantson et al. (2019), tertiary oil recovery methods are capable of retrieving a greater amount of oil than primary or secondary recovery methods. In this study, EOR synergy methods involving the injection of low salinity water (LSW) and carbon dioxide (CO₂) gas were employed to enhance oil recovery at the field scale. The use of LSW in field trials has demonstrated a significant improvement in oil recovery (Robertson, 2007; Webb et al., 2004; Vledder et al., 2010), making it a favourable option over conventional chemical EOR methods in terms of chemical costs, environmental impact, and field process implementation (Dang et al., 2014). On the other hand, CO₂-EOR has the potential to recover an additional 15%–20% of the remaining oil in place (Ahmed, 2018). The two main mechanisms behind CO₂ injection schemes are oil swelling and viscosity reduction (AlQuraishi et al., 2019). It is noted that all reservoir lithologies, including siliciclastic, carbonate, and others, are appropriate for CO₂-EOR provided they have an enough seal to contain hydrocarbons and interconnected pore space for fluid accumulation and flow (Verma, 2015). Therefore, estimating hydrocarbon’s ultimate recovery factor provides more detailed insights into oilfield development strategies (Roustazadeh et al., 2022). The methods of material balance, decline curve analysis, and dynamic numerical simulation are used to estimate recovery factors, but they are time-consuming.

Over the years, there has been increasing awareness and concern over the continuous buildup of greenhouse gases in the atmosphere. This is due to human activities such as burning of fossil fuels, deforestation, and industrial processes that emit greenhouse gases such as carbon dioxide (CO₂), methane, and nitrous oxide. The accumulation of these gases has led to an increase in global temperatures, causing significant changes in the climate, which poses a threat to the entire world. One of the consequences of climate change is rising sea levels, which have been observed to be a direct result of the increasing levels of CO₂ and other greenhouse gases in the atmosphere. The rising sea levels have led to devastating consequences, such as flooding of coastal areas, displacement of communities, loss of habitats, and destruction of infrastructure (Santos et al., 2014). Therefore, it is crucial to find ways to mitigate the impact of greenhouse gas emissions on the environment and the world at large.

In recent years, there has been considerable attention given to the potential use of CO₂-EOR as a long-term anthropogenic CO₂ storage application (Mandadige et al., 2016). CO₂-EOR is a technique used in the oil and gas industry to extract more oil from wells by injecting CO₂ into the reservoir. This technique not only increases the amount of recoverable oil but also has
