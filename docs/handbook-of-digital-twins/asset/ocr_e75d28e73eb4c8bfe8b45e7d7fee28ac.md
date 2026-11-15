P200 in the inlet pipeline. The control valve V104 in the outlet pipeline provides resistance.

+   - Valves: Three types of valve symbols are present in the diagram:

+   - Manually controlled valve V-105 used to drain the process.

+   - Automatic control valve, e.g. V102, which can be adjusted to any partially opened state by an analogue signal from the control system.

+   - Automatic binary valve, e.g. V203, which can only be fully opened or closed by a binary (on/off) signal from the control system.

+   - Pumps P100 in the pipeline from TK100 to TK200 and P200 from TK200 to TK300. The pumps are capable of continuous control based on an analogue signal from the control system.

+   - Sensors in the circles. The significance of the code is as follows:

+   - Temperature, pressure, level and flow sensors are indicated in P&IDs with initial letters T, P, L and F, respectively.

+   - The second letter is I or S standing for indication or switch, respectively. Indications are analogue measurement. For example, LI determines the surface level of the tank and is implemented with an analogue ultrasound sensor at the top of the tank measuring the distance to the surface. The switches in these cases are binary sensors, all of which are related to level. They activate when the surface level is below or above a predefined threshold. The suffix _H signifies a high-level threshold and _L a low-level threshold.

+   - The number code relates the sensor to a process equipment or control loop.

# ## 26.2.3 Modelling the Physical Process

Now that the control loops have been discussed, the main functionality of the process is understood, and it is possible to discuss the modelling of the physical process. There are two fundamentally different approaches: steady state and dynamic. The former does not consider time-dependent phenomena and thus does not model control loops. The latter consider such phenomena and is useful for investigating how the process reacts to transients such as changes to the setpoint of a control loop, operation of binary actuators or various kinds of failures of the process components.

Steady-state modelling can be beneficial, especially for designing new plants and retrofits to reduce operating costs (Pinto-Varela, 2017), energy consumption (Wang et al., 2020), CO₂ emissions (Min et al., 2015), freshwater consumption (Faria & Bagajewicz, 2009) and environmental pollution (Men et al. 2020). It is an open question that what could be considered a steady-state digital twin. Sierla et al. (2020c) presented a roadmap towards generating such a twin, using the process in Figure 26.1 as a case study. In this case,