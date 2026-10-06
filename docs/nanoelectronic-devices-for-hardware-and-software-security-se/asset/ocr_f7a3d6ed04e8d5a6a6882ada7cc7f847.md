# 6 • Memristor 133

suggest the algorithms and tamper with the data [46]. There is also a possibility of side-channel attacks, as it may retrieve the security key by observing the side-channel contents like timing and power. Along with the security issue, this cryptographic technique also results in huge power consumption and size overhead. To resolve this issue, researchers have suggested encryption utilizing nanoelectronic devices. The sneak path encryption (SPE) technique is mostly referred for creating secure NVMM (SNVMM).

# 6.6.1 Architecture Memristor-Based Cryptography

There are four main part of this architecture:

+   - a. Processor memory.
- b. Cache memory.
- c. Sneak path encryption control unit (SPECU).
- d. SNVMM/NVMM.

Two-level memory architecture was proposed by S. Kannan et al. in 2014 [47]. The processor and cache memory operate on unencrypted data. The cache memory is divided into two levels, Level 1 and Level 2. The SPECU is just below the Level 2 cache before NVMM. The data stored in NVMM is encrypted, and the sneak path encryption of this data is controlled by SPECU [48]. The SPECU architecture and modified NVMM are shown in Figure 6.11. The SNVMM mainly consists of a crossbar, row decoder, column decoder, and transistor control unit. The crossbar is similar to that of Figure 6.3; the only difference is that each cross-point in the crossbar has an additional transistor along with the memristor. These transistors are used to regulate voltage, causing the memristor to change its resistance value [49]. This transistor control unit enables or disables the selected memristor across which the connected memristor is referred to as the point of encryption (PoE).

![](bbox=[0.079, 0.553, 0.922, 0.903])