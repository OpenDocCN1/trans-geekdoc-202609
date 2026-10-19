
of tourism and sightseeing reached USD 8.90 trillion, contributing to 10.3% of the global gross domestic product (GDP). The global tourism industry employs 3.3 billion people, accounting for 10.0% of global employment. Considering its contributions to economic output and employment, it is evident that tourism is significant to economies.

In 2019, the outbreak of the COVID-19 pandemic significantly impacted the global tourism market. According to data from the World Tourism Organization, the number of global inbound tourist arrivals was 1.465 billion in 2019, but this dropped to 407 million in 2020, with a decrease of 72.2% compared to 2019. In 2022, the number of global tourist arrivals reached 963 million, representing 65.7% of that in 2019. As the pandemic subsided, borders reopened, and global tourism gradually returned to its former trend. Economic growth is now expected worldwide. Thus, it is important to seize opportunities in tourism-related businesses, create operational efficiencies, and understand the characteristics of people’s travel consumption behaviors.

In Taiwan, tourism provides diverse activities for family leisure. From 2015 to 2019, more than half of annual leisure expenditures were allocated to package tours. In recent years, destination travel platforms have emerged, offering an abundance of travel information and a variety of affordable travel products and itineraries for consumer choice. This trend has increased the number of independent travelers, posing a significant challenge to traditional travel industry operators.

We identified three variables in the time dimensions of family package travel data using a cohort analysis. The effects of age, period, and cohort were analyzed through an observation of long-term changes in family package travel consumption. Package travel is not a necessity in daily life, and there was no data for several families, known as zero spending. If parameter estimation is conducted using ordinary least squares during these periods, then it may lead to biased and inconsistent results [1]. Thus, the double-hurdle model [2] and the Heckit model [3] were used to explore consumption behaviors, participation, and consumption decisions. A two-part model or two-stage decision model was used to address the issue of zero spending by analyzing the consumption behavior of tourists.

We combined the two-part model with the cohort analysis method to construct a model for the package tour consumption behavior of the Taiwanese population. We determined the factors influencing participation and expenditure decisions in family package travel, thus providing a reference for travel industry operators in formulating business strategies.

## 2. Literature Review

Previous research on tourism expenditures has been conducted in terms of macroeconomics and microeconomics. In macroeconomics, the impact of prices and income from tourist countries and destination countries on tourism expenditures were investigated. An analysis of tourist destination countries or regions, with a predominant emphasis on Europe as the primary subject, was used in the construction of an analysis model of a demand system [4], and the data were aggregated. In microeconomic studies, the optimal choice behavior of tourism demand, the influencing factors, and the construction of tourism price models were investigated [5]. The data used in these studies consisted of household or individual survey cross-sectional data, with traditional linear regression models being commonly employed [6].

### 2.1. Two-Part Model for Travel Expenditure

Weagley and Huh [7] used the double-hurdle (DH) model to explore the factors influencing the leisure consumption expenditures of households with older people who were either retired or nearing retirement in the United States. They compared the differences in the factors of decision-making on participation and consumption expenditure. The results revealed that, concerning the participation in decisions about active leisure activities, variables such as income, education level, and homeownership positively impacted the willingness of retired and near-retirement households to engage in leisure consumption.

## 3.4. Two-Part Model

### 3.4.1. Double Hurdle

The Tobit model is used to address the issue of zero expenditure in consumption [23]. It is used to analyze the observed data, assuming that zero expenditure represents the true consumption value of the goods. Zero expenditure is influenced by economic factors (corner solution), and the possibility that no consumption may result from a lack of willingness to participate can be overlooked. Cragg [2] modified the Tobit model and suggested that the origin of zero observations was determined due to corner solutions and the fact that consumers had zero demand for the product, meaning that they chose not to consume. Cragg’s double-hurdle (DH) model separates consumption into two components: the participation decision and the consumption decision. In the DH model, zero observations may occur either due to non-economic factors leading to non-participation in consumption in the first stage or due to economic factors resulting in zero expenditure in the second stage [24].

The primary distinction between the DH and Heckit models lies in the occurrence of zero observation. In the Heckit model, zero observation appears in the first stage of consumption choice, whereas in the DH model, it occurs in the first or second stage. Assuming independence between the error terms of the participation decision and consumption decision equations, the logarithmic likelihood function of the DH model is written as (1) [25,26]

$$ lnL = \sum_{0} ln[1 - \Phi(\alpha' z_i)\Phi(\frac{\beta' x_i}{\sigma})] + \sum_{+} ln[\Phi(\alpha' z_i)\frac{1}{\sigma}\phi(\frac{y_i - \beta' x_i}{\sigma})], \tag{1} $$

where $z_i$ represents the variables affecting the participation decision, $x_i$ represents the variables influencing consumption expenditure, and $y_i$ is the observable consumption expenditure. In the DH model, the explanatory variables in the participation decision equation differ from those in the consumption decision equation, as shown in Equation (2) [27,28]:

$$ \begin{pmatrix} \mu_i \\ v_i \end{pmatrix} \sim \left[ \begin{pmatrix}0\\0\end{pmatrix}, \begin{pmatrix}1 & \rho\sigma \\ \rho\sigma & \sigma^2\end{pmatrix} \right], \tag{2} $$

where $\rho$ represents the correlation coefficient. The logarithmic likelihood function of the dependent double-hurdle model with the inclusion of the correlation coefficient is expressed as (3) [29]

$$ lnL = \sum_{0} ln[1 - \Phi(\alpha' z_i, \frac{\beta' x_i}{\sigma}, \rho)] + \sum_{+} ln\left[ \Phi\left(\frac{\alpha' z_i + \frac{\rho}{\sigma}(Y_i - \beta' x_i)}{\sqrt{1-\rho^2}}\right) \frac{1}{\sigma}\phi\left(\frac{y_i - \beta' x_i}{\sigma}\right) \right]. \tag{3} $$

### 3.4.2. Heckit Model

Heckman [3] proposed a sample selection model to address zero expenditure on unobservable goods, suggesting that zero expenditure results from consumer self-selection not to participate. If model parameter estimation is performed using only a subset of the sample, then the issue of sample selection bias may arise. The Heckit model assumes a correlation between the error terms $(\mu_i, v_i)$ of the decision equation and the consumption equation, with the degree of correlation denoted as $\rho$. The bivariate normal distribution of the errors in the two equations of the Heckit model is expressed in Equation (2). In addition to using a two-step estimation method, the Heckit model also employs maximum likelihood estimation for parameter estimation. The logarithmic likelihood function for the Heckit model is specified as follows [30,31]:

$$ lnL = \sum_{0} ln[1 - \Phi(\alpha' z_i)] + \sum_{+} ln\left[ \Phi\left(\frac{\alpha' Z_i + \frac{\rho}{\sigma}(y_i - \beta' x_i)}{\sqrt{1-\rho^2}}\right) \frac{1}{\sigma}\phi\left(\frac{y_i - \beta' x_i}{\sigma}\right) \right]. \tag{4} $$
