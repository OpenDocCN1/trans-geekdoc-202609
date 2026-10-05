# CHAPTER 7 GLOBAL MODEL-AGNOSTIC METHODS

![](bbox=[0.165, 0.12, 0.755, 0.385])

Figure 7.11: ALE plots for the bike prediction model by temperature, humidity and wind speed. The temperature has a strong effect on the prediction. The average prediction rises with increasing temperature, but falls again above 25 degrees Celsius. Humidity has a negative effect: When above 60%, the higher the relative humidity, the lower the prediction. The wind speed does not affect the prediction.

months are ordered by the similarity of days of each month based on the other features, such as temperature or whether it is a holiday.

Since many of the features are related to weather, the order of the months strongly reflects how similar the weather is between the months. All colder months are on the left side (February to April) and the warmer months on the right side (October to August). Keep in mind that non-weather features have also been included in the similarity calculation, for example relative frequency of holidays has the same weight as the temperature for calculating the similarity between the months.

Next, we consider the second-order effect of humidity and temperature on the predicted number of bikes. Remember that the second-order effect is the additional interaction effect of the two features and does not include the main effects. This means that, for example, you will not see the main effect that high humidity leads to a lower number of predicted bikes on average in the second-order ALE plot.

Keep in mind that both main effects of humidity and temperature say that the predicted number of bikes decreases in very hot and humid weather. In hot and humid weather, the combined effect of temperature and humidity is not the sum of the main effects, larger than the sum. To emphasize the difference between the pure second-order effect (the 2D ALE plot you just saw) and, let us look at the partial dependence plot. The PDP shows the total effect, which combines the main prediction, the two main effects and the second-order effect (the interaction).