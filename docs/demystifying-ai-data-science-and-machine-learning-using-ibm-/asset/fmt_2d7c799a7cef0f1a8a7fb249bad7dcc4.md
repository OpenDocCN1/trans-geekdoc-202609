
# Variable Measurement Scales

In statistics, we typically use two types of scales: continuous (metric) and categorical (non-metric). Within these types, there are four specific scales: interval and ratio (continuous) and ordinal and nominal (categorical). [Table 2.2](#chapter2.xhtml#tbl2_2) describes these four scales and provides some examples.

## Table 2.2 Variable Measurement Scales

| Types | Traditional Scales | Characteristics | Examples | SPSS Modeler Scales |
| --- | --- | --- | --- | --- |
| Continuous (metric) | Interval | Numeric, rank order, no true zero values, difference between values is the same | F degree (0 degree is not true zero) | Continuous |
| Continuous (metric) | Ratio | Numeric, rank order, having true zero values, difference between values is the same | Age, distance, population, accident rate | Continuous |
| Categorical (non-metric) | Ordinal | Non-numeric classes, rank order, difference between responses is inconsistent | *Usage*: never; sometimes; often<br>*Agreement*: disagree, somewhat disagree, somewhat agree, agree | Ordinal |
| Categorical (non-metric) | Nominal | Non-numeric classes, no rank order, difference between responses is meaningless | *Region*: north, south, east, west<br>*Travel purpose*: business, pleasure | Nominal |
| Categorical (non-metric) | *Binary*: Nominal scale with only two levels | | *Decision*: yes, no<br>*Answer*: true, false | Flag |

![](images/ufig2_11.jpg)

However, SPSS Modeler has a slightly different scale setup with several options. In this book, I focus on the three most relevant levels: continuous, ordinal, and nominal. As you may notice, SPSS Modeler uses different terminology from the traditional names. To avoid confusion, I include the SPSS scales with their corresponding names in the same table, so you know which ones to use when working with the software.

![](images/ufig2_12.jpg)

## Interval and Ratio

“Interval” and “ratio” scales are both continuous scales represented by numerical values, which can be ranked in order and have consistent gaps (intervals) between levels across the measurements. To avoid confusion with the interval scale, I use the term “gaps” instead. The key difference between these two scales is that the ratio scale has a true zero value, while the interval scale does not. For example, Fahrenheit degrees are considered “interval” because 0°F does not mean the absence of temperature; it represents a specific value indicating very cold conditions. In contrast, “ratio” variables, such as age, distance, or scores, have true zero values since they represent 0 years, 0 distance, and 0 points.

As you can see, ratio variables are more common than interval variables, as interval variables are often found in scientific fields rather than in everyday life or business activities. However, you may notice that the term “interval” is more frequently used than “ratio” on the Internet and in many materials. One possible explanation is that authors often use “interval” to refer to the continuous scale. Perhaps for this reason, SPSS Modeler does not distinguish between the two, offering only one scale called “continuous” for both cases. This should not affect the analysis results since these two scales are used in the same way during analysis. The distinction is only important when interpreting the results. Accordingly, in this book, I will use the term “interval” for both scales to simplify the content and maintain consistency. Just remember that the SPSS Modeler software uses “continuous” for this scale.

## Ordinal

On the other hand, non-metric scales, such as “ordinal” and “nominal,” are represented by non-numeric classes. The ordinal scale has a ranking order, but the gaps between levels can be inconsistent. Examples include levels of usage (never, sometimes, often) or levels of agreement (disagree, somewhat disagree, somewhat agree, agree). These categories reflect participants’ responses to questions about their preferences or perceptions. Although they are non-numerical, they can still be ranked in order.

## Nominal

Finally, the nominal scale is represented by non-metric classes that lack any rank order, making the differences between levels meaningless. For example, the “region” variable might have levels such as north, south, east, and west. These levels do not have any inherent relationship to one another and cannot be ranked. They are primarily used to categorize variables of interest in a qualitative manner.

SPSS Modeler includes a “nominal” scale but also has a special case known as the “flag” scale. The flag scale is essentially a binary scale, which is a subtype of the nominal scale with only two levels. For instance, a “decision” can be either Yes or No, or an “answer” can be True or False. This scale is frequently used to predict risks or decisions, which is why the SPSS Modeler has a dedicated scale for it.

## Likert Scale

The Likert scale is a widely used measurement tool, typically consisting of either 5 or 7 points, designed to measure people's perceptions, behaviors, or attitudes. It always includes a middle point, as shown in [Figure 2.6](#chapter2.xhtml#fig2_6). Common examples include measuring “satisfaction” (very dissatisfied, dissatisfied, neutral, satisfied, very satisfied) or “quality” (very poor, poor, fair, good, excellent). The gaps between levels are generally consistent and considered equal. This scale is extensively used in business management and social science research.

![FIGURE 2.6 Likert scale. Return to text.](images/fig2_6.jpg)

**FIGURE 2.6** Likert scale. [Return to text.](#chapter2.xhtml#b2fig2_6)

A common question arises: should Likert scale variables be categorized as “interval” or “ordinal?” Based on the way responses are coded, Likert scales appear to be “ordinal.” However, many researchers choose to treat Likert scale variables as “interval” variables. The primary reason is that this classification allows the use of parametric statistical techniques, which require metric variables. While there are non-parametric techniques available, they are often limited and less robust. For instance, when researchers are dealing with multiple hypotheses involving complex relationships among variables, they often rely on multiple regression analysis or structural equation modeling (SEM) methods to test those hypotheses. These are parametric methods and require metric variables. Since there are no equivalent non-parametric methods, researchers often treat Likert scale variables as interval scales, enabling the use of these parametric methods.

The decision to treat Likert-scale variables as interval data often receives criticism because the Likert scale is not a true interval scale. Nonetheless, researchers in fields such as marketing, management, and social behaviors frequently categorize Likert scale data as “interval” in their studies. Although this approach has limitations—such as the restricted number of levels (5 or 7) and challenges in meeting test assumptions—it allows researchers to obtain meaningful and practical analysis results. The crucial factor is ensuring that the gaps between levels are equal throughout the measurement. This consistency distinguishes continuous scales from categorical scales. For example, when designing a survey questionnaire, the gap between “Very dissatisfied” and “Somewhat dissatisfied” should be equal to the gap between “Somewhat satisfied,” “Very satisfied,” and so on.

![](images/ufig2_13.jpg)
