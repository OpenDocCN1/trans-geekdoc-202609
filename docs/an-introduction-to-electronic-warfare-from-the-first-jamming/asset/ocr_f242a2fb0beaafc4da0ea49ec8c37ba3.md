This kind of radar must have a wide bandwidth to process the signal and that is the price one has to pay.

# **2.12 Searching Radar**

As explained in Section 2.5, the skin return can be very weak compared to the transmitted signal, so the radar antenna must have a very high gain to increase the received signal strength. Also, as described in Section 2.10, the radar uses the same antenna to transmit and receive signals.

If the antenna is omni-directional, it can detect targets in all directions instantly. However, the gain of this antenna is 1 (or we can say that it has identical gain in every direction). An antenna gain is often represented in decibels (dB) and the decibel value is calculated as

$dB = 10\log_{10}(Gain)$. (2.4)

If the gain of an antenna is 1, we can also say its gain is 0 dB. When the antenna is omni-directional, if a target is detected, the direction of the target cannot be determined as the reflected signal can be from any direction.

To solve this ambiguity, instead of an omni-directional antenna, a directional antenna might be used. A radiation pattern of a directional antenna which has a main beam (main lobe) and side lobes is shown in Figure 2.7. The main beam of antenna is the area where transmitted/received signal receives maximum amplification. When a directional antenna is used in a radar system, the radar mainly looks for objects in the main beam. The side lobe is the area where signals are still transmitted or received, but the amplification signal receives is much weaker.

One might want to use a high gain directional antenna for a radar system. If a target is detected, the position of the target can be easily determined

![](bbox=[0.2, 0.66, 0.8, 0.86])

**Figure 2.7** Radiation pattern of a directional antenna.