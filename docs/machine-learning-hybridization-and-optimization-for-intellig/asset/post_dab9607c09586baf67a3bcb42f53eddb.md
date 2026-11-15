
would be helpful in states like India as at the time of publication, the factor of vaccination wasn't accounted for.

Lei Zhang et al. [18] used the LSTM model for the prediction of future cases of COVID-19 in Canada having data set until March 2020. They predicted cases of 2, 4, 6, 8, 10, 12 and 14th days with successive 2 days and forecasted that the decline in cases would start from June 2020, compared with the transmission rate of Canada with that of Italy and the USA.

Katoch et al. [19] suggested ARIMA (auto regressive integrated moving average) and SARIMA (seasonal auto-regressive integrated moving average) methods, which were used for future forecasting of COVID-19 cases based on a dataset from Johns Hopkins University (JHU). They apply difference and log transform to remove seasonality and trends in the data as it didn't pass the Augmented-Dickey fuller test. The prediction obtained a 95% confidence interval, showing a high accuracy with real-world data.

Ricardo et al. [20] used a reduced space Gaussian regression for forecasting cases and deaths with available data for 82 days from January to April. They discovered that the fatality rate in China is lower than that of the USA and they also estimated that the peak in deaths would be in July, with the total number of deaths being 132,800 and that of cases being 1.5 million. They concluded that even with strong lockdown restrictions, the rate of infection spread in the USA would increase within two months.

Mohsen et al. [21] developed a model for forecasting the upcoming confirmed and recovered cases based on the data they had from January to April. They used an auto-regressive model for the prediction of cases and recoveries which is based on a two-piece scale normal distribution. Since they were dealing with time series data, they had to make it stationary before fitting the model, which was called TP-SMN-AR (two-piece distribution based on scaled mixtures normal distribution); this is a flexible model involving classic symmetric/asymmetric and light/heavy autoregressive models.

Charles et al. [22] carried out a simple survey based on random sampling on how COVID-19 affected the students of Ghana. The effect of the pandemic pushed students towards online education; however, based on the survey, a lot of students find this inefficient as some lack the technology to do so while others don't know how to use the technology. Overall online learning in Ghana ensures that each student understands the way to access online education.

Matjaž et al. [23] predicted upcoming daily cases of COVID-19 in various regions based on the deaths and recoveries obtained in those regions previously. They developed a formula based on the growth rate in that region for the past m days in total n days. They provide results of growth in cases at various rates of infection spread to consider the best and worst-case scenario based on which the medical authorities can take necessary action.

Kapoor et al. [24] used graph neural networks (GNNs) for forecasting cases and compared them with various other time series forecasting methods. In GNNs, the models learn from a single spatio-temporal graph where the nodes represent region-level human mobility and the edges represent human mobility based on the region. The model was trained on a dataset of COVID-19 cases in the USA. On analysis, the model showed a reduction in Root Mean Squared Logarithmic Error (RMSLE) by 6% and an improvement in Pearson correlation from 0.9978 to 0.998. The chapter concluded the usage of GNNs would be beneficial for forecasting as the results obtained support their statement.

A team in China [25] carried out an overall exploratory analysis of data which was obtained in the initial days of the virus in mainland China. The chapters look into factors such as age and sex, calculation of case fatality and mortality, geo-temporal data on viral speed, epidemiological curve construction, and subgroup analysis. They compared the data obtained from the above factors with the total number of people infected, susceptible, and asymptomatic, and they calculated the rate of infection spread in Wuhan and various other parts of China.

We looked into various literatures which involved different analyses and predictions of cases of COVID-19 across various regions around the globe, and each study drew different conclusions. One of the major grievances in most of the literature was data shortage and its reliability. However, researchers continued working on the models even with the grievances. Along with similar research, few studies researched the investigation of solar energy [26], document clustering [27], data processing [28], tree protocol in wireless sensor networks [29], inventory management [30], health care [31], and medical data analysis [32, 33] using machine learning and artificial intelligence techniques. In the upcoming section, we look into data analysis and model training followed by an examination of the possible features which other countries used for bending the curve.

## 3.3 EXPERIMENTAL SETUP

### 3.3.1 DATASET

In this section, we will be working on various datasets as each dataset serves a different purpose; while some are used for training, some are used for exploratory data analysis. The dataset, which provides total confirmed cases, deaths, and recoveries, is provided by JHU. Each of the mentioned datasets has columns with the country name, state/province, latitude, and longitude coordinates, and the total cases denoted from 27 January and the dataset gets updated every day. However, in the USA, the recovered were set to 0 after 12 December, as the source where the university obtained the values stopped providing the same.

The next dataset used was obtained from crowd-sourced application programming interface (API), which provides data on various categories in India. The Indian Council of Medical Research (ICMR) provided testing details of the country as a whole from January as well as the testing details for each state from January, and it also shows the various kinds of tests performed by each state and state vaccination details. There is another dataset that has the details of various factors such as reproduction rate, vaccination rate, number of patients in ICUs, and so on for various countries, which is provided by a website called owid, available on GitHub. While most of the data are obtained from reliable sources, data on COVID-19 in general isn't as reliable as there is a high chance of asymptomatic cases.

### 3.3.2 TRAINING HYPER-PARAMETERS

The hyper-parameters are important as the different models use these hyper-parameters to make their predictions. The parameters provided work on the calculation of various equations for that specific model. When the appropriate parameters have been specified, the model uses the parameters and calculates the necessary output based on the input data. The hyper-parameters which we have used in our RNN models are as follows.

Batch size: This provides the total number of samples from the particular data set that has to be trained on the model. We could say that the total number of samples used for training the model for predictions, which are then compared with the true values, and the parameters are updated based on the changes required. There are several types of batches: batch gradient descent, when the entire samples are used as the batch size; stochastic gradient descent, when the batch size = 1, that is, one sample is trained on the model at a time; and mini-batch, when n number of samples are considered where n is greater than 1 and less than the dataset size. The type we used is stochastic gradient descent for training or model for all the LSTMs used.

Epochs: The number of epochs determines the amount of time the entire dataset was able to modify the parameters to our dataset. One epoch indicates that each sample in the dataset has been used once to update parameters or has been used for training the model. The number of epochs used on our dataset is 1,000 for training in all three LSTMs in our network.

Number of hidden layers and units: The number of hidden units in our LSTMs is 64 units and the two hidden layers were used for all the networks.

Number of steps per epoch: six steps per epoch were used to predict 4 days, which are four units of predictions in output layers.

Learning Rate: The optimizer used was Adam's optimizer, and the effective learning rate was 0.001.

## 3.4 IMPLEMENTATION

### 3.4.1 OVERVIEW

In this section, we will talk about the various models we have used in the chapter for future forecasting cases of cases. We will look into what the model does and the prediction it has provided. Before moving to prediction, we will provide a brief overview of pre-processing and acquisition of our data, after which will talk about scaling data as it plays a vital role in prediction and ultimately the models.
