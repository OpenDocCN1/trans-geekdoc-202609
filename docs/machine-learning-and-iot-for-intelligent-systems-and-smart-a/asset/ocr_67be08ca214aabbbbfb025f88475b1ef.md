+   iv. DC supply preferred.

+   v. Primary components of the waveforms are used for analysis.

+   vi. Turns ratio h = 1 for ideal transformer high.

Equivalent circuit of LCL-T Inverter is shown in Figure 3.3.

State space model is a mathematical model of state variables, where output and input are related by differential equations. The number of states, outputs, inputs, the vector variables, algebraic equations and differential equations are written as matrix equations. The time-domain approach (also known as the “state space representation”) examine systems with multiple inputs and outputs. The circuit contains the number of inductors and capacitors. The state variables signify the magnetic and electric fields of the inductors and capacitors, respectively. The state equation provides system behavior. The state model gives the time history of the state variables.

```
$$\dot{X} = Ax + Bu \tag{3.1}$$
```

Where

```
$$\dot{X} = \begin{bmatrix} \frac{di_{Ll}}{dt} \\ \frac{dV_{C_F}}{dt} \\ \frac{di_{L_G}}{dt} \end{bmatrix} x = \begin{bmatrix} i_{Ll} \\ V_{C_F} \\ i_{L_G} \end{bmatrix} u = \begin{bmatrix} V_i \\ V_G \end{bmatrix}$$
```

The state- space mathematical model for LCL-T filter is found from Figure 3.3 and the load side equations are given in Equations (3.2)–(3.4)

```
$$\frac{d}{dt} i_{Ll} = V_i \frac{1}{L_l} - V_{C_F} \frac{1}{L_F} \tag{3.2}$$
```

```
$$\frac{d}{dt} V_{C_F} = \frac{1}{C_F} (i_{Ll} - i_{L_G}) \tag{3.3}$$
```

```
$$\frac{d}{dt} i_{L_G} = -V_G \frac{1}{L_G} + V_{C_F} \frac{1}{L_G} \tag{3.4}$$
```

From Equations (3.2), (3.3) and (3.4), we get the model represented as a continuous state space model, given by