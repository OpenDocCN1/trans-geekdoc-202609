# 31.4.4.2 Forecast timeliness

Cooper et al. (2001) propose using earnings forecast timeliness to identify lead analysts. The forecast timeliness is computed using the following procedure. First, we calculate the cumulative days required to generate the N forecasts preceding or following each of the K forecasts by an analyst in a given year using the formula:

$$T_0 = \sum_{k=1}^{K} \sum_{i=1}^{N} t_{ik}^0, \tag{31.4}$$

$$T_1 = \sum_{k=1}^{K} \sum_{i=1}^{N} t_{ik}^1, \tag{31.5}$$

where $t_{ik}^0$ and $t_{ik}^1$ denote the number of days by which forecast $i$ either precedes or follows the $k$th forecast by a selected analyst, respectively. The following test statistics are then computed for each analyst:

$$\text{LFR} = \frac{T_0}{T_1}. \tag{31.6}$$

Cooper et al. (2001) identify top-ranked analysts as those with the LFR statistics significant at the 10% level. It is noted that there are no theoretical arguments on the choice of the parameter $N$ in (31.4) and (31.5). We choose $N = 3$ and $N = 5$ to study the relationship between the structural hole measure and analyst forecast timeliness. We use $N = 3$ to identify timeliness leaders by the LFR ratios. Table 31.4 presents the number of timeliness leaders and the percentage of timeliness leaders as the total number of analysts in the sample period of 1994-2016. On average, timeliness leaders account for 23% of the total analyst population, which is two times the percentage of accuracy leaders in our sample period. We then test the difference of the measures of structural hole (constraint and rank of constraint) between the timeliness leaders and other analysts. Results in Panel B of Table 31.5 indicate that timeliness leaders occupy more structural holes than other analysts, with the constraint of timeliness leaders significantly smaller than those of other analysts. Results are similar when we choose $N = 5$ and repeat the analysis.

# 31.4.4.3 Forecast consistency

Hilary and Hsu (2013) propose that forecast consistency should be used to rank analysts, as analysts with more consistent earnings forecast have higher