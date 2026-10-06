# 154 Nanoelectronic Devices for Security

This randomness of powering up will produce stable states (1 or 0) for every available SRAM cell independently of each other. An individual SRAM cell will latch to the same condition for every power-up with high probability. Provided that every SRAM cell has its preferred form when it is driven, the SRAM response yields a unique and random sequence of zeros and ones. This pattern is like the fingerprint of a chip because it is unique to a certain SRAM.

Since the SRAM PUF can be attached directly to the general circuitry implemented on the same hardware, these PUFs are instantly installed in cryogenic applications as a hardware device, presenting themselves as a perfect candidate for security solutions. One may regard many locations within an SRAM memory block as a task for SRAM-PUFs. A further advantage of the PUF is that a stream of 0 or 1 is produced at the output when presented with a challenge. To obtain a stream from other PUF implementations, a lengthy analog to digital conversion process must be followed.

# 7.7.5 Memory-Based Intrinsic PUFs

At the time of manufacturing, the APUF circuit is not embedded in a hardware device and is not considered an intrinsic PUF. Because of this, to design an APUF, we require additional layout and design steps. However, an SRAM PUF is deemed to be an intrinsic PUF and was introduced in 2007.

The SRAM cell address within the schematic is treated as a challenge, and the response is derived from its power-up state (Figure 7.16). Due to their pervasiveness in electronic products, DRAM PUFs, SRAM PUFs, and flash memory-based PUFs are more convenient in practice [39, 40]. However, the primary limitation of a memory-based PUF is that its challenge-response pair size is limited and, therefore, cannot be used in public CRP-based authentication applications. Simultaneously, its application in the generation of an on-demand volatile cryptographic key is a direct consequence of its preferred random address response bits.

# 7.7.6 Other Memory-Based PUFs

The definition of the butterfly PUF was suggested in the literature [41]. In the FPGA matrix, structures are constructed such that they mimic the behavior of the startup process of an SRAM cell. Using the latches accessible in the FPGA matrix, a cross-coupled fusion is utilized. This design causes excitation

![](bbox=[0.285, 0.665, 0.715, 0.89])

FIGURE 7.16 Bistable memory elements based on various PUF designs.