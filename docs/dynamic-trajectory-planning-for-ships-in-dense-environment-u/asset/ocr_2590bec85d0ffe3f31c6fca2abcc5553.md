![](bbox=[0.137, 0.075, 0.863, 0.749])

# HEAD-ON Situation

# OVERTAKING Situation

# CROSSING Situation

**Fig. 9.** Examples of situations where the trained agent must apply COLREGs, as implemented in this work. Each example is presented in four frames, depicting the progression of the episode from left to right. These examples were generated at the end of the experiment to evaluate the agent’s ability to activate the appropriate COLREG in response to various scenarios.

be integrated to compensate for any information loses or improve the collision grid’s informational quality. The hitboxes for detecting possible collisions could be refined to better adapt to the trajectories of moving obstacles. Furthermore, the values within the collision grid could be propagated to their surroundings with weighted intensity, so that areas too close to ships are not considered safe by the agent. An evaluation of the model’s performance with actual data from AIS could also be considered to validate the agent’s maneuvers in real conditions and compare the approaches of different autonomous ships under the same

conditions. Despite the promising results of this study, there is still work to be done to ensure the collision grids’ reliability as input to the model.

# CRediT authorship contribution statement

**R. Teitgen:** Conceived and designed the analysis, Collected the data, Contributed data or analysis tools, Performed the analysis, Writing – original draft. **B. Monsuez:** Contributed data or analysis tools, Performed the analysis, Writing – original draft. **R. Kukla:** Contributed data or analysis tools, Performed the analysis, Writing – original draft.