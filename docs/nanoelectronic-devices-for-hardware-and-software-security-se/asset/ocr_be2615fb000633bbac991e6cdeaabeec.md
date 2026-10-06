# 1 Emerging Nanoelectronic Devices 19

![](bbox=[0.258, 0.085, 0.715, 0.375])

FIGURE 1.14 Increase in leakage current with each step of threshold voltage scaling [39].

Therefore, device-level solutions such as small swing devices were needed. In the subthreshold region, the rate of increases for an increase in gate voltage depends on the Fermi-Dirac function, given by f(E) = 1/(1+e((E-E_F)/kT)). This function limits the MOSFET subthreshold current by a factor of kTIq. The equation of current for MOSFET in the subthreshold region is given by equation (1.5).

> I- e'(V_OS - Vₜ) / (m * (kT/q)) (1.5)

The subthreshold swing SS (dV_D/d log ID) derived from this equation comes out to be in form ln(10)/(mTIq). Whereas 'm' is the body coefficient, the value of 1+(C_dm/C_cox). COX is the oxide capacitance, and C_dm is the body capacitance at threshold. For C_dm << C_cox, m is marginally higher than 1, which makes least value of SS = 60 mV/dec for MOSFET.

# 1.7.2 Ion ionization MOS

As explained, the subthreshold swing in the MOSFET is knotted down by the physical phenomenon that produces current in the MOSFET in subthreshold mode. For smaller SS, we need to change the physical mechanism for current generation. The impact ionization MOS (IMOS) is is gated p-i-n device where the gate is underlapped from a junction and overlapped from the other side [40]. Avalanche breakdown occurs in the intrinsic region at the non-gated portion, as a very high electric field is present in that region, shown in Figure 1.15. This leads to very low subthreshold swing and larger, ION of the device. But there are many issues pertaining to IMOS such as scalability, low-voltage operation, and hot carrier degradation that need to be addressed.

# 1.7.3 MEMS and NEMS

The other type of small swing device is an electromechanical device on a micron scale (MEMS) or nanometer scale (NEMS). There are 2-terminal MEMS that retain exceptionally low swing value but have restricted applications for circuits. The 3-terminal MEMS have the capability to replace MOSFETs.