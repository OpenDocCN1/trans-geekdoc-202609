| | HackRF | bladeRF x115 | USRP B200 |
|---|---|---|---|
| Operating Frequency | 1 MHz to 6 GHz | 300 MHz to 3.8 GHz | 70 MHz to 6 GHz |
| Bandwidth | 20 MHz (6 GHz) | 28 MHz (124 MHz) | 56 MHz |
| Duplex | Half | Full | Full |
| Bus | USB 2 | USB 3 | USB 3 |
| ADC Resolution | 8 bit | 12 bit | 12 bit |
| Samples per Second | 20 MSps (Million Samples per second) | 40 MSps | 61 MSps (122 MSps) |
| Approximate Cost | $300 | $650 | $745 |

Table 5-1 Comparison of Affordable SDR

The operating frequency determines what frequencies the radio can tune to. For example, Bluetooth operates between 2.4 GHz and 2.48 GHz over 40 to 80 channels, depending on the version. FM radio operates between 87.8 MHz and 108 MHz over 101 channels. Although the bladeRF operating frequency is significantly smaller than the other two devices, add-on boards can effectively drop the low frequency to 60 KHz. (I am unaware of any add-on board to increase the upper limit of the bladeRF.) Add-ons are also available for HackRF and USRP B200 that effectively lower their lower limits.

The bandwidth is the amount of the RF spectrum that can be scanned by the application/device. The listed bandwidths are published on the respective websites, but may differ depending on the firmware loaded. For example, HackRF firmware version 2017.02.01 now supports a sweep mode that allows the device to sweep over the full 6 GHz range. Support is added to bladeRF to extend its bandwidth to 124 MHz. One potential benefit of the increased bandwidth is the ability to monitor all channels of Bluetooth simultaneously (80 MHz).

Duplex refers to how two systems can communicate with one another. Full duplex means that the device can both transmit and receive simultaneously. Half duplex, as you have no doubt guessed, means that the device can transmit and receive data, but not at the same time. Examples of half-duplex communications are walkie-talkies and many computer Voice over IP applications. When both parties attempt to speak at the same time, collisions occur and data is lost. Although full duplex is more flexible, the duplex of SDR will likely not hinder the effectiveness of the analysis.

Analog-to-digital conversion (ADC) resolution refers to the number of distinct voltage values each sample can take on. For example, an 8-bit ADC with a voltage range of 4V has a resolution of 15.6 mV, or 0.39 percent. In combination with the sampling rate, more bits of ADC resolution result in a more accurate digital representation of the analog signal.

The published samples per second are dependent on the USB throughput, the CPU, the