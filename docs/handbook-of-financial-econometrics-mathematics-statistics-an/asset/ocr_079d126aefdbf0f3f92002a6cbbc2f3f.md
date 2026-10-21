rate and with a spectral density function unbounded at the origin.² If d = 0, the series is integrated of order 0, I(0). If 0 < d <0.5, the series exhibits long memory and stationarity, if d ≥ 0.5, the series is then non-stationary³ and if d = 1 the series is integrated of order 1 or I(1). It is important to note that if the time-series is I(d) with d < 1, the series is “mean reverting”, in the sense that shocks affecting the series will disappear in the long run. On the contrary, if the series is I(d) with d ≥ 1 it is not mean reverting and shocks could eventually remain in the series forever.

Several methods exist for estimating and testing the fractional differencing parameter d. Some are parametric while others are semiparametric and can be specified in the time or in the frequency domain. In this paper, we use first a parametric frequency domain Whittle estimation approach (Dahlhaus, 1989) along with a testing procedure (Robinson, 1994), which is based on the Lagrange Multiplier (LM) principle and that also uses the Whittle function in the frequency domain. This latter method has the advantage that it remains valid even in non-stationary contexts (i.e., d ≥ 0.5) and its functional form is presented in Appendix A. In addition we also conduct the analysis with a semiparametric method, where no functional form is imposed on the I(0) error term. Here we use a local Whittle estimate in the frequency domain, based on a band of frequencies that degenerates to zero. This method (Robinson, 1995a) is described in detail in Appendix B.

# 23.4.1 Fractional cointegration

The multivariate extension of the above I(d) model refers to the concept of fractional cointegration. In a broad sense, given two real numbers d, b, the components of the vector zt are said to be cointegrated of order d, b, denoted zt ~ CI(d,b) if:

+   (i) all the components of zt are I(d),
+   (ii) there exists a vector α ≠ 0 such that st = α'zt ~ I(γ) = I(d-b), b > 0.

> Robinson (1978) and Granger (1980) justified the use of these models based on the aggregation of heterogeneous autoregressive (AR) processes. See also Chambers (1998). Gil-Alana and Hualde (2009) present an updated review of fractional integration and its applications in economic time-series.

> Non-stationary in the sense that the variance of the partial sums increases with d.