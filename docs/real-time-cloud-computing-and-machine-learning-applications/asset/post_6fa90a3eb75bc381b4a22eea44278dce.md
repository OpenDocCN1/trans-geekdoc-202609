
[content]
# 672 T. P. Fowdur, L. Babooram, M. N-U-Ibn Nazir Rosun and M. Indoonadon

![](img/2b52fde0e707e8c2f05a10309c3f8982_683_0.png)

Figure 6.51. Prediction Result is shown in Textfield.

## 6.5. CLOUD DATABASE CONFIGURATIONS AND HOSTING FOR WEATHER FORECASTING

This section discusses the steps involved in creating an account on the IBM platform, creating a Cloudant database on the IBM Cloud platform, and hosting a java servlet using the eclipse IDE to deploy the application on the Cloud platform.

### 6.5.1. Creating a New Cloudant Database to Store Weather Observations

This section consists of creating a new Cloudant database and configure it to store incoming weather observations from the edge devices. The steps to create the database are as follows:

1. Login into the IBM Cloud Platform and search for “Cloudant” in the search bar. The results will be shown in the Catalogue Results as in Figure 6.52. Click on “Cloudant” to go to the account creation page.

![](img/2b52fde0e707e8c2f05a10309c3f8982_684_0.png)

Figure 6.52. Search for Cloudant.

2. Next, configure a resource group as shown in Figure 6.53. For this step, the values were left on default. Then, click on.

![](img/2b52fde0e707e8c2f05a10309c3f8982_684_1.png)

Figure 6.53. Setting a resource group and region for the database.

3. After creating the Cloudant database, it will be available on the resource list as shown in Figure 6.54. Click on view Full details to view the details of the database. Click on “Launch Dashboard” to log into the Cloudant platform.

![](img/2b52fde0e707e8c2f05a10309c3f8982_685_0.png)

Figure 6.54. Access Cloudant Database via Resource List.

4. The Cloudant System panel looks as in in Figure 6.55. To create a database here, click on "Create Database" and then enter the database name, in this case, "weather_data" as shown in Figure 6.55.

![](img/2b52fde0e707e8c2f05a10309c3f8982_685_1.png)

Figure 6.55. Creating a new Database.

5. The database will then be created with the default configuration as shown in Figure 6.66.

![](img/2b52fde0e707e8c2f05a10309c3f8982_686_0.png)

Figure 6.56. Database after new user to Creation.

6. To add a new user to the database, click on the database that the new user must be added, then click on permission and click on Generate API API Key as shown in Figure 6.57.

![](img/2b52fde0e707e8c2f05a10309c3f8982_686_1.png)

Figure 6.57. Creating New API Key.

7. The new user will be added, the user will receive a key and the corresponding password for the key. Cloudant will not store this key, once forgotten another API key will have to be generated again. Give the new API Key the admin permission so that it may write and read data from the database as shown in Figure 6.58.

![](img/2b52fde0e707e8c2f05a10309c3f8982_687_0.png)

Figure 6.58. Give admin permission to the new user.

### 6.5.2. Adding a New Index to the Database

When IBM Cloudant Query is used, the query planner looks at the selector (the query) to determine the correct index to choose from. If it doesn't find a suitable index, it uses the _all_docs special index, which looks up documents by ID. In the worst-case scenario, it returns all the documents by ID. In memory, the documents are filtered out using a selector, which is, why, even without an index, it is still possible to query with various fields. Full table scans are expensive to process thus, it is recommended that to create an index to decrease processing time.

To add a new selector index to the database, the following steps are followed:

- 1. Choose the database to add the new index and Click on Query as shown in Figure 6.59.

![](img/2b52fde0e707e8c2f05a10309c3f8982_687_1.png)

Figure 6.59. Click on Query.

- 2. Click on “Manage indexes” as shown in Figure 6.60.

![](img/2b52fde0e707e8c2f05a10309c3f8982_688_0.png)

Figure 6.60. Click on Manage Indexes.

- 3. Replace the index field with the appropriate key to use. (In this case, it is idx) and click on “Create Index” as shown in Figure 6.61. The index will then be created and can be used in queries.

![](img/2b52fde0e707e8c2f05a10309c3f8982_688_1.png)

Figure 6.61. Choose the appropriate key.

## REFERENCES

- [1] Kapoor, P., Bedi, S. S., Weather forecasting using sliding window algorithm, ISRN Signal Process. (2013) 1–5 2013, doi: 10.1155/2013/156540.
- [2] Wiston, M., and Gkagamgasto, M., Weather Forecasting: From the Early Weather Wizards to Modern-day Weather Predictions, Journal of Climatology and Weather Forecasting, vol. 06, no. 02, 2018, doi: 10.4172/2332-2594.1000229.
- [3] Wang, B., Lu, Yan, Z., Luo, Li, T., Zheng, Y., and Zhang, G., Deep Uncertainty, Proceedings of the 25th ACM KDD International Conference on Knowledge Discovery and Mining, 2019, doi: 10.1145/3329504.
- [4] Kulkarni, P., and Kute, P., Internet of things based for remote monitoring of weather parameters, Int. J. Adv. Electron. Sci. 3 (2016) 66–73.
- [5] De Castro, J., Salre, G., and Gerardo, B., Flash flood prediction based on nonlinear regression analysis in Proceedings of the World Congress on Engineering and Science, San Francisco.
- [6] Krishappa, D., Irwin, D., and Lyons, E., CloudCast: short-term weather forecasts, in North American Physics Symposium (NAPS), Austin, TX, 2016, doi: 10.1109/NAPS.7747859.
- [7] Mathur, S., A simple weather model using mathematical methods, Ind. Res. (2012).
- [8] Ansari, H., and Kumar, P., Rainfall prediction using stochastic methods, Int. J. Pract. 2 (2017).
- [9] Prabhakaran, S., and Tarun, P., Daily precipitation predictions using three different wavelet neural network algorithms by meteorological data, Stoch. Environ. Risk Assess. 29 (.
- [10] Liu, L., Ma, Z., and Fan, Y., Hadoop-based application for weather forecast, Data. Appl. 6 (2013), doi: 10.1016/prtycy.2012.
- [11] Shams, S., Shahidi, A., and Li, Z., Seasonal to inter-annual climate prediction using K-NN technique, in Wireless Networks, Berlin, Heidelberg, doi: 10.1017/978-3-540-8985-5.
- [12] Meijer, G., Predicting the Dutch Weather Using Recurrent Neural, University of Twente, Enschede, 2017.
- [13] Suksri, S., and Kimpan, W., Neural network training model for weather forecasting using fireworks algorithm, in International Computer Science and Engineering Conference (ICSEC), Chiang Mai, Thailand, 2016, doi: 10.1109/ICSEC.2016.7859952.
- [14] OpenWeatherMap.org, Current weather data – OpenWeatherMap. Openweathermap.org, 2020. https://openweathermap.org/current (accessed Apr. 28, 2021)
