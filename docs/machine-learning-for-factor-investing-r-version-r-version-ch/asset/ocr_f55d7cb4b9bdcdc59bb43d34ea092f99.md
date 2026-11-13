Posterior to the discovery of these stylized facts, some contributions have aimed at building theoretical models that capture these properties. We cite a handful below:

+   - size and value: Berk et al. (1999), Daniel et al. (2001b), Barberis and Shleifer (2003), Gomes et al. (2003), Carlson et al. (2004), Arnott et al. (2014);
+   - momentum: Johnson (2002), Grinblatt and Han (2005), Vayanos and Woolley (2013), Choi and Kim (2014).

In addition, recent bridges have been built between risk-based factor representations and behavioural theories. We refer essentially to Barberis et al. (2016) and Daniel et al. (2020a) and the references therein.

While these factors (i.e., long-short portfolios) exhibit time-varying risk premia and are magnified by corporate news and announcements (Engelberg et al. (2018)), it is well-documented (and accepted) that they deliver positive returns over long horizons. We refer to Gagliardini et al. (2016) and to the survey Gagliardini et al. (2019), as well as to the related bibliography for technical details on estimation procedures of risk premia and the corresponding empirical results. A large sample study that documents regime changes in factor premia was also carried out by Ilmanen et al. (2019). Moreover, the predictability of returns is also time-varying (as documented in Farmer et al. (2019), Tsiaras et al. (2020) and Liu et al. (2020)), and estimation methods can be improved (Johnson (2019)).

In Figure 3.2, we plot the average monthly return aggregated over each calendar year for five common factors. The risk free rate (which is not a factor per se) is the most stable, while the market factor (aggregate market returns minus the risk-free rate) is the most volatile. This makes sense because it is the only long equity factor among the five series.

```
FF_factors %>>%
mutate(date = year(date)) %>>% # Turn date into year
gather(key = factor, value = value, - date) %>>% # Put in tidy shape
group_by(date, factor) %>>% # Group by year and factor
summarise(value = mean(value)) %>>% # Compute average return
ggplot(aes(x = date, y = value, color = factor)) + # Plot
geom_line() + coord_fixed(500) # Fix x/y ratio
```

The individual attributes of investors who allocate towards particular factors is a blossoming topic. We list a few references below, even though they somewhat lie out of the scope of this book. Betermier et al. (2017) show that value investors are older, wealthier and face lower income risk compared to growth investors who are those in the best position to take financial risks. The study Cronqvist et al. (2015b) leads to different conclusions: it finds that the propensity to invest in value versus growth assets has roots in genetics and in life events (the latter effect being confirmed in Cocco et al. (2020), and the former being further detailed in a more general context in Cronqvist et al. (2015a)). Psychological traits can also explain some factors: when agents extrapolate, they are likely to fuel momentum (this topic is thoroughly reviewed in Barberis (2018)). Micro- and macro-economic consequences of these preferences are detailed in Bhamra and Uppal (2019). To conclude this paragraph, we mention that theoretical models have also been proposed that link agents' preferences and beliefs (via prospect theory) to market anomalies (see for instance Barberis et al. (2020)).

Finally, we highlight the need of replicability of factor premia and echo the recent editorial by Harvey (2020). As is shown by Linnainmaa and Roberts (2018) and Hou et al. (2020), many proclaimed factors are in fact very much data-dependent and often fail to deliver sustained profitability when the investment universe is altered or when the definition of variable changes (Asness and Frazzini (2013)).