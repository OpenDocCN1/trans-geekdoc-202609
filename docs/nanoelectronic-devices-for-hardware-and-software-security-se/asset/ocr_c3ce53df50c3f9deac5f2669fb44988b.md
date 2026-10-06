reconfiguration without altering the overall structure of a PUF circuit is still considered a desirable feature for crucial applications such as revocation and regeneration.

# 7.6.4 Erasable PUFs

The erasable PUF design is motivated by a reconfigurable PUF design. In an RPUF, each CRP is refreshed independently, and such a system is not a strong PUF [24]. The erasable PUF's CRP can be independently refreshed or reconfigured, which makes it a strong PUF and robust against most reuse attack. A SHIC-PUF-based first erasable PUF design was proposed in 2011 and appreciated [25]. However, this wide range of uses and hence more versatile than an exclusive reconfigurable system is still plagued by many flaws, and the development of an inexpensive and functional erasable PUF continues to be a significant field of study.

# 7.6.5 Novel Architectures

In addition to traditional architecture, novel PUF architectures have been proposed, including transient ring oscillator (TERO) PUFs (Figure 7.8). The basic building block of the TERO PUF [26] is the TERO cell, which is characterized by a stable state and a transient oscillating state. It can be thought of as a RO PUF. An RSlatch used in TERO PUFs, and the circuit starts oscillating, setting the initial signal to one for short period.

The public PUF (PPU) is an alternative development of arbiter PUFs that utilizes XORs. PPU systems have good effectiveness, side-channel attacks immunity, and low power utilization and potential candidates for general key protocol implementations for the IoT [28]. PUFs and arbiter PUFs based on hybrid ring oscillators are also recently proposed PUF architectures suitable for use in IoT applications. They have reported low power consumption, making them powerful candidate for battery-powered IoT devices. PPPFs are yet another evolution of PUF arbiters. PUFs based on the current array are also designed to withstand machine learning attacks and have been reported in the literature [29, 30].

TABLE 7.1 Desirable PUF Properties in Various PUF Architectures

| PROPERTIES OF VARIOUS PUF | OPTICAL PUF | ARBITER PUF | RING OSCILLATOR PUF | SRAM PUF | LATCH PUF | BUTTERFLY PUF |
|--- | :---: | :---: | :---: | :---: | :---: | :---: |
| Uniqueness | ✓ | | | | | | |
| Reproducibility | | ✓ | | | | | |
| Physically Unclonable | | | ✓ | | ✓ | ✓ |
| Unpredictability | ✓ | | | | ✓ | ✓ |

![](bbox=[0.205, 0.805, 0.735, 0.915])

FIGURE 7.8 TERO PUF architecture [27].