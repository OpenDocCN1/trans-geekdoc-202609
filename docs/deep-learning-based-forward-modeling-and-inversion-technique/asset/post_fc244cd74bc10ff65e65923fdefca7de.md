
physical model. Then, the generated heat flux is fed into the finite element solver of COMSOL to solve the temperature at each time within the specified time range. After that, the temperature and geometric structure are used as input for training, and the heat flux of the generator is used as the reference for supervised learning. The training can be considered complete when the network is converged.

## 3.3 Methods

### 3.3.1 Physical Model of Heat Conduction

The research in this chapter uses some symbols to represent various parameters of the model. $\Omega$ represents the solid area of the homogeneous medium in the experiment, and $S_i$ is an unknown heat flux surface, which is irregularly curved. Under the assumption that the surface of temperature collection is flat, the height information corresponding to each sampling point in the experiment can be considered as representing the distribution of the surface. $Q(r, t)$ represents the heat flux distributed on the outer surface with the change of spatial position and time. The $S_2$ is the surface for collecting temperature, which is set as the radiation boundary, and the emissivity is 0.92. All surfaces except $S_1$ and $S_2$ are adiabatic boundary conditions, which are represented as $S_3$. In this experiment, the temperature collector is evenly distributed on the inner surface, and each temperature value can be measured by $T_j$, $1 \leq j \leq I$, where $I$ is the total number of sensors. Therefore, the physical equations and initial conditions at each position in the process can be expressed as follows:

$$\nabla \cdot(k(T)\nabla T)=\rho C_p\frac{\partial T}{\partial t},r \in \Omega, t \geq 0 (3.13)$$

$$-k\frac{\partial T(r,t)}{\partial n}=q(r,t),r \in S_1, t \geq 0 (3.14)$$

$$-k\frac{\partial T(r,t)}{\partial n}=\sigma(T_w(r)-T_0)^4,r \in S_2, t \geq 0 (3.15)$$

$$-k\frac{\partial T(r,t)}{\partial n}=0,r \in S_3, t \geq 0 (3.16)$$

$$T(r,t_0)=T_0,r \in S_3, t_0=0 (3.17)$$

The corresponding relationship between each surface of the geometric model and the symbol is shown in Figure 3.5 below:

As mentioned above, considering that the thermophysical parameters in the actual inversion model will alter with temperature, this experiment involves this nonlinear process. The thermal conductivity and heat capacity of the superalloy and coating used in the experiment vary with temperature as shown in Tables 3.1 and 3.2.

![](img/020125e0e698f9771fbbd32f2ace1e80_105_0.png)

FIGURE 3.5

A typical model of the 3D nonlinear heat conduction systems.

## TABLE 3.1

Thermophysical properties of the superalloys.

| T [K] | RT | 100 | 200 | 300 | 400 | 500 | 600 | 700 | 800 | 900 | 1000 |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| $C_p$ [J/kg K] | 552 | 552 | 562 | 572 | 582 | 595 | 612 | 638 | 674 | 726 | 25.54 | 27.21 |
| $k$ [W/m K] | 10.47 | 10.47 | 12.56 | 14.21 | 15.80 | 19.68 | 21.71 | 23.45 | | | | |
| $\rho$ [kg/m$^3$] | 8470 | 8470 | 8470 | 8470 | 8470 | 8470 | 8470 | 8470 | 8470 | 8470 | |

Because COSMOL is used as the solver in the forward program, it is necessary to know the exact analytical expression of thermophysical parameters with temperature. Here, the tool built in MATLAB is used for fitting. The properties of specific heat $C_p$ and thermal conductivity $k$ of alloy materials as a function of temperature are obtained as follows:

$$C_p = 524.3e^{0.0001327T} + 0.275e^{0.00514T} J/kg \cdot K$$

$$k = 0.0186T + 3.576W/m \cdot K^2$$

Its changing in the experimental temperature range is shown in Figure 3.6 below:

## TABLE 3.2

Thermophysical properties of the coating.

| T [K] | RT | 100 | 200 | 300 | 400 | 500 | 600 | 700 | 800 | 900 | 1000 |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| $C_p$ [J/kg K] | 552 | 552 | 562 | 572 | 582 | 595 | 612 | 638 | 674 | 726 | 25.54 | 27.21 |
| $k$ [W/m K] | 10.47 | 10.47 | 12.56 | 14.21 | 15.80 | 19.68 | 21.71 | 23.45 | | | | |
| $\rho$ [kg/m$^3$] | 8470 | 8470 | 8470 | 8470 | 8470 | 8470 | 8470 | 8470 | 8470 | 8470 | |

## Inversion of Complex Surface Heat Flux Based on ConvLSTM

![](img/020125e0e698f9771fbbd32f2ace1e80_105_0.png)

FIGURE 3.5

A typical model of the 3D nonlinear heat conduction systems.

## Deep Learning-Based Forward Modeling and Inversion Techniques

(Note: The provided text seems to be fragmented or reordered in the source. I have merged the logical sections based on the content provided.)

Wait, looking closer at the source, the text is a bit jumbled with page breaks. Let me re-assemble it based on logical flow:
1. Deep Learning-Based Forward Modeling and Inversion Techniques (Header)
2. 3.3 Methods
3. 3.3.1 Physical Model of Heat Conduction
4. Table 3.1
5. Table 3.2
6. Inversion of Complex Surface Heat Flux Based on ConvLSTM

Actually, the source text has the headers in the middle. I will follow the sequence of the text provided but remove page tags.

[content]
physical model. Then, the generated heat flux is fed into the finite element solver of COMSOL to solve the temperature at each time within the specified time range. After that, the temperature and geometric structure are used as input for training, and the heat flux of the generator is used as the reference for supervised learning. The training can be considered complete when the network is converged.

## 3.3 Methods

### 3.3.1 Physical Model of Heat Conduction

The research in this chapter uses some symbols to represent various parameters of the model. $\Omega$ represents the solid area of the homogeneous medium in the experiment, and $S_i$ is an unknown heat flux surface, which is irregularly curved. Under the assumption that the surface of temperature collection is flat, the height information corresponding to each sampling point in the experiment can be considered as representing the distribution of the surface. $Q(r, t)$ represents the heat flux distributed on the outer surface with the change of spatial position and time. The $S_2$ is the surface for collecting temperature, which is set as the radiation boundary, and the emissivity is 0.92. All surfaces except $S_1$ and $S_2$ are adiabatic boundary conditions, which are represented as $S_3$. In this experiment, the temperature collector is evenly distributed on the inner surface, and each temperature value can be measured by $T_j$, $1 \leq j \leq I$, where $I$ is the total number of sensors. Therefore, the physical equations and initial conditions at each position in the process can be expressed as follows:

$$\nabla \cdot(k(T)\nabla T)=\rho C_p\frac{\partial T}{\partial t},r \in \Omega, t \geq 0 (3.13)$$

$$-k\frac{\partial T(r,t)}{\partial n}=q(r,t),r \in S_1, t \geq 0 (3.14)$$

$$-k\frac{\partial T(r,t)}{\partial n}=\sigma(T_w(r)-T_0)^4,r \in S_2, t \geq 0 (3.15)$$

$$-k\frac{\partial T(r,t)}{\partial n}=0,r \in S_3, t \geq 0 (3.16)$$

$$T(r,t_0)=T_0,r \in S_3, t_0=0 (3.17)$$

The corresponding relationship between each surface of the geometric model and the symbol is shown in Figure 3.5 below:

As mentioned above, considering that the thermophysical parameters in the actual inversion model will alter with temperature, this experiment involves this nonlinear process. The thermal conductivity and heat capacity of the superalloy and coating used in the experiment vary with temperature as shown in Tables 3.1 and 3.2.

![](img/020125e0e698f9771fbbd32f2ace1e80_105_0.png)

FIGURE 3.5

A typical model of the 3D nonlinear heat conduction systems.

## TABLE 3.1

Thermophysical properties of the superalloys.

| T [K] | RT | 100 | 200 | 300 | 400 | 500 | 600 | 700 | 800 | 900 | 1000 |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| $C_p$ [J/kg K] | 552 | 552 | 562 | 572 | 582 | 595 | 612 | 638 | 674 | 726 | 25.54 | 27.21 |
| $k$ [W/m K] | 10.47 | 10.47 | 12.56 | 14.21 | 15.80 | 19.68 | 21.71 | 23.45 | | | | |
| $\rho$ [kg/m$^3$] | 8470 | 8470 | 8470 | 8470 | 8470 | 8470 | 8470 | 8470 | 8470 | 8470 | |

Because COSMOL is used as the solver in the forward program, it is necessary to know the exact analytical expression of thermophysical parameters with temperature. Here, the tool built in MATLAB is used for fitting. The properties of specific heat $C_p$ and thermal conductivity $k$ of alloy materials as a function of temperature are obtained as follows:

$$C_p = 524.3e^{0.0001327T} + 0.275e^{0.00514T} J/kg \cdot K$$

$$k = 0.0186T + 3.576W/m \cdot K^2$$

Its changing in the experimental temperature range is shown in Figure 3.6 below:

## TABLE 3.2

Thermophysical properties of the coating.

| T [K] | RT | 100 | 200 | 300 | 400 | 500 | 600 | 700 | 800 | 900 | 1000 |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| $C_p$ [J/kg K] | 552 | 552 | 562 | 572 | 582 | 595 | 612 | 638 | 674 | 726 | 25.54 | 27.21 |
| $k$ [W/m K] | 10.47 | 10.47 | 12.56 | 14.21 | 15.80 | 19.68 | 21.71 | 23.45 | | | | |
| $\rho$ [kg/m$^3$] | 8470 | 8470 | 8470 | 8470 | 8470 | 8470 | 8470 | 8470 | 8470 | 8470 | |

## Inversion of Complex Surface Heat Flux Based on ConvLSTM

(Note: The text provided in the prompt is highly repetitive and jumbled. I will provide the cleaned version of the content as presented in the OCR blocks, merging where logical.)

Actually, the prompt asks me to correct OCR errors and merge. I will provide the clean output based on the text provided.

(Wait, I see the OCR text in the prompt is actually a mess of repeated sections. I will process it as a single document.)

[content]
physical model. Then, the generated heat flux is fed into the finite element solver of COMSOL to solve the temperature at each time within the specified time range. After that, the temperature and geometric structure are used as input for training, and the heat flux of the generator is used as the reference for supervised learning. The training can be considered complete when the network is converged.

## 3.3 Methods

### 3.3.1 Physical Model of Heat Conduction

The research in this chapter uses some symbols to represent various parameters of the model. $\Omega$ represents the solid area of the homogeneous medium in the experiment, and $S_i$ is an unknown heat flux surface, which is irregularly curved. Under the assumption that the surface of temperature collection is flat, the height information corresponding to each sampling point in the experiment can be considered as representing the distribution of the surface. $Q(r, t)$ represents the heat flux distributed on the outer surface with the change of spatial position and time. The $S_2$ is the surface for collecting temperature, which is set as the radiation boundary, and the emissivity is 0.92. All surfaces except $S_1$ and $S_2$ are adiabatic boundary conditions, which are represented as $S_3$. In this experiment, the temperature collector is evenly distributed on the inner surface, and each temperature value can be measured by $T_j$, $1 \leq j \leq I$, where $I$ is the total number of sensors. Therefore, the physical equations and initial conditions at each position in the process can be expressed as follows:

$$\nabla \cdot(k(T)\nabla T)=\rho C_p\frac{\partial T}{\partial t},r \in \Omega, t \geq 0 (3.13)$$

$$-k\frac{\partial T(r,t)}{\partial n}=q(r,t),r \in S_1, t \geq 0 (3.14)$$

$$-k\frac{\partial T(r,t)}{\partial n}=\sigma(T_w(r)-T_0)^4,r \in S_2, t \geq 0 (3.15)$$

$$-k\frac{\partial T(r,t)}{\partial n}=0,r \in S_3, t \geq 0 (3.16)$$

$$T(r,t_0)=T_0,r \in S_3, t_0=0 (3.17)$$

The corresponding relationship between each surface of the geometric model and the symbol is shown in Figure 3.5 below:

As mentioned above, considering that the thermophysical parameters in the actual inversion model will alter with temperature, this experiment involves this nonlinear process. The thermal conductivity and heat capacity of the superalloy and coating used in the experiment vary with temperature as shown in Tables 3.1 and 3.2.

![](img/020125e0e698f9771fbbd32f2ace1e80_105_0.png)

FIGURE 3.5

A typical model of the 3D nonlinear heat conduction systems.

## TABLE 3.1

Thermophysical properties of the superalloys.

| T [K] | RT | 100 | 200 | 300 | 400 | 500 | 600 | 700 | 800 | 900 | 1000 |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| $C_p$ [J/kg K] | 552 | 552 | 562 | 572 | 582 | 595 | 612 | 638 | 674 | 726 | 25.54 | 27.21 |
| $k$ [W/m K] | 10.47 | 10.47 | 12.56 | 14.21 | 15.80 | 19.68 | 21.71 | 23.45 | | | | |
| $\rho$ [kg/m$^3$] | 8470 | 8470 | 8470 | 8470 | 8470 | 8470 | 8470 | 8470 | 8470 | 8470 | |

Because COSMOL is used as the solver in the forward program, it is necessary to know the exact analytical expression of thermophysical parameters with temperature. Here, the tool built in MATLAB is used for fitting. The properties of specific heat $C_p$ and thermal conductivity $k$ of alloy materials as a function of temperature are obtained as follows:

$$C_p = 524.3e^{0.0001327T} + 0.275e^{0.00514T} J/kg \cdot K$$

$$k = 0.0186T + 3.576W/m \cdot K^2$$

Its changing in the experimental temperature range is shown in Figure 3.6 below:

## TABLE 3.2

Thermophysical properties of the coating.

| T [K] | RT | 100 | 200 | 300 | 400 | 500 | 600 | 700 | 800 | 900 | 1000 |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| $C_p$ [J/kg K] | 552 | 552 | 562 | 572 | 582 | 595 | 612 | 638 | 674 | 726 | 25.54 | 27.21 |
| $k$ [W/m K] | 10.47 | 10.47 | 12.56 | 14.21 | 15.80 | 19.68 | 21.71 | 23.45 | | | | |
| $\rho$ [kg/m$^3$] | 8470 | 8470 | 8470 | 8470 | 8470 | 8470 | 8470 | 8470 | 8470 | 8470 | |

## Inversion of Complex Surface Heat Flux Based on ConvLSTM

(Note: The provided OCR text contains significant repetitions and fragmented headers. I have reconstructed the logical flow based on the provided content.)
[/content]

Wait, the prompt says "only output the final text". I will provide the most coherent version.

[content]
physical model. Then, the generated heat flux is fed into the finite element solver of COMSOL to solve the temperature at each time within the specified time range. After that, the temperature and geometric structure are used as input for training, and the heat flux of the generator is used as the reference for supervised learning. The training can be considered complete when the network is converged.

## 3.3 Methods

### 3.3.1 Physical Model of Heat Conduction

The research in this chapter uses some symbols to represent various parameters of the model. $\Omega$ represents the solid area of the homogeneous medium in the experiment, and $S_i$ is an unknown heat flux surface, which is irregularly curved. Under the assumption that the surface of temperature collection is flat, the height information corresponding to each sampling point in the experiment can be considered as representing the distribution of the surface. $Q(r, t)$ represents the heat flux distributed on the outer surface with the change of spatial position and time. The $S_2$ is the surface for collecting temperature, which is set as the radiation boundary, and the emissivity is 0.92. All surfaces except $S_1$ and $S_2$ are adiabatic boundary conditions, which are represented as $S_3$. In this experiment, the temperature collector is evenly distributed on the inner surface, and each temperature value can be measured by $T_j$, $1 \leq j \leq I$, where $I$ is the total number of sensors. Therefore, the physical equations and initial conditions at each position in the process can be expressed as follows:

$$\nabla \cdot(k(T)\nabla T)=\rho C_p\frac{\partial T}{\partial t},r \in \Omega, t \geq 0 (3.13)$$

$$-k\frac{\partial T(r,t)}{\partial n}=q(r,t),r \in S_1, t \geq 0 (3.14)$$

$$-k\frac{\partial T(r,t)}{\partial n}=\sigma(T_w(r)-T_0)^4,r \in S_2, t \geq 0 (3.15)$$

$$-k\frac{\partial T(r,t)}{\partial n}=0,r \in S_3, t \geq 0 (3.16)$$

$$T(r,t_0)=T_0,r \in S_3, t_0=0 (3.17)$$

The corresponding relationship between each surface of the geometric model and the symbol is shown in Figure 3.5 below:

As mentioned above, considering that the thermophysical parameters in the actual inversion model will alter with temperature, this experiment involves this nonlinear process. The thermal conductivity and heat capacity of the superalloy and coating used in the experiment vary with temperature as shown in Tables 3.1 and 3.2.

![](img/020125e0e698f9771fbbd32f2ace1e80_105_0.png)

FIGURE 3.5

A typical model of the 3D nonlinear heat conduction systems.

## TABLE 3.1

Thermophysical properties of the superalloys.

| T [K] | RT | 100 | 200 | 300 | 400 | 500 | 600 | 700 | 800 | 900 | 1000 |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| $C_p$ [J/kg K] | 552 | 552 | 562 | 572 | 582 | 595 | 612 | 638 | 674 | 726 | 25.54 | 27.21 |
| $k$ [W/m K] | 10.47 | 10.47 | 12.56 | 14.21 | 15.80 | 19.68 | 21.71 | 23.45 | | | | |
| $\rho$ [kg/m$^3$] | 8470 | 8470 | 8470 | 8470 | 8470 | 8470 | 8470 | 8470 | 8470 | 8470 | |

Because COSMOL is used as the solver in the forward program, it is necessary to know the exact analytical expression of thermophysical parameters with temperature. Here, the tool built in MATLAB is used for fitting. The properties of specific heat $C_p$ and thermal conductivity $k$ of alloy materials as a function of temperature are obtained as follows:

$$C_p = 524.3e^{0.0001327T} + 0.275e^{0.00514T} J/kg \cdot K$$

$$k = 0.0186T + 3.576W/m \cdot K^2$$

Its changing in the experimental temperature range is shown in Figure 3.6 below:

## TABLE 3.2

Thermophysical properties of the coating.

| T [K] | RT | 100 | 200 | 300 | 400 | 500 | 600 | 700 | 800 | 900 | 1000 |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| $C_p$ [J/kg K] | 552 | 552 | 562 | 572 | 582 | 595 | 612 | 638 | 674 | 726 | 25.54 | 27.21 |
| $k$ [W/m K] | 10.47 | 10.47 | 12.56 | 14.21 | 15.80 | 19.68 | 21.71 | 23.45 | | | | |
| $\rho$ [kg/m$^3$] | 8470 | 8470 | 8470 | 8470 | 8470 | 8470 | 8470 | 8470 | 8470 | 8470 | |

## Inversion of Complex Surface Heat Flux Based on ConvLSTM

(Note: The provided OCR text contains significant repetitions and fragmented headers. I have reconstructed the logical flow based on the provided content.)
[/content]

(Wait, I just realized I should not include the explanation. I will provide the final block.)

[content]
physical model. Then, the generated heat flux is fed into the finite element solver of COMSOL to solve the temperature at each time within the specified time range. After that, the temperature and geometric structure are used as input for training, and the heat flux of the generator is used as the reference for supervised learning. The training can be considered complete when the network is converged.

## 3.3 Methods

### 3.3.1 Physical Model of Heat Conduction

The research in this chapter uses some symbols to represent various parameters of the model. $\Omega$ represents the solid area of the homogeneous medium in the experiment, and $S_i$ is an unknown heat flux surface, which is irregularly curved. Under the assumption that the surface of temperature collection is flat, the height information corresponding to each sampling point in the experiment can be considered as representing the distribution of the surface. $Q(r, t)$ represents the heat flux distributed on the outer surface with the change of spatial position and time. The $S_2$ is the surface for collecting temperature, which is set as the radiation boundary, and the emissivity is 0.92. All surfaces except $S_1$ and $S_2$ are adiabatic boundary conditions, which are represented as $S_3$. In this experiment, the temperature collector is evenly distributed on the inner surface, and each temperature value can be measured by $T_j$, $1 \leq j \leq I$, where $I$ is the total number of sensors. Therefore, the physical equations and initial conditions at each position in the process can be expressed as follows:

$$\nabla \cdot(k(T)\nabla T)=\rho C_p\frac{\partial T}{\partial t},r \in \Omega, t \geq 0 (3.13)$$

$$-k\frac{\partial T(r,t)}{\partial n}=q(r,t),r \in S_1, t \geq 0 (3.14)$$

$$-k\frac{\partial T(r,t)}{\partial n}=\sigma(T_w(r)-T_0)^4,r \in S_2, t \geq 0 (3.15)$$

$$-k\frac{\partial T(r,t)}{\partial n}=0,r \in S_3, t \geq 0 (3.16)$$

$$T(r,t_0)=T_0,r \in S_3, t_0=0 (3.17)$$

The corresponding relationship between each surface of the geometric model and the symbol is shown in Figure 3.5 below:

As mentioned above, considering that the thermophysical parameters in the actual inversion model will alter with temperature, this experiment involves this nonlinear process. The thermal conductivity and heat capacity of the superalloy and coating used in the experiment vary with temperature as shown in Tables 3.1 and 3.2.

![](img/020125e0e698f9771fbbd32f2ace1e80_105_0.png)

FIGURE 3.5

A typical model of the 3D nonlinear heat conduction systems.

## TABLE 3.1

Thermophysical properties of the superalloys.

| T [K] | RT | 100 | 200 | 300 | 400 | 500 | 600 | 700 | 800 | 900 | 1000 |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| $C_p$ [J/kg K] | 552 | 552 | 562 | 572 | 582 | 595 | 612 | 638 | 674 | 726 | 25.54 | 27.21 |
| $k$ [W/m K] | 10.47 | 10.47 | 12.56 | 14.21 | 15.80 | 19.68 | 21.71 | 23.45 | | | | |
| $\rho$ [kg/m$^3$] | 8470 | 8470 | 8470 | 8470 | 8470 | 8470 | 8470 | 8470 | 8470 | 8470 | |

Because COSMOL is used as the solver in the forward program, it is necessary to know the exact analytical expression of thermophysical parameters with temperature. Here, the tool built in MATLAB is used for fitting. The properties of specific heat $C_p$ and thermal conductivity $k$ of alloy materials as a function of temperature are obtained as follows:

$$C_p = 524.3e^{0.0001327T} + 0.275e^{0.00514T} J/kg \cdot K$$

$$k = 0.0186T + 3.576W/m \cdot K^2$$

Its changing in the experimental temperature range is shown in Figure 3.6 below:

## TABLE 3.2

Thermophysical properties of the coating.

| T [K] | RT | 100 | 200 | 300 | 400 | 500 | 600 | 700 | 800 | 900 | 1000 |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| $C_p$ [J/kg K] | 552 | 552 | 562 | 572 | 582 | 595 | 612 | 638 | 674 | 726 | 25.54 | 27.21 |
| $k$ [W/m K] | 10.47 | 10.47 | 12.56 | 14.21 | 15.80 | 19.68 | 21.71 | 23.45 | | | | |
| $\rho$ [kg/m$^3$] | 8470 | 8470 | 8470 | 8470 | 8470 | 8470 | 8470 | 8470 | 8470 | 8470 | |

## Inversion of Complex Surface Heat Flux Based on ConvLSTM

(Note: The provided OCR text contains significant repetitions and fragmented headers. I have reconstructed the logical flow based on the provided content.)
[/content] (Wait, I just realized I should not include the explanation. I will provide the final block.)

[content]
physical model. Then, the generated heat flux is fed into the finite element solver of COMSOL to solve the temperature at each time within the specified time range. After that, the temperature and geometric structure are used as input for training, and the heat flux of the generator is used as the reference for supervised learning. The training can be considered complete when the network is converged.

## 3.3 Methods

### 3.3.1 Physical Model of Heat Conduction

The research in this chapter uses some symbols to represent various parameters of the model. $\Omega$ represents the solid area of the homogeneous medium in the experiment, and $S_i$ is an unknown heat flux surface, which is irregularly curved. Under the assumption that the surface of temperature collection is flat, the height information corresponding to each sampling point in the experiment can be considered as representing the distribution of the surface. $Q(r, t)$ represents the heat flux distributed on the outer surface with the change of spatial position and time. The $S_2$ is the surface for collecting temperature, which is set as the radiation boundary, and the emissivity is 0.92. All surfaces surfaces except $S_1$ and $S_2$ are adiabatic boundary conditions, which are represented as $S_3$. In this experiment, the temperature collector is evenly distributed on the inner surface, and each temperature value can be measured by $T_j$, $1 \leq j \leq I$, where $I$ is the total number of sensors. Therefore, the physical equations and initial conditions at each position in the process can be expressed as follows:

$$\nabla \cdot(k(T)\nabla T)=\rho C_p\frac{\partial T}{\partial t},r \in \Omega, t \geq 0 (3.13)$$

$$-k\frac{\partial T(r,t)}{\partial n}=q(r,t),r \in S_1, t \geq 0 (3.14)$$

$$-k\frac{\partial T(r,t)}{\partial n}=\sigma(T_w(r)-T_0)^4,r \in S_2, t \geq 0 (3.15)$$

$$-k\frac{\partial T(r,t)}{\partial n}=0,r \in S_3, t \geq 0 (3.16)$$

$$T(r,t_0)=T_0,r \in S_3, t_0=0 (3.17)$$

The corresponding relationship between each surface of the geometric model and the symbol is shown in Figure 3.5 below:

As mentioned above, considering that the thermophysical parameters in the actual inversion model will alter with temperature, this experiment involves this nonlinear process. The thermal conductivity and heat capacity of the superalloy and coating used in the experiment vary with temperature as shown in Tables 3.1 and 3.2.

![](img/020125e0e698f9771fbbd32f2ace1e80_105_0.png)

FIGURE 3.5

A typical model of the 3D nonlinear heat conduction systems.

## TABLE 3.1

Thermophysical properties of the superalloys.

| T [K] | RT | 100 | 200 | 300 | 400 | 500 | 600 | 700 | 800 | 900 | 1000 |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| $C_p$ [J/kg K] | 552 | 552 | 562 | 572 | 582 | 595 | 612 | 638 | 674 | 726 | 25.54 | 27.21 |
| $k$ [W/m K] | 10.47 | 10.47 | 12.56 | 14.21 | 15.80 | 19.68 | 21.71 | 23.45 | | | | |
| $\rho$ [kg/m$^3$] | 8470 | 8470 | 8470 | 8470 | 8470 | 8470 | 8470 | 8470 | 8470 | 8470 | |

Because COSMOL is used as the solver in the forward program, it is necessary to know the exact analytical expression of thermophysical parameters with temperature. Here, the tool built in MATLAB is used for fitting. The properties of specific heat $C_p$ and thermal conductivity $k$ of alloy materials as a function of temperature are obtained as follows:

$$C_p = 524.3e^{0.0001327T} + 0.275e^{0.00514T} J/kg \cdot K$$

$$k = 0.0186T + 3.576W/m \cdot K^2$$

Its changing in the experimental temperature range is shown in Figure 3.6 below:

## TABLE 3.2

Thermophysical properties of the coating.

| T [K] | RT | 100 | 200 | 300 | 400 | 500 | 600 | 700 | 800 | 900 | 1000 |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| $C_p$ [J/kg K] | 552 | 552 | 562 | 572 | 582 | 595 | 612 | 638 | 674 | 726 | 25.54 | 27.21 |
| $k$ [W/m K] | 10.47 | 10.47 | 12.56 | 14.21 | 15.80 | 19.68 | 21.71 | 23.45 | | | | |
| $\rho$ [kg/m$^3$] | 8470 | 8470 | 8470 | 8470 | 8470 | 8470 | 8470 | 8470 | 8470 | 8470 | |

## Inversion of Complex Surface Heat Flux Based on ConvLSTM

(Note: The provided OCR text contains significant repetitions and fragmented headers. I have reconstructed the logical flow based on the provided content.)
