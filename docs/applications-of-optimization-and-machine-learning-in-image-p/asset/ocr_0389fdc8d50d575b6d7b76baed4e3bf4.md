# 3.3.2.4 Random Mode

Due to the discrete nature of smell molecules, their concentrations and intensities can change over time if they are spread out over a vast area relative to the search space. As a result, trailing becomes more difficult, and the scent is lost, making it difficult for an agent to follow. The agent may be unable to continue trailing at this moment, resulting in a local minimum. When this occurs, the agent enters a random mode:

\( x_N^d \left( t+1 \right)=x_N^d \left( t \right)+r_4 * SL \) (3.22)

Random number \( r_4 \) penalizes the value of \( SL \) by stochastically increasing the step length of \( S \) . The molecule performs a step at random using Eq. (3.22) if the agent loses its track or if the trailing mode is unable to obtain the best fitness or locate the source of the smell.

As a result, the molecule will always try to retain its position on the search path that has the most concentration of the smell molecules. As previously noted, this information is used when trailing in Eq. (3.21) as the agent keeps track of its current location, \( x_{gbest}^d \left( t \right) \) agent and worst positions \( x_{worst}^d \left( t \right) \) agent, although the agent is restricted to searching only within the viable region by the optimization problem.

# 3.4 RESULTS AND DISCUSSIONS

The transmission power of −30 [dBm] has been chosen as the minimum for the experiments. The maximum power is set to offer a connection across a distance of 28.284 [m] within the random distribution area, while the transmission frequency is set to give the lowest attenuation value in the 915 Hz range [MHz], which is generally utilized in WSN applications. Finally, the sensitivity, which is defined as the minimum received power necessary for information recovery, is set at −60 [dBm]. Table 3.1 lists all the parameters values used in this investigation. There are only 10 possible

| Parameter | Value |
|---|---|
| Total number of sensor nodes | 20 |
| Power range of sensor transmission | −30 [dBm] |
| power frequency of sensor transmission (f) | 915 [MHZ] |
| Sensor's random locations area (LXL) | 20 [m] X 20 [m] |
| Sensitivity of sensor (\( P_{th} \)) | −60 [dBm] |