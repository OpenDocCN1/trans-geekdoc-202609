observations of $X_1$ and $X_2$ are within their corresponding control limits. Also, Fig. 2.6 clearly demonstrates the ability of a multivariate scheme to detect this fault (i.e., the red star in the upper right corner (outside the control ellipse)). This point clearly represents a mismatch between $X_1$ and $X_2$. Therefore, monitoring these two process variables separately can be very misleading.

![](bbox=[0.23, 0.22, 0.77, 0.5])

FIGURE 2.6 Illustration of the disadvantage of using univariate schemes for monitoring multivariate data.

Furthermore, the use of univariate charts for monitoring multivariate processes has at least two limitations, which are described briefly below:

+   • Once joint univariate monitoring schemes are applied for multivariate process monitoring, each univariate monitoring schemes has its own procedure parameters that should be tuned before it can be used. For example, if a univariate EWMA is utilized for monitoring a single process variable, then the univariate EWMA scheme has two parameters involved (i.e., \(\gamma\) and \(L\)). Thus, the joint monitoring scheme to monitor \(p\) process variables would have \(2p\) parameters to determine.

+   • Suppose we have two variables, \(X_1\) and \(X_2\), which are monitored individually with a univariate scheme. For instance, 3-sigma thresholds are applied to each process variable. Each scheme will result in the value of the probability of a false alarm of \(\alpha = 0, 27\%\) (type I error). So the overall rate of false alarms for this case is \(\hat{\alpha} = 0, 54\%\). For instance, if 100 schemes are applied for monitoring simultaneously, the probability of a false alarm will reach 27% (i.e., 0.27% * 100). In general, if \(p\) statistically independent process variables and monitoring schemes with a false alarm rate are used, the overall false alarm rate \(\hat{\alpha}\) is

\(\hat{\alpha} = 1 - (1 - \alpha)^p\). (2.57)