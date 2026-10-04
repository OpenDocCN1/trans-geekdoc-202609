# 274 Summary: The State of Health

```
dalys_pm25 <- df %%
janitor::clean_names() %%
select(ref_area, measure, risk, obs_time, obs_value) %%
arrange(obs_time)
```

```
dalys_pm25 %%
head(
  # ref_area measure risk obs_time obs_value
  # 1 PRI DALY_PM2_5_OUT 2010 2.474
  # 2 DZA DALY_PM2_5_OUT 2010 14.680
  # 3 CHL DALY_PM2_5_OUT 2010 6.758
  # 4 OECD DALY_PM2_5_OUT 2010 5.516
  # 5 NPL DALY_PM2_5_OUT 2010 14.249
  # 6 MWI DALY_PM2_5_OUT 2010 4.211
)
```

Then, to make the data more interpretable, we convert the ref_area column from ISO3 to codes using the {country} package. Data provides information for various regions and groups, which we exclude from the analysis.

```
library(countrycode)
dalys_pm25 <- dalys_pm25 %in% c("A9", "ASEAN", "EA19", "EU27",
"EU28", "F98", "G20", "OECD",
"OCDA", "DECE", "DECDSO", "W") %%

mutate(ref_area = countrycode::country(ref_area,
                               origin = "iso3c",
                               destination = "country.name"))
```

Finally, to visualise the data use a line plot to compare Disability-adjusted life years (DALYs) due to Ambient Matter as a risk exposure per 1000 inhabitants for Egypt, Serbia, Morocco, Italy, and Iceland. These countries were selected based on geographical location and varying levels of DALYs due to Ambient Matter.

We can conclude that the Disability-adjusted life years (DALYs) due to Ambient Matter Varied across countries from 2010 to 2019. This variation may be due to differences in environmental policies, air quality, and health interventions aimed at reducing exposure to particulate matter. In particular, countries like Egypt and Serbia experienced higher DALYs due to Ambient Matter compared to countries like Iceland and Italy.

In general, the data shows that regions with high pollution, such as parts of East Asia, saw increased DALYs from respiratory conditions. This is due to the high levels of particulate matter in the air, which can lead to respiratory diseases like asthma and **chronic obstructive pulmonary disease (COPD)**. Countries with stringent air quality regulations, such as those in Western Europe, tend to have lower DALYs from pollution-related conditions.

# 17.1.2 Example of GBD Cross-Country Comparisons

The Global Burden of Disease GBD study by the **Institute for Health Metrics and Evaluation** (IHME) provides comprehensive data on various health metrics covering a vast array of diseases, injuries, and risk factors across 204 countries. To access the GBD data (<www.healthdata.org>), we can use the Sustainable Development Goals (SDG) API