
with each bar showing the accuracy with 95% confidence interval running for 30 experiments over 1,000 epochs.

![](img/8c9c25929b8bfe55c61ba059d5462e42_101_0.png)

FIGURE 3.4 Univariate LSTM, Bi-LSTM, and ED-LSTM and train and test dataset based on a random split with each bar showing the accuracy with 95% confidence interval running for 30 experiments over 1,000 epochs.

We have already seen the outcomes which state that vanilla LSTM performs better compared to the rest of the LSTM and the accuracy is better when it was running on a random split dataset.

While prediction of the future cases can’t be compared, we can assume that the values are close to accurate and probably take into consideration the uncertainty due to the MSE value which we observed earlier. Almost 12 models are taken into consideration to represent multivariate models, which have been used in most of the research. We could assume that RNN was effective in forecasting the COVID-19 cases. Since the COVID cases constantly rise, no models can be fixed as the best model for forecasting COVID-19 as the data provided isn’t completely reliable. So the best way to approach it is through the usage of multiple and taking averages of it and comparing it to the actual values and also constantly evolving the model based on the requirements. However, among all the models used, we can conclude that LSTM has been the most effective.

![](img/8c9c25929b8bfe55c61ba059d5462e42_102_0.png)

- LSTM
- Bi-LSTM
- ED-LSTM

FIGURE 3.5 Multivariate LSTM, Bi-LSTM, and ED-LSTM and train and test dataset based on a static split with each bar showing the accuracy with 95% confidence interval running for 30 experiments over 1,000 epochs.

![](img/8c9c25929b8bfe55c61ba059d5462e42_103_0.png)

FIGURE 3.6 Multivariate LSTM, Bi-LSTM, and ED-LSTM and train and test dataset based on a random split with each bar showing the accuracy with 95% confidence interval running for 30 experiments over 1,000 epochs.

## 3.6 CONCLUSION AND FUTURE WORK

We have discussed at length about how COVID-19 affected the globe, and we also focused on how it affected India. Initially, we looked at the various research algorithms that have been used to analyze the fairly new problem of COVID-19, its origin, and how it spread across the world, leading to a pandemic. One of the major issues in the study was the shortage of data and its reliability, which was a problem beyond our control. However, we had the luxury of having more data available to work on various models. After the research, we looked into various visualizations of the data for the purpose of data analysis for the entire world and then for India. Once we were done with the analysis, we looked into pre-processing and scaling, which led to the usage of various models for forecasting and its prediction, after which we compared the models on various parameters to draw a conclusion to suggest which model would suffice for forecasting cases for the current stage.

COVID-19 started in November 2019 in Wuhan, China, and is still a problem to date. The world has also faced new problems; with limited solutions available, the economy hit a new low never seen before, unemployment became common in many developed countries, and in developing countries like India COVID created the additional problem of starvation due to the poor average economy. The battle between humanity and the virus continues, and while there are some measures that can be taken, such as sanitation and strict lockdowns in various regions, the mass distribution of vaccines is the best solution that we have right now. Though the supply is not yet able to meet the demand, we are slowly moving closer to this goal, which is helpful; however, the mutation of the virus could be critical so humanity needs to do everything in its means to end the virus by taking basic precautions. In terms of forecasting, the usage of various models and the constant adaptation of the models concerning the growth or decline in the spread would be effective. The newer the models, such as transformers, we can apply to the data provided, the better results will be, which would lead to better precautions being taken based on the situation so that we can get the upper hand in fighting the virus and eradicating it.

## REFERENCES

- 1. Sardar, Tanvir Habib, and Ahmed Rimaz Faizabadi. “Parallelization and analysis of selected numerical algorithms using OpenMP and Pluto on symmetric multiprocessing machine.” Data Technologies and Applications 53.1 (2019): 20–32.
- 2. Sardar, Tanvir H., and Zahid Ansari. “Distributed big data clustering using mapreduce-based fuzzy C-medoids.” Journal of the Institution of Engineers (India): Series B (2022): 1–10.
- 3. Manikiran, G., et al. “E-commerce clothing review analysis and model building.” Proceedings of Second International Conference on Advances in Computer Engineering and Communication Systems: ICACECS 2021. Singapore: Springer Nature Singapore, 2022.
- 4. Sardar, Tanvir Habib, and Zahid Ansari. “An analysis of distributed document clustering using MapReduce based K-means algorithm.” Journal of the Institution of Engineers (India): Series B 101.6 (2020): 641–650.
- 5. Ansari, Zahid, Asif Afzal, and Tanvir Habib Sardar. “Data categorization using Hadoop MapReduce-based parallel K-means clustering.” Journal of the Institution of Engineers (India): Series B 100.2 (2019): 95–103.
- 6. Rustam, Furqan, et al. “COVID-19 future forecasting using supervised machine learning models.” IEEE Access 8 (2020): 101489–101499.
- 7. Chandra, Rohitash, Ayush Jain, and Divyanshu Singh Chauhan. “Deep learning via LSTM models for COVID-19 infection forecasting in India.” PloS One 17.1 (2022): e0262708.
- 8. Karmakar, Saurav, Dibyanshu Gautam, and Purnendu Karmakar. “Modeling and predictions of COVID-19 spread in India.” Machine Vision and Augmented Intelligence—Theory and Applications: Select Proceedings of MAI 2021. Springer Singapore, 2021.
- 9. Petropoulos, Fotios, and Spyros Makridakis. “Forecasting the novel coronavirus COVID-19.” PloS One 15.3 (2020): e0231236.
- 10. Cooper, Ian, Argha Mondal, and Chris G. Antonopoulos. “A SIR model assumption for the spread of COVID-19 in different communities.” Chaos, Solitons & Fractals 139 (2020): 110057.
- 11. Senapati, Apurbalal, et al. “A novel framework for COVID-19 case prediction through piecewise regression in India.” International Journal of Information Technology 13.1 (2021): 41–48.
- 12. Muhammad, L. J., et al. “Supervised machine learning models for prediction of COVID-19 infection using epidemiology dataset.” SN Computer Science 2 (2021): 1–13.
- 13. Massonnaud, Clément, Jonathan Roux, and Pascal Crépey. “COVID-19: Forecasting short term hospital needs in France.” medrxiv (2020): 2020–2003.
- 14. Malavika, B., et al. “Forecasting COVID-19 epidemic in India and high incidence states using SIR and logistic growth models.” Clinical Epidemiology and Global Health 9 (2021): 26–33.
- 15. Anastassopoulou, Cleo, et al. “Data-based analysis, modelling and forecasting of the COVID-19 outbreak.” PloS One 15.3 (2020): e0230405.
- 16. AlJame, Maryam, et al. “Ensemble learning model for diagnosing COVID-19 from routine blood tests.” Informatics in Medicine Unlocked 21 (2020): 100449.
- 17. Sarkar, Kankan, Subhas Khajanchi, and Juan J. Nieto. “Modeling and forecasting the COVID-19 pandemic in India.” Chaos, Solitons & Fractals 139 (2020): 110049.
- 18. Chimmula, Vinay Kumar Reddy, and Lei Zhang. “Time series forecasting of COVID-19 transmission in Canada using LSTM networks.” Chaos, Solitons & Fractals 135 (2020): 109864.
- 19. Katoche, Rupinder, and Arpit Sidhu. “An application of ARIMA model to forecast the dynamics of COVID-19 epidemic in India.” Global Business Review (2021): 0972150920988653.
- 20. Velásquez, Ricardo Manuel Arias, and Jennifer Vanessa Mejia Lara. “Forecast and evaluation of COVID-19 spreading in USA with reduced-space Gaussian process regression.” Chaos, Solitons & Fractals 136 (2020): 109924.
- 21. Maleki, Mohsen, et al. “Time series modelling to forecast the confirmed and recovered cases of COVID-19.” Travel Medicine and Infectious Disease 37 (2020): 101742.
- 22. Owusu-Fordjour, Charles, Charles Kwesi Koomson, and David Hanson. “The impact of Covid-19 on learning-the perspective of the Ghanaian student.” European Journal of Education Studies 7.3 (2020): 88–101.
- 23. Perc, Matjaž, et al. “Forecasting covid-19.” Frontiers in Physics 8 (2020): 127.
- 24. Kapoor, Amol, et al. “Examining covid-19 forecasting using spatio-temporal graph neural networks.” arXiv preprint arXiv:2007.03113(2020).
- 25. Team, Epidemiology. “The epidemiological characteristics of an outbreak of 2019 novel coronavirus diseases (COVID-19)—China, 2020.” China CDC Weekly 2.8 (2020): 113.
- 26. Subbarao, E., P. Gite, A. Sharma, L. Vyakaranam, T. H. Sardar, S. N. Taqui, ... M. A. Kalam. “Investigation of solar energy for urban areas and metropolitan communities using machine learning.” Electric Power Components and System. Latest Article 4 (2023): 1–11.
- 27. Sardar, T. H., Z. Ansari, and A. Khatun. “An evaluation of Hadoop cluster efficiency in document clustering using parallel K-means.” In 2017 IEEE International Conference on Circuits and Systems (ICCS) (pp. 17–20). IEEE, 2017, December.
- 28. Sardar, T. H., A. R. Faizabadi, and Z. Ansari. “An analysis of data processing using Mapreduce paradigm on the Hadoop framework.” International Journal of Emerging Research in Management and Technology 6.5 (2017).
- 29. Sardar, T. H., A. Khatun, and S. Khan. “Design of energy aware collection tree protocol in wireless sensor network.” In 2017 IEEE International Conference on Circuits and Systems (ICCS) (pp. 12–17). IEEE, 2017, December.
- 30. Sardar, T. H., A. Muttineni, and R. Ranjan. “The future of big data in customer experience and inventory management.” In Big Data Computing (pp. 233–248). CRC Press, 2024.
- 31. Sardar, T. H., A. Khatun, S. Sengupta, Y. Alam, and T. Ara. “Machine learning in the healthcare sector and the biomedical big data: Techniques, applications, and challenges.” In Tanvir Habib Sardar and Bishwajeet Kumar Pandey (eds.), Big Data Computing. (2024): 336–352.
- 32. Sardar, T. H., S. Das, and B. K. Pandey. “Explainable AI (XAI): Concepts and theory.” In Medical Data Analysis and Processing using Explainable Artificial Intelligence (pp. 1–18). CRC Press, 2023.
- 33. Guru, P. M., G. J. Praveen, R. Dodmane, T. H. Sardar, A. Ashwitha, and A. N. Yeole. “Brain tumor identification and classification using a novel extraction method based on adapted Alexnet architecture.” In 2023 6th International Conference on Information Systems and Computer Networks (ISCON) (pp. 1–5). IEEE, 2023, March.
