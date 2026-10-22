is

$$W_3 = Q_C = -R T_{\text{cold}} \ln\left(\frac{V_4}{V_3}\right)\tag{2.164}$$

+   - Step #4 is diabatic, reversible compression from $V_4$ back to $V_1$. Because work is done in compressing the gas with the piston, the temperature of the gas must increase from $T_{\text{cold}}$ back to $T_{\text{hot}}$. The system (i.e., the gas in the cylinder and the piston) is restored to its original state. Because this step is adiabatic and reversible, the work is

$$W_4 = \Delta U_4 = -c_V \left(T_{\text{cold}} - T_{\text{hot}}\right).\tag{2.165}$$

Because steps #1 and #3 are adiabatic and reversible, the volume changes are related by

$$\left(\frac{T_{\text{cold}}}{T_{\text{hot}}}\right)^{c_V} = \left(\frac{V_2}{V_3}\right)^{R}\quad\text{and}\quad\left(\frac{T_{\text{hot}}}{T_{\text{cold}}}\right)^{c_V} = \left(\frac{V_4}{V_1}\right)^{R}$$

or

$$\frac{V_1}{V_2} = \frac{V_4}{V_3}.\tag{2.166}$$

By using (2.166), the net work is

$$W = W_1 + W_2 + W_3 + W_4 = -R\left(T_{\text{hot}} - T_{\text{cold}}\right)\ln\left(\frac{V_2}{V_1}\right)\tag{2.167}$$

and the engine efficiency, as defined in (2.161), is

$$\eta_{\text{carnot}} = \frac{W}{Q_H} = \frac{-R\left(T_{\text{hot}} - T_{\text{cold}}\right)\ln\left(V_2/V_1\right)}{-R T_{\text{hot}}\ln\left(V_2/V_1\right)} = \frac{T_{\text{hot}} - T_{\text{cold}}}{T_{\text{hot}}}\tag{2.168}$$

or

$$\eta_{\text{carnot}} = 1 - \frac{|Q_C|}{|Q_H|} = 1 - \frac{R T_{\text{cold}}\ln\left(V_2/V_1\right)}{R T_{\text{hot}}\ln\left(V_2/V_1\right)} = 1 - \frac{T_{\text{cold}}}{T_{\text{hot}}},\tag{2.169}$$

where $T_{\text{hot}}$ and $T_{\text{cold}}$ are in Kelvin, respectively. Efficiency is zero if $T_{\text{hot}} = T_{\text{cold}}$ and 100 percent only if $T_{\text{cold}} = 0$ Kelvin. Because such reservoirs are not available, $T_{\text{hot}} > T_{\text{cold}}$ and $T_{\text{cold}} \neq 0$ Kelvin, 100 percent efficiency cannot be achieved. In most practical cases, $T_{\text{cold}}$ is near room temperature, 300 K. Moreover, no real heat engine operating between two energy reservoirs can be more efficient than a Carnot engine operating between the same two reservoirs.

**Quiz:** An engine transfers $2 \times 10^3$ J of energy from a hot reservoir during a cycle and transfers $1.5 \times 10^3$ J to a cold reservoir. (1) Find the efficiency of the engine. (2) How much work does the engine do in one cycle?