and artificial intelligence techniques. In the upcoming section, we look into data analysis and model training followed by an examination of the possible features which other countries used for bending the curve.

# 3.3 EXPERIMENTAL SETUP

# 3.3.1 DATASET

In this section, we will be working on various datasets as each dataset serves a different purpose; while some are used for training, some are used for exploratory data analysis. The dataset, which provides total confirmed cases, deaths, and recoveries, is provided by JHU. Each of the mentioned datasets has columns with the country name, state/province, latitude, and longitude coordinates, and the total cases denoted from 27 January and the dataset gets updated every day. However, in the USA, the recovered were set to 0 after 12 December, as the source where the university obtained the values stopped providing the same.

The next dataset used was obtained from crowd-sourced application programming interface (API), which provides data on various categories in India. The Indian Council of Medical Research (ICMR) provided testing details of the country as a whole from January as well as the testing details for each state from January, and it also shows the various kinds of tests performed by each state and state vaccination details. There is another dataset that has the details of various factors such as reproduction rate, vaccination rate, number of patients in ICUs, and so on for various countries, which is provided by a website called owid, available on GitHub. While most of the data are obtained from reliable sources, data on COVID-19 in general isn’t as reliable as there is a high chance of asymptomatic cases.

# 3.3.2 TRAINING HYPER-PARAMETERS

The hyper-parameters are important as the different models use these hyper-parameters to make their predictions. The parameters provided work on the calculation of various equations for that specific model. When the appropriate parameters have been specified, the model uses the parameters