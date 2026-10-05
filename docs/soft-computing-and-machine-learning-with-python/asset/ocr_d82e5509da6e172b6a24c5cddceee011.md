# Soft Computing and Machine Learning with Python

# Stability by Vintage

Stability by vintage corresponds to breaking the development sample down by time within the development window and evaluate the model's performance in all of the periods within the data. For example, if one has information collected from January 08 to December 08, a good stability by vintage analysis would be to evaluate the model's performance over each month of 2008. This tends to increase the chance of a model to be stable after its implementation.

# Vintage Selection

Many phenomena found in nature, and even in human behaviour, repeat themselves year after year in a recurrent manner; this is known as seasonality. Choosing a development window from a very atypical month of the year can be very misleading; in credit cards, for example, choosing only December as the development window can lead to overestimation of expected losses since it is the busiest time of the year. Two approaches intend to mitigate this problem. Both approaches are based on selecting the broadest development window possible. One common window is 12 months, allowing the window to cover the whole year. Please notice, there is no need to fix the window to any particular month. The first approach corresponds to simply develop the model with this pool of observation points; it is expected for the model to be an average model that will work throughout the year. A second approach is to introduce a characteristic indicating the “month of the year” the information was collected from, or any good combination of it, and then to develop the model. A as result, one would expect a model that adjusts better to each observation point in the development window.

# Different Scale over Time

Another problem applies to the situation where characteristic values fall outside the training sample boundaries or some unknown attributes occur. To reduce the impact of this problem, one can always leave the groups with the smallest and biggest boundaries as negative infinite and positive infinite, respectively, for example, changing [0,10];[11,20];[21,30] to [-\infty,10];[11,20];[21,+\infty]. Furthermore, undefined values could also be assigned to a default group. For example, if for a numeric a non-numeric value occurs it could be assigned to a default group.