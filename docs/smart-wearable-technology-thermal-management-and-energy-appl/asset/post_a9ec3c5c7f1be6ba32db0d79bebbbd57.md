
heat pump operation [14]. Additionally, the pressure level of the heat pump system is also an important property for selecting working fluid. The higher pressure should be kept below a practical value of about 25 bar, and the pressure ratio should be as low as possible [15]. HFC-245fa belongs to hydrofluorocarbon chemicals and offers zero ODP and relatively high critical temperatures of 154.0 °C at moderate pressures of 36.5 bar, which is suitable for HTHPs, so R245fa is selected as the working fluid of the high-temperature heat pump. The parameters of HFC-245fa are shown in Table 1.

![](img/c1925febd7dde400183c23c14d668ef0_190_0.png)

Figure 1. Principle diagram of the vapor injection heat pump with flash tank.

![](img/c1925febd7dde400183c23c14d668ef0_190_1.png)

Figure 2. Principle diagram of the vapor injection heat pump with sub-cooler.

Table 1. Parameters of HFC-245fa.

| Working Fluid | Chemical Formula | Group | M [g/mol] | tcr [°C] | Pcr [bar] | NBP [°C] | GWP | ODP | SG |
|---|---|---|---|---|---|---|---|---|---|
| R245fa | CHF2CH2CF3 | HFC | 134.05 | 154 | 36.5 | 15.3 | 858 | 0 | B1 |

## 3. Model Establishment

### 3.1. Assumptions and Boundary Conditions

To analyze the performance of high-temperature heat pumps with different vapor injection techniques, mathematical models are developed based on assumptions as follows:

- (1) The working fluid in the heat pump system is steady state;
- (2) The heat loss and pressure loss in heat exchangers and pipelines are ignored;
- (3) The compressor efficiencies in heat pumps are constant;
- (4) The expansion valve process is considered isenthalpic.

The reference values and the boundary conditions are shown in Table 2.

| Parameters | Reference Values | Boundary Conditions |
| :--- | :--- | :--- |
| Refrigerant mass flow rate \(\dot{m}_{ref}/(kg/s)\) | 1 | - |
| Evaporation temperature \(t_e/^\circ C\) | 55 | 40~80 |
| Superheat degree \(t_{sup}/^\circ C\) | 10 | 0~15 |
| Condensation temperature \(t_c/^\circ C\) | 125 | 100~130 |
| Subcooling degree \(t_{sub}/^\circ C\) | 5 | 0~15 |
| Injection mass flow ratio A | 0.3 | - |
| Relative injection pressure RIP | 1 | - |
| Injection superheat degree \(t_{sup,inj}/^\circ C\) | 5 | 0~20 |
| Compressor isentropic efficiency \(\eta_{is}\) | 0.72 | 0~0.9 |

### 3.2. Model Establishment

Thermodynamics models of high-temperature heat pumps with flash tank vapor injection and sub-cooler vapor injection are established based on the energy conservation equation and the mass conservation equation.

In the condenser, heat transfers from the working fluid to the heat sink and the enthalpy of the working fluid decreases while the pressure loss is slight. So, the condensation process can be considered as heat release process with constant pressure. Condensation heat can be calculated as Equation (1) with the product of working fluid mass flow rate and the inlet and outlet condenser enthalpy difference.

```
\( Q_{cond} = (1 + A) \times \dot{m}_{ref} \times (h_{cond,in} - h_{cond,out}) \) (1)
```

The expansion valve throttling process is considered as the isenthalpic process, so

```
\( h_{th,in} = h_{th,out} \) (2)
```

For the SCVI heat pump system, heat transfer takes place in the sub-cooler, so

```
\( \dot{m}_{ref} \times (h_6 - h_9) = \dot{m}_{ref} \times A \times (h_3 - h_8) \) (3)
```

For the flash tank in the FTVI heat pump system

```
\( \dot{m}_{ref} \times (1 + A) \times h_6 = \dot{m}_{ref} \times h_7 + \dot{m}_{ref} \times A \times h_3 \) (4)
```

In the evaporators of the two heat pump systems, evaporation heat can be calculated as Equation (5) with the product of working fluid mass flow rate and the inlet and outlet evaporator enthalpy difference:

```
\( Q_{evap} = \dot{m}_{ref} \times (h_{evap,out} - h_{evap,in}) \) (5)
```

In compression processes of the two cycles, processes 1–2 and 2′–4 are the adiabatic compression process, and process 3–2 can be treated as the mixing process with a constant pressure, so

```
\( h_2 = (h_{2s} - h_1) / \eta_{is} + h_1 \) (6)
```

```
\( h_4 = (h_{4s} - h_{2'}) / \eta_{is} + h_{2'} \) (7)
```

```
\( \dot{m}_{ref} \times (1 + A) \times h_{2'} = \dot{m}_{ref} \times h_2 + \dot{m}_{ref} \times A \times h_3 \) (8)
```

```
\( W_{c1} = \dot{m}_{ref}(h_2 - h_1) \) (9)
```

```
\( W_{c2} = \dot{m}_{ref} \times (1 + A) \times (h_4 - h_{2'}) \) (10)
```

W = W_{c1} + W_{c2} (11)

Injection mass flow ratio A and relative injection pressure RIP are defined as follows:

A = \frac{\dot{m}_{inj}}{\dot{m}_{ref}} (12)

RIP = \frac{P_{inj}}{\sqrt{P_{cond}P_{evap}}} (13)

The compressor discharge temperature can be calculated from the condensation pressure and refrigerant enthalpy at the compressor outlet.

t_{disch} = f(P_{cond}, h_{disch}) (14)

Most commonly, the coefficient of performance (COP) is used to evaluate the efficiency of a heat pump system. The COP is obtained from the heating capacity and the compressor power consumption, as shown in Equation (15). To compare the influence of the heating capacity and the volumetric flow rate at the suction line, the volumetric heating capacity (VHC) is calculated using Equation (16):

COP = Q_{cond} / (W_{c1} + W_{c2}) (15)

VHC = Q_{cond} / \dot{m}_{ref}v_1 (16)

## 4. Results and Discussion

Evaporation temperature, condensation temperature, compressor suction superheat degree, sub-cooling degree and compressor isentropic efficiency are the main factors that influence the performance of a high-temperature heat pump. So, the performance of a high-temperature heat pump with flash tank vapor injection and that with sub-cooler vapor injection are compared under these different main factors.

### 4.1. Performance Comparison under Different Evaporation Temperatures

Figure 3 shows the performance comparison at different evaporation temperatures of the high-temperature heat pump cycles with flash tank vapor injection and sub-cooler vapor injection. One of the important differences between the two cycles is that the refrigerant vapor injected into the compressor of the FTVC is in a saturated state, while that of the SVIC can be in either a saturated state or superheated state. Therefore, the SVIC with different injection superheat degrees are also investigated. SVIC-0, SVIC-5, SVIC-10 and SVIC-20 represent the SVIC with the injection superheat degrees of 0 °C, 5 °C, 10 °C and 20 °C, respectively. As can be seen from Figure 3a, the COP of the FTVC system is higher than the SVIC at the same evaporation temperature. At the same time, it can be seen from Figure 3a that the COP of the SVIC heat pump system decreases as the injection superheat degree increases. When the evaporation temperature and condensation temperature and injection pressure are 55 °C, 125 °C and 921.4 kPa, the system COPs corresponding to the FTVC, SVIC-0, SVIC-5, SVIC-10 and SVIC-20 are 4.49, 4.19, 4.16, 4.14 and 4.09, respectively, and the COPs of the FTVC are 6.7%, 7.3%, 7.8% and 8.9% higher than those of the systems of the SVIC-0, SVIC-5, SVIC-10 and SVIC-20, respectively. Figure 3b shows that the injection mass flow ratio decreases with the increase in evaporation temperature, which is explained by the fact that the increase in evaporation temperature leads to the decrease in pressure difference between the condensation pressure and injection pressure. It can also be seen from Figure 3b that the injection mass flow ratio of the FTVC is higher than those of the SVIC under different injection superheat degrees, which causes the higher COP of the FTVC than that of the SVIC under the same injection pressure. At the evaporation temperature of 55 °C, condensation temperature of 125 °C and injection pressure of 921.4 kPa, the injection mass flow ratio of the FTVC is 18.6%, 23.6%, 28.0% and 35.2% higher than the SVIC-0, SVIC-5, SVIC-10 and SVIC-20, respectively. Figure 3c shows that the volumetric heating capacity of the FTVC is also higher than those of the SVIC at different injection superheat degrees. When the evaporation temperature, the condensation temperature and injection pressure are 55 °C, 125 °C and 921.4 kPa, the VHCs of the FTVC, SVIC-0, SVIC-5, SVIC-10 and SVIC-20 are 3976, 3714, 3710, 3706 and 3699 kJ/m³, respectively. Figure 3d shows the discharge temperature of different systems at different evaporation temperatures. According to Figure 3d, the FTVC and SVIC-0 have equivalent discharge temperatures at different evaporation temperatures. When the evaporation temperature and the injection superheat degree increase, the discharge temperature increases.

![](img/c1925febd7dde400183c23c14d668ef0_193_0.png)

![](img/c1925febd7dde400183c23c14d668ef0_193_1.png)

![](img/c1925febd7dde400183c23c14d668ef0_193_2.png)

![](img/c1925febd7dde400183c23c14d668ef0_193_3.png)

Figure 3. Performance comparison under different evaporation temperatures.

### 4.2. Performance Comparison under Different Condensation Temperatures

Figure 4 shows the performance comparison of the FTVC and SVIC at different condensation temperatures. From Figure 4a, it can be seen that at the same injection pressure and condensation temperature, the COP of the FTVC system is always higher than those of the SVIC with different injection superheat degrees. The higher condensation temperature leads to the larger COP difference between the FTVC system and the SVIC system. At the evaporation temperature of 55 °C, condensation temperature of 100 °C, compressor suction superheat degree and condensation subcooling degree of 5 °C, COPs corresponding to the FTVC, SVIC-0, SVIC-5, SVIC-10, and SVIC-20 are 6.15, 5.93, 5.92, 5.90 and 5.88, respectively. COP of the FTVC is 3.7%, 3.9%, 4.2% and 4.6% higher than those of the SVIC-0, SVIC-5, SVIC-10, and SVIC-20, respectively. When the condensation temperature is 130 °C and the other conditions are kept the same, COP of the FTVC is 7.9%, 8.9%, 9.8% and 11.3% higher than those of the SVIC-0, SVIC-5, SVIC-10 and SVIC-20, respectively. According to Figure 4b, the injection mass flow ratio increases with the increase in condensation temperature. The main reason is that as the condensation temperature increases, the pressure difference between the condensation pressure and the injection pressure increases, causing the injection vapor mass flow rate to increase. At
