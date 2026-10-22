
## 10.4.2. Step 2

In total, 207 water bodies were identified and distributed, as shown in Figure 10.7. Because of the scale and the area covered by each regional newspaper source, little or no information was found for small basins within the expected time search.

An examination between the newspaper circulation size (region covered) and the extension of the water body was carried out. The news articles about the largest water bodies reported more information from more sources, while the news items about small water bodies presented the most accurate information at the local level. It was also not possible to access some newspapers because of website restrictions or property law restrictions.

## 10.4.3. Step 3

As a result of the digital citizens’ media search, 19,490 newspaper articles from January 2016 to July 2020 were found. The largest number of articles regarding the analyzed type of water body featured the Magdalena River (4,405 news articles), followed by Hidroituango Dam (2,600 news articles), Cienaga Grande de Santa Marta (swamp, 621 news articles), and Fúquene Lake (94 news articles).

![](img/dd2f1e467aed0a84f984e6e656b2cc0f_316_0.png)

Figure 10.7 Distribution of 207 water bodies.

![](img/dd2f1e467aed0a84f984e6e656b2cc0f_318_0.png)

Figure 10.8 Web-scraping simplified process.

![](img/dd2f1e467aed0a84f984e6e656b2cc0f_319_0.png)

Text section of the news website

Figure 10.9 Example of information extracted from a newspaper website (https://www.elespectador.com).

![](img/dd2f1e467aed0a84f984e6e656b2cc0f_319_1.png)

Figure 10.10 Distribution of journal articles (percentage).

attended, civil, defense, informed, situation, generated, overflow, river, streams, Toro, Naranjal

- **_Tokenization vector (word: “overflow”). This result is calculated for each word given the paragraph as corpus:_** [1.61e-03, -1.59e-03, -4.26e-03, -4.87e-03, -1.46e-03, 1.09e-03, -3.36e-03, -1.99e-03, 8.40e-04, -2.99e-03, 2.48e-03, -3.71e-03, 2.06e-03, 2.68e-03, -1.53e-03, 4.51e-03, 4.11e-03, 2.23e-03, -2.47e-03, 1.03e-03, -4.58e-03, 3.82e-03, -4.65e-03, 9.20e-04, 2.32e-03, -2.91e-03, 4.91e-03, -4.60e-04, -4.42e-03, 3.40e-03, -3.38e-03, -2.47e-03, -3.05e-03, 2.19e-03, 2.48e-03, -2.50e-03, -3.09e-03, 2.98e-03, 2.23e-03, -1.60e-03, -3.25e-03, -2.60e-04, 6.70e-04, -4.09e-03, -6.20e-04, 4.08e-03, -3.78e-03, 1.33e-03, 4.60e-04, 2.55e-03, 1.01e-03, -8.60e-04, 4.79e-03, 3.01e-03, 2.06e-03, -1.76e-03, 9.10e-04, 1.79e-03, -3.66e-03, 3.73e-03, 9.90e-04, 2.00e-05, 1.19e-03, -4.63e-03, -1.30e-04, -1.81e-03, -2.02e-03, 3.05e-03, 1.33e-03, 2.33e-03, 2.49e-03, -1.82e-03, 7.40e-04, 1.96e-03, -3.34e-03, 1.90e-04, 1.42e-03, 1.86e-03, 4.70e-04, 3.95e-03, -2.77e-03, 1.17e-03, 1.88e-03, 4.19e-03, 2.70e-03, -3.21e-03, -4.90e-04, -4.94e-03, -4.49e-03, -3.90e-04, 2.70e-03, 4.70e-03, 4.92e-03, -3.30e-03, 3.32e-03, 3.54e-03, -1.27e-03, -3.43e-03, 3.16e-03, -3.77e-03]

- **_Top three words similar to “overflow,” given the vector distance (minimum distance):_**
  1. affected - distance: 0.275
  2. township - distance: 0.183
  3. rains - distance: 0.135

## 10.4.6. Step 6 (NLP Analysis)

The main words about each water body over time were found and represented as word cloud images. Figure 10.11 shows the word cloud image for Quebrada el Carmen, with the word *Ecopetrol*, which is the largest and primary petroleum company in Colombia. In the word cloud, we also identified the word *derrame*, which means “oil spill,” illustrating the region’s main problem related to the river.

An increase in newspaper articles published in the last years of the study period (Fig. 10.12), tripling the number of articles written between 2016 and 2019, was also found.

## 10.4.7. Step 7 (Sentiment Analysis)

Applying sentiment analysis allowed us to understand the social perception about the water bodies. For the case, the *spanish_sentiment_analysis* trained model was tested and MAE values of 0.068 and 0.198 were found regarding positive and negative reviews respectively. These values indicate the improved performance of the model regarding positive reviews. This is a logical consequence of the data sources of calibration, as positive reviews are more frequent in these websites. For example, we analyzed the sentiment toward the water body (Hidroituango Reservoir) over time. This sentiment shows the news writer's opinion, decreasing after the emergency,

![](img/dd2f1e467aed0a84f984e6e656b2cc0f_321_0.png)

Quebrada El Carmen

Figure 10.11 Word cloud image for Quebrada el Carmen representing the news articles about the water bodies (rivers) composing the Magdalena River Basin.

![](img/dd2f1e467aed0a84f984e6e656b2cc0f_321_1.png)

Figure 10.12 Number of newspaper articles about the rivers composing the Magdalena River Basin.

in comparison with the previous months, as presented in Figure 10.13. This result indicates a negative mainstream opinion about the project due to the emergency. The y-scale values in Figure 10.13 are limited to those found in Hidroituango Reservoir, while the horizontal line, intended to represent clearly the changes in sentiment before and after the emergency.

![](img/dd2f1e467aed0a84f984e6e656b2cc0f_322_0.png)

Figure 10.13 Sentiment change over time: Hidroituango.

## 10.4.8. Step 8 (Validation)

- *Sentiment index versus monthly river-level ranges next to Hidroituango Dam and Bogotá River.* The graphical results of the comparison between the sentiment index and the monthly river-level ranges of the Cauca River stations (located next to the dam) related to the Hidroituango Dam emergency in April 2018 are shown in Figure 10.14. Likewise, the Bogotá River sentiment results over time were validated through a river-level station at the river mouth, as shown in Figure 10.15.

In both cases, larger monthly level ranges are related to decreases in the sentiment toward the water body (dark dashed lines, Figs. 10.14 and 10.15). Nevertheless, due to the characteristics of each water body, its associated problems, and main physical variables, it is not possible to infer a direct relation between sentiments toward water bodies and flow/level changes. This suggests detailed research on each water body to understand the nexus between communities and water bodies.

- *Correlation of climatic events and sentiment index.* Due to the lack of available news covering the complete time range, only Bogotá River, Cauca River, and Magdalena River were used in this analysis. The results of the correlation of climatic variables (precipitation and temperature) and the sentiment index are shown in Table 10.3.

![](img/dd2f1e467aed0a84f984e6e656b2cc0f_323_0.png)

Figure 10.14 Monthly river-level range, Puerto Valdivia station in the Cauca River (Continuous line) versus Hidroituango sentiment (Dash line).

![](img/dd2f1e467aed0a84f984e6e656b2cc0f_324_0.png)

Figure 10.15 Monthly river-level range, La Campina station (Continuous line) versus Bogotá River sentiment (Dash line).

### Table 10.3 Correlation of monthly sentiment index and monthly climatic data.

| Element | Precipitation Min | Precipitation Max | Temperature Min | Temperature Max |
|---|---|---|---|---|
| Bogotá River | -0.050 | 0.010 | 0.038 | 0.023 |
| Cauca River | 0.032 | -0.099 | -0.006 | -0.130 |
| Magdalena River | -0.101 | -0.217 | 0.018 | -0.197 |

### Table 10.4 Confusion matrix results from Ayapel Swamp, showing high and low values of Precipitation (Pr.) and Temperature (Temp.) versus sentiment index.

|  | True negative | False positive | False negative | True positive |
|---|---|---|---|---|
| Pr. min | 34 | 15 | 1 | 2 |
| Temp. min | 35 | 17 | 0 | 0 |
| Pr. max | 33 | 16 | 2 | 1 |
| Temp. max | 35 | 17 | 0 | 0 |

These results are explained by the difficulty in filtering the topic from the obtained news related to climatic conditions (e.g., higher temperatures and precipitation). This is an important statement, considering that most of the newspaper articles include components that cannot be easily measurable by means of physical variables. Likewise, a precise identification of the spatial location and the temporal range of the events remains a challenge.

These results reveal that the spatial distribution, the amount of information, the time range, and the integration of multiple topics are key components for using digital news information in an IWRM.

- 3. Confusion matrix of extreme events identified by climatic variables (precipitation and temperature) versus number of articles over time.

Two examples of the confusion matrix application are presented in Tables 10.4 and 10.5. The first one refers to the Ayapel Swamp in the northern area of the Magdalena River Basin. The Betania Reservoir results are also presented. This reservoir is located in the upper river region.

While the confusion matrix results are inconclusive because of the multiple climatic, social, or environmental variables that can influence a news article, it is possible to analyze the patterns for which the True
