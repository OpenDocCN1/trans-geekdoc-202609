# 18 Nanoelectronic Devices for Security

device is taken at 0.1 nm in the vertical or y-axis across the silicon thickness and 0.5 nm in the horizontal x-axis from the source side of the gate to the drain. This mesh is used to capture the phenomenon of tunneling for low gate voltages or Off-state. The cutlines are at 0.5 nm from the insulator-semiconductor interface, as used in [37]. The surface state density value at the interface boundaries has the default concentration of the Silvaco simulator, is, ~10. The tunneling masses of 0.60 m_, for holes and 0.40 m_, for electrons are used for JAMFET, set by Sahay et al. [24]. For DLT, the simulation setup was calibrated according to [15]. The tunneling masses of m_e = m_h = 0.65 m_ were taken as as reported by Sindhu et al. [23].

# 1.7 STEEP SLOPE DEVICES

# 1.7.1 Limitations in CMOS

R. Dennard had a proposed scaling in 1974 that explained how to scale the device dimensions by keeping the electric fields nearly although this law worked correctly until the 1.4 µm node, afterwards it became inaccurate. The reason behind this was the inability of threshold voltage to scale down with supply voltage scaling. The required scaling of threshold voltage did not happen, because when the scaling laws were correctly applied, they kept the electric fields constant, which consequently kept the threshold voltage constant. This led to reduction in gate overdrive, as the supply voltage was continuously scaled down, as shown in Figure 1.13. The power consumption had increased severely, as both the static and dynamic power depended on supply voltage (VD). The other option of scaling threshold voltage depended on the device behavior of the MOSFET. The least subthreshold swing of the conventional MOSFET was fixed at 60 mV/dec, the only option to decrease Vth was to move the ID-VGS curves horizontally. For a shift of ID-Vth, the penalty is one decade of Off-state current. This also led to serious issues of leakage current in scaling devices, shown in Figure 1.14. Many circuit level solutions such as sleep transistors, dual-Vth circuits, stacked transistors, and multiprocess were proposed to solve this problem. All of them were not highly effective, as they had their consequences.

![](bbox=[0.265, 0.545, 0.735, 0.893])

FIGURE 1.13 Decrease in the gate overdrive voltage (VGS-Vth) with scaling [38].