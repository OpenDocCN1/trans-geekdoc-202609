
2021), using the agent-based simulation modelling method, a multi-scenario simulation experiment was carried out on the policies and measures of the Taiyuan City hospital and government to deal with COVID-19. (Oda et al. 2015) established an urban spatial network model to analyze the spread of COVID-19 in the Wuhan situation is simulated. Due to a large amount of calculation in the multi-agent simulation process, the results are uncertain, and the epidemic spread process has Markov characteristics (Chancay-García et al. 2018); that is, the future state of the epidemic state is only related to the current state, not the previous state. Therefore, this model uses the Markov chain Monte Carlo method (MCMC) (Nair et al. 2022) to obtain the stable distribution of the results and then dynamically calibrate the critical parameters in the model. This paper uses this model to analyze the impact of the scale of urban closure and control on the spread of the epidemic after the epidemic rebounds. It puts forward suggestions to provide a reference for formulating prevention and control measures for a new round of epidemic rebounds that may come.

### 1.1 Study area and data

This paper selects a large city with typical urban characteristics as the research area. The town has a large population, complex personnel, developed traffic, and many crowded regions. Consequently, it is highly vulnerable to the threat of infectious diseases and causes serious consequences. Taking the COVID-19 epidemic in 2020 as an example, the city has experienced four processes: early import and local spread in Hubei, overseas import and spread in spring, gathering epidemic in a market in summer, and multi-point distribution in autumn and winter. This paper collects epidemic data for some of the above processes. At the same time, because the essential geographic information data is required to construct the virtual geographic environment and generate the agent during the simulation process of the spatial agent model, the spread of the epidemic is closely related to the travel activities of the people, this paper collects the primary geographic information data and travel statistics of the city.

## 2 MODEL DESIGN AND IMPLEMENTATION

Through the preliminary analysis of the existing data, this paper takes the active residents in the city as the agent and designs. It implements the agent model to simulate the spread of the virus in urban population flow and interaction under different policy measures. According to the existing news reports, statistical data and research papers, the model divides the agent into different groups (students, office workers, other groups) according to the travel groups and divides the crowd activity places according to the land type (residential, school, work areas etc.), assign travel trajectories to agents according to travel statistics, and build a virtual geographic environment to simulate the interaction of infected persons with other agents in their places (homes, hospitals, public places, etc.), the spread of viruses, and the health status of infected persons.

### 2.1 Framework of the model

The model is divided into a three-layer overall framework. The first layer is the primary data layer. This layer mainly provides the essential data (shown in Table 1) required by the model. The second layer is the model preparation layer. In this layer, the vector data in the data layer is spatially connected by GIS to obtain the land type of each building, generate environmental entity data (attributes are shown in Table 1), and extract and calculate. Calculate the total residential area and population density of each street, assign the population of each road to each floor of each residential building, generate the same amount of crowd agent data, each agent represents a resident, and design the intelligent agent to travel rules and assigns travel trajectory records to agent data.

Table 1. Environmental entity attributes.

| Property field | Illustrate |
|---|---|
| Gid | building number |
| Floor | floor number |
| Level | building type code |
| X | Longitude |
| Y | Latitude |

### 2.2 Agent attributes and travel rules

According to the statistical analysis results of the travel purpose of urban residents in the “Annual Report on Traffic Development of New Delhi” (from now on referred to as the annual report), this paper divides the crowd agents into three types of travel groups, namely students, office workers and other groups. Next, it assigns attributes to them. Then, the travel rules of the agent are determined based on the statistical results of the travel time of the three types of travel groups and the step size set by the model. It saves them in the attribute field. In addition, this paper also needs to consider relevant policies for the movement rules of agents and some parameters in the model (travel ratio, infection probability, return to work ratio). Based on the relevant news materials from January to March 2020 and the statistical results of China Unicom’s travel ratio, this paper makes the following settings for the management and control measures for the corresponding time of the model.

### 2.3 Simulation of contact groups of infected persons

The transmission methods of new coronary pneumonia include direct transmission (droplets, breathing, etc.), aerosol transmission, and contact transmission (Soni et al. 2022). Therefore, simulating the relationship network of the individuals contacted by the infected person can describe the transmission path of the virus. A complex network is a model that can be used to describe the interaction between different individuals. It can be divided into random networks, small-world networks, self-similar networks, scale-free networks, etc. (Gupta and Awasthi 2011; Gupta et al. 2017). When the susceptible person and the untreated infected person are in the same building, according to different building types, a corresponding small-world network is constructed centered on the infected person to represent the infected person and his contacts, and set the probability of infection of the susceptible person after contact as perfect, and determine whether the contact person is infected by comparing the random number with excellent to realize the spread of the virus to the adjacent nodes of the infected person.

### 2.4 The health state transition rules of infected persons

In the infectious disease model, the population can generally be divided into susceptible (S), latent(E), onset (I), removal (recovery (R) or death (D)), four states (Javed et al. 2018). Infections (after the incubation period, they carry the virus, but those who have not yet become ill are recorded) as in (Khan et al. 2020), and the diagnosis and treatment of infected persons have a more significant impact on the spread of the epidemic.

### 2.5 Model realization and parameter calibration

The model realization takes the early growth of the city’s epidemic (January 20-March 8) as an example. According to the information released by the city’s health and health commission, the model sets two agents in zone D as the initially infected persons (Mazhar et al. 2023). The simulation step is 8 hours, and the simulation time is 50 days. After running according to the process in Figure 1, the distribution map of locations where infection events.

![](img/9eefc6d2972274efeb1680c6a31895e5_140_0.png)

Figure 1. Example of distribution of infection events in simulated experiment.

The numerical results of the model take the number of people diagnosed with the real epidemic as the observed value and use the MCMC method to conduct large-scale sampling and iteration to obtain a stable distribution of simulated values (Ullah et al. 2023). Bayesian fitting explores suitable parameter value ranges that go through. After 1000 MCMC iterations, a linear regression equation is established between the sampling results and the actual values, and the unknown parameter pInfect in the program is determined by measuring the coefficients in the equation:

$y = \alpha\hat{y} + \beta$ (1)

In the formula, y is the actual value of the model, and \(\hat{y}\) is the fitted value of the model. When the output result \(\alpha\) is close to 1 and \(\beta\) is close to 0, the simulated value of the model is most comparable to the actual value, and the model parameters are the optimal parameters (Yao et al. 2021).

At the same time, to verify the rationality of the parameter calibration results, this paper compares the results of the three methods of MCMC sampling, the least-squares method and manual coarse parameter adjustment. It uses the goodness of fit (\(R^2\)) and the coefficient of equation (1) to compare; the formula for calculating \(R^2\) is as follows:

$R^2 = \frac{\sum_{i=1}^n (\hat{y}_i - \bar{y})^2}{\sum_{i=1}^n (y_i - \bar{y})^2}$ (2)

In the formula, \(\bar{y}\) is the mean value of the observed value. The best estimates of unknown parameters are shown in Table 2.

Table 2. Comparison of parameter settings.

| Parameter | Parameter Description | MCMC | Least squares | Artificial rough parameter tuning |
| :--- | :--- | :--- | :--- | :--- |
| pInfect1 | Phase 1 infection rate | 0.236 | 0.252 | 0.241 |
| pInfect2 | Stage 2 infection rate | 0.097 | 0.101 | 0.101 |
| pInfect3 | Stage 3 infection rate | 0.008 | 0.011 | 0.012 |
| alpha | Linear equation coefficients after fitting | 1.125 | 1.042 | 0.67 |
| beta | Linear equation coefficients after fitting | 1.015 | 2.123 | 93.93 |
| R² | The goodness of fit of the model | 0.995 | 0.99 | 0.851 |

The optimal infection rate MCMC fitting values of the three stages are respectively: the first stage is 0.239, the second stage is 0.099, and the third stage is 0.009. The fitted coefficients \(\alpha = 1.126, \beta = 1.011\) (Bhatt and Sharma 2023). Since the MCMC sampling results are
