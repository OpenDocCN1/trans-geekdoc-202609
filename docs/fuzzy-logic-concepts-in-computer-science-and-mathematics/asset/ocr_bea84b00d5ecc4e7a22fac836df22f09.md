The relational operator is utilized to generate the PWM signal, working in conjunction with logical operations. The inverter operates with two PWM signals. The “Not” operator is employed to negate and generate the complementary PWM signal.

![](bbox=[0.12, 0.24, 0.87, 0.38])

**FIGURE 1.16** Single-phase asynchronous driven by an inverter chopper, control part.

After implementing the same fuzzy controller used for the DCM, the speed response of the single-phase asynchronous motor is depicted in Figure 1.17, demonstrating the motor’s precise tracking of the specified reference speed. The system exhibits an impressive response time of just 0.5 s, displaying no overshooting or steady-state errors. The motor operates effectively, responding to speeds of 400 and 800 RPM. These responses are achieved under a resistive torque of 2 Nm. Upon the application of a torque disturbance of 5 Nm at 6 seconds, the motor promptly rejects the disturbance, with only minor oscillations observed.

![](bbox=[0.13, 0.63, 0.87, 0.89])

**FIGURE 1.17** Single-phase asynchronous motor speed response.