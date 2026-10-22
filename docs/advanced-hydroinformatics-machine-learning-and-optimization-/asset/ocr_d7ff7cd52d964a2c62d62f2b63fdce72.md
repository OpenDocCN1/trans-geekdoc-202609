been proposed (see section 15.2.3) to be optimized by applying three objectives with which it seeks to emulate the interests in the operation of the reservoir.

# 15.2.2. Data

The period of analysis for the case study was defined from the information available on the reservoir’s operation; it corresponds to the period of 2009 to 2019, with daily time steps. These data consist of series of inflows, levels, and outflows of the reservoir (Fig. 15.4), in addition to storage elevation curve, area elevation curve, and evaporation losses. In machine learning models (which are developed in section 15.3), the normalization or standardization of data is often advisable. In this study, the data are standardized using the standard scoring method: $X_n = (X - \mu)/\sigma$, with $X$ being the value of the variable without standardization, $\sigma$ the standard deviation, and $\mu$ the average of the time series.

# 15.2.3. Reservoir Operation Model

A reservoir operation model was built from the data from the period of analysis. This model integrates water balances, physical characteristics of the dam components and a water release decision component that is integrated by machine learning models (which will be further discussed). The water balances determine the storage volume of the reservoir at each time step $t$, the level and the surface area are calculated by applying the storage-elevation curve and the area-elevation curve, respectively. The water balance equation is as follows:

$S_{t+1} = S_t + I_{N_t} - Q_{spill,t} - Q_{c,t} - EVP_t$  (15.1)

where $S_{t+1}$ (subject to $S_{t+1} \geq 0$) and $S_t$ correspond, respectively, to the storage volume of the reservoir for the next time step $(t+1)$ and the current time step $t$; $I_{N_t}$ corresponds to the inflows of the reservoir for the current time step $t$, taking the inflow time series; $EVP_t$ corresponds to the evaporation losses for the current time step $t$, which are calculated based on the surface area of the reservoir and the month of the year; $Q_{spill,t}$ corresponds to the spilled volume of the reservoir for the current time step $t$, which is calculated as a function of the height above the crest of the spillway; and $Q_{c,t}$ corresponds to the controlled outflows of the reservoir for the current time step $t$. At every time step (i.e., day), the model computes the water balance.