
## DALYs Calculation

### 3.3.1 Example: DALY Due to Stroke

The sum of YLLs and YLDs releases the overall value of DALYs to stroke in the Global region.

```r
DALY_global_stroke <- YLL_global_stroke %%
select(age
```

```r
DALY_global_stroke 6 x 5
head()
# A tibble: 3 x 5
# age sex YLL YLD DALY
# <ord><chr> dbl dbl dbl
# 1 <1 male 257916 1475. 259391
# 2 <1 female 182396 1696. 1844092
# 3 <1 both 443156 3170. 4463077
# 4 01-04 male 147563 25094. 172657
# 5 01-04 female 115680 30047. 1457288
# 6 01-04 both 264428 55142. 319570
```

Let's have a look at the 35-39 age groups.

```r
DALY_global_stroke %%
filter(age == "35-39") %%
# A tibble: 3 x 5
# age sex YLL YLD DALY
# <ord><chr> dbl dbl dbl
# 1 35-39 male 1363800. 512004. 1875809
# 2 35-39 female 875909. 533485. 1412994
# 3 35-39 both 2273474. 1045489. 3318963
```

In summary, DALYs are a valuable metric for assessing the overall burden. The DALYs due to stroke provide a comprehensive measure of the impact on the quality of life of individuals, combining the years of life lost due to premature death and the years lived with disability.

DALYs can vary significantly between conditions, reflecting both the severity and impact of each disease and quality of life. For instance, stroke and diabetes affect globally, differ widely in their DALY contributions. Strokes tend to have high DALYs due to their immediate impact on mortality (Years of Life Lost or YLLs) and long-term disability (Years lived with Disability or YLDs). On the other hand, diabetes, a chronic condition, has a lower YLL but a higher YLD, reflecting the long-term impact on quality of life.

### 3.3.2 Exercise: Total DALYs Estimation

Calculate the DALYs due to stroke in the Global region for All-ages, and compare the results with the IHME data for the year 2019 as done for the YLLs. Use the IHME provided in Section 3.1.2 Table 3.3 from the stroke_ihme dataset.

## Methods and Calculations

![](img/6b61f0d3dcab44c60cdfe4e888d549c9_48_0.png)

(a) DALYs due to stroke in the Global region for females and males.

(b) DALYs, YLLs and YLDs due to stroke in the Global region

Figure 3.4 DALYs due to stroke in the Global region

## 3.4 How DALYs are Used

DALYs, YLLs, and YLDs can be used in several ways to help identify health priorities, evaluate the impact of diseases and injuries, and inform public health decision-making. Some common uses of these metrics include:

- Prioritising public health interventions: By calculating the overall burden of disease in a population, public health practitioners can prioritise which diseases and injuries to address first. This helps allocate resources and target interventions to the areas of greatest need.
- Evaluating the impact of diseases and injuries: These metrics can be used to measure the impact of diseases and injuries on individuals and populations to track changes over time. This information can help inform public health decision-making and allocate resources more effectively.
- Comparing the burden of disease across populations: DALY, YLL, and YLD can be used to compare the burden of disease across populations and between different regions. This information can help identify disparities in health outcomes and inform targeted public health interventions.
- Evaluating the effectiveness of public health programs: These metrics can be used to evaluate the effectiveness of public health programs and assess the effectiveness of public health interventions. This information can help public practitioners identify areas for improvement and make necessary changes to ensure that programs are achieving their goals.
- Monitoring global health trends: DALY, YLL, and YLD can also be used to monitor global health trends and track changes in the burden of disease over time. This information can be used to inform global health policies and allocate resources to address emerging health threats.

To mention the case of Rwanda, the GBD 2021 results released by the IHME showed that the country has made significant progress in reducing the burden of disease over the past decade.¹ By using DALYs, YLLs, and YLDs, public health leaders were able to identify key areas for improvement and target resources to address the most health challenges. For example, the government used the DALYs metrics to address the burden of non-communicable diseases (NCDs), public health observed that conditions like cardiovascular disease and diabetes were contributing significantly to the country's overall disease burden, surpassing infectious diseases in certain demographics. This insight led to targeted policy shifts, including prioritizing funding for NCD prevention and treatment programs, investing in training for healthcare providers on chronic disease management, and increasing public awareness of lifestyle risk factors like smoking and poor diet.

Overall, the health metrics of DALY, YLL, and YLD provide valuable information for public health practitioners, researchers, and policy makers to prioritize and allocate resources, evaluate the impact of diseases and injuries, and inform public health decision-making.

### 3.4.1 General Application of DALYs

As an example here is shown how the DALY metric can be used for prevention. Suppose we have data on the number of the number of data on the number of of of of the of the of the of of of the the of of of of of the the of of of of the the the of of the the the of the of of the of of of of of of of of, We can use this information to the the number of DALYs due to disease. We can use this information to calculate the total number of lifes.

```r
# Data frame with the number of cases and average years of lost
df <- data.frame(YLL = c(5), YLD = c(10))

# Calculate the number of DALYs
total_dalys <- sum(df$DALY)
```

In this example, the number of cases and average years of lost lead to the total number of DALYs. This information can be used to inform public health policies. For example, the information could be used to the the of the the of the the of the of the the of the the of the of the the of the the of the the of the of the of the of the of the of the the of the of the the of the the of the of the the of the the of the the of the the of the of the the of the the the the the the of the the of the the of the the of the of the of the of the of the of the of the the of the the of the the of the of the the of the the of the the of the of of the of the the the of the the of the the of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of the of of of the of the of the of the of the of the the of the of the the of the the of the the of the the of the the of of the of of of of of the of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of of the of of the of the of the of the of the of the of the of the of the of the of the of the of the of the of the of the of the of the of the of the of the of the of the the of the of the of the of the of the of the of the of the of the of the of the of of of the of the of of of of of of of of.

## 3.5 HALE Calculation

Healthy Life Expectancy (HALE) is a metric used to estimate the average number of years a person can expect to live in good health, taking into account mortality and non-fatal outcomes. It is often calculated as:

```r
HALE = life expectancy – YLD
```

The process of calculating HALE for a specific population, considering factors such as sex, country, and year, involves computing the average health of individuals across different groups and aggregating information on the various conditions and associated disability weights. Comorbidity is addressed using a Monte simulation approach. Simulations are conducted to model different health conditions based on their estimated prevalence in each age group, resulting in a simulated population reflecting multi-morbidities.¹²

Positive health associated with each health condition is defined as one minus the disability weight (1 – DW). The combined health for an individual in the simulated population is determined by multiplying these positive values for all relevant health conditions.

The average health values are computed as one the Years Lived with Disability (YLD) (1 – YLD) per person in the population, which are used to calculate health-adjusted person years. The Sullivan method is employed to incorporate these average health values into the life table. By adjusting the values in the life table by the corresponding average health values, recalculating the life table using these and then using an iterative process to estimate health-adjusted person-years for different groups.

Finally, HALE is calculated by dividing the adjusted person-years for each age group by the portion of a hypothetical birth cohort alive at that age.
