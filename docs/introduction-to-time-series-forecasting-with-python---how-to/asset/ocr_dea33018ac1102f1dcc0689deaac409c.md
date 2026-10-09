![](bbox=[0.13, 0.12, 0.87, 0.49])

Figure 25.2: ACF plot with lags=50 on the Minimum Daily Temperatures dataset.

# ### 25.3 Partial Autocorrelation Function

A partial autocorrelation is a summary of the relationship between an observation in a time series with observations at prior time steps with the relationships of intervening observations removed.

The partial autocorrelation at lag $k$ is the correlation that results after removing the effect of any correlations due to the terms at shorter lags.

— Page 81, Section 4.5.6 Partial Autocorrelations, *Introductory Time Series with R*.

The autocorrelation for an observation and an observation at a prior time step is comprised of both the direct correlation and indirect correlations. These indirect correlations are a linear function of the correlation of the observation, with observations at intervening time steps. It is these indirect correlations that the partial autocorrelation function seeks to remove. Without going into the math, this is the intuition for the partial autocorrelation.

The example below calculates and plots a partial autocorrelation function for the first 50 lags in the Minimum Daily Temperatures dataset using the plot_pacf() function from the

<sup>2</sup>http://statsmodels.sourceforge.net/devel/generated/statsmodels.graphics.tsaplots.plot_pacf.html