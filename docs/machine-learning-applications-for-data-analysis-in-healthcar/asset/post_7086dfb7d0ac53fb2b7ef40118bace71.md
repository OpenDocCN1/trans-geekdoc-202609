
in the top 10 affected nations is described in this chapter [7]. After China, Europe is the most infested continent. The characteristics verified, active, recovering, and mortality cases, as well as the next days’ outbreak forecast, were studied in this research. State-by-state statistics from a few nations verified current instances, and death cases were also investigated.

The ability of seven well-known machine learning methods for forecasting dengue outbreaks was evaluated in this research [8]. A total of eight performance metrics are used to assess these approaches. The LogitBoost ensemble model has the highest classification accuracy of 92%, with 90% and 94% sensitivity and specificity, respectively. The very complicated structure of the COVID-19 epidemic, as well as the variance in its behavior between countries, implies that machine learning might be a useful technique for modeling the outbreak. This work [9] serves as an early benchmarking exercise to show how machine learning might be used in an additional investigation. This work also implies that by combining machine learning and SEIR models, a true innovation in outbreak prediction may be accomplished.

Using a machine learning model [10], the COVID-19 epidemic in India was anticipated based on the trend seen in China. Data collected from January 22, 2020, to April 3, 2020, the model is designed to forecast the number of cases reported, recovered instances, and mortality cases. For prediction models, the time series forecasting approach is utilized. A model-based [11] forecast of the likely epidemic maximum and scale of COVID-19 in Algeria is essential to resolve the COVID-19 tough time and a devastating situation. COVID-19 management and prevention would substantially benefit from a better knowledge of the disease’s dynamics. To the best of our understanding, the outbreak’s unique characteristics have restricted the use of all current models. A new stochastic model is provided in this study [12] to account for COVID-19’s unique transmission and prevention and capture the consequences of preventive measures adopted in Mainland China.

## 2.2 INTRODUCTION TO FACEBOOK PROPHET AND DATA VISUALIZATION

Facebook Prophet [13] is an open-source time-series modeling methodology that incorporates both traditional and novel fundamentals. It succeeds in modeling time series with multiple seasons while avoiding some of the drawbacks of other methods. The Facebook Prophet Time Series data forecasting technique has an extra restriction that accommodates nonlinear trends including yearly, monthly, and daily seasonality, as well as holiday effects. It usually performs with time series that have a lot of seasonal variation and historical information from multiple seasons. The Facebook Prophet is used in a wide range of Facebook apps to provide correct estimates for planning, control, and goal setting. It is accommodating of incomplete information and trend modifications, and it generally manages outliers. The Prophet method gives customers a lot of options for tweaking and adjusting predictions.

In this chapter, the author has evaluated a Facebook Prophet Model for the prediction of a pandemic outbreak. The author has taken a COVID-19 dataset and visualized it first to find out the country-wise plot for the number of COVID-19 cases in 2020 (Figure 2.1). Further visualization is done to find out the number of tests conducted and the number of deaths (Figure 2.2).

![](img/e7e1b4040cce350b0d1520d1f0df754d_54_0.png)

FIGURE 2.1 Country-wise plot for the number of COVID-19 cases.

![](img/e7e1b4040cce350b0d1520d1f0df754d_54_1.png)

FIGURE 2.2 Daily number of COVID-19 tests.

Figure 2.3 shows the plot for the number of deaths due to COVID-19, it has been observed that the number of deaths in the United States was skyrocketing. Such types of visualization helped government agencies to frame the policies and take some precautionary measures against the pandemic.

![](img/e7e1b4040cce350b0d1520d1f0df754d_55_0.png)

FIGURE 2.3 Number of deaths due to COVID-19.

## 2.3 BUILDING THE AI BASED FRAMEWORK TO PREDICT PANDEMIC

After data visualization, the Facebook Prophet Model is trained. The author has forecasted for 31 days, so the data frame contains dates, which includes the training. In Figure 2.4, the plot of predicted data is plot for India for the duration of March 2020 to November 2020. As you can see in this plot, the number of COVID-19 cases increased drastically from March 2020 to November 2020.

![](img/e7e1b4040cce350b0d1520d1f0df754d_55_1.png)

FIGURE 2.4 Plot of forecasted data for India.

Thereafter, the change points are plotted for visualizing the predicted data in Figure 2.5. This feature assists us in identifying trend modifications that the model has inferred.

![](img/e7e1b4040cce350b0d1520d1f0df754d_56_0.png)

FIGURE 2.5 Plot of change points to the plot.

## 2.4 ANALYZING THE PERFORMANCE OF TRAINED MODEL

At last, the performance of the trained model is analyzed and the original versus predicted values are plotted. The trained model is able to generate predictions for the next 31 days and for the next 60 days as well. In Figure 2.6, the comparative analysis of the model predictions versus the ground truth, that is, actually what actually happened in real life is done.

![](img/e7e1b4040cce350b0d1520d1f0df754d_56_1.png)

FIGURE 2.6 Original plot versus predicted plot.

The only problem with the data that is used in this chapter is that we do not have a lot of historical information like the CoV pandemic started around March 2020. So all the information that we have from March till October or November is quite limited.

## 2.5 CONCLUSION

The spread of the CoV has brought civilization to the verge of extinction. Moreover, future transmission growth and distribution events must be researched and forecasted. Machine learning methods are crucial in the investigation and forecasting of pandemics. Machine learning techniques may also help in the detection of epidemic patterns. In this chapter, the author has discussed the rise of outbreak (COVID-19) and how the Facebook Prophet Model helped in the prediction of the outbreak. The chapter will be helpful for machine learning enthusiasts, healthcare professionals, PhD scholars, researchers, and students.

## KEYWORDS

- coronavirus
- COVID-19 epidemic
- Facebook Prophet
- severe acute respiratory syndrome
- Middle East respiratory syndrome

## REFERENCES

1. Fong SJ, Dey N, Chaki J. An introduction to COVID-19. In Artificial Intelligence Coronavirus Outbreak. 2021; p. 1, https://doi.org/10.1007/978-981-15-5936-5_1.
2. Basics of COVID-19. CDC. https://www.cdc.gov/coronavirus/2019-ncov/your-health/about-covid-19/basics-covid-19.html (accessed Apr. 12, 2022).
3. Wu YC, Chen CS, Chan YJ. The outbreak of COVID-19: An overview. Journal of the Chinese Medical Association 2020;83(3):217–220, https://doi.org/10.1097/JCMA.0000000000000270.
4. Bhattraju PK et al. Covid-19 in critically ill patients in the Seattle region—case series. The New England Journal of Medicine 2020;382(21):2012–2022, https://doi.org/10.1056/NEJMOA2004500.
5. Kaushik K, Dahiya S, Singh R, Dwivedi AD. Role of blockchain in forestalling pandemics. In: Proceedings—2020 IEEE 17th International Conference on Mobile Ad Hoc and Smart Systems, MASS 2020, December 2020, pp. 32–37, https://doi.org/10.1109/MASS50613.2020.00014.
6. Khakhraria A et al. Outbreak prediction of COVID-19 for dense and populated countries using machine learning. Annals of Data Science 2021;8(1):1–19, https://doi.org/10.1007/S40745-020-00314-9/TABLES/3.
7. Yadav D, Maheshwari H, Chandra U. Outbreak prediction of covid-19 in most susceptible countries. Global Journal of Environmental Science and Management 2020;6(Special Issue (Covid-19)):11–20, https://doi.org/10.22034/GJESM.2019.06.SI.02.
8. Iqbal N, Islam M. Machine learning for dengue outbreak prediction: A performance evaluation of different prominence classifiers. Informatica 2019;43(3):363, https://doi.org/10.31449/INF.V43I3.1548.
9. Ardabili SF et al. COVID-19 outbreak prediction with machine learning. Algorithms 2020;13(10):249, https://doi.org/10.3390/A13100249.
10. Tiwari S, Kumar S, Guleria K. Outbreak trends of coronavirus disease—2019 in India: A prediction. Disaster Medicine and Public Health Preparedness 2020;14(5):e33–e38, https://doi.org/10.1017/DMP.2020.115.
11. Bentout S, Chekroun A, Kuniya T. Parameter estimation and prediction for coronavirus disease outbreak 2019 (COVID-19) in Algeria. AIMS Public Health 2020;7(2):306, https://doi.org/10.3934/PUBLICHEALTH.2020026.
12. Zhang Y, You C, Cai Z, Sun J, Hu W, Zhou X-H. Prediction of the COVID-19 outbreak based on a realistic stochastic model. medRxiv 2020; , https://doi.org/10.1101/2020.03.10.20033803.
13. Time Series Analysis with Facebook Prophet: How it works and How to use it | by Mitchell Krieger. Towards Data Science. https://towardsdatascience.com/time-series-analysis-with-facebook-prophet-how-it-works-and-how-to-use-it-f15ecf2c0e3a (accessed Apr. 12, 2022).
