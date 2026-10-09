
![](img/ff55c581d8704d3a62714cacfc830da5_45_0.png)

**Figure 2.6** Basic radar schematic diagram.

## 2.11 Frequency Modulation Radar

Microwaves often travel in waveguides, which are rectangular-shaped metal pipes. Since the loss is small when microwaves travel in air, high-power microwaves can cause the air to break down inside the waveguide, which is equivalent to a short circuit. To avoid this problem, different kinds of gas rather than air, or even liquid, can be used to fill the waveguide. Either way, this kind of system is difficult to maintain because keeping the gas or liquid from leaking through the waveguide is another problem to deal with.

An alternative solution to this problem is to reduce the peak transmitted microwave power and increase the pulse width to maintain the total energy. One way to achieve this goal is to use a frequency modulated (FM) signal. The frequency of an FM signal can start with a low frequency and end with a high frequency. At the receiver side, a device called a dispersive delay line is used to handle the FM signal. The delay time of the dispersive delay line is frequency dependent. In this case, the delay time is long for the low frequency and short for the high frequency. If the FM signal passes through the line, the signal can be compressed into a short pulse because the low frequency part takes longer time and the high frequency part takes shorter time, and they come out of the line at the same time. Therefore, the difficulty of generating and transmitting short pulse signals with high power can be overcome. The difference between starting and ending frequencies (known as bandwidth) and the pulse width can be used to calculate the processing gain. If the pulse width is $100 \mu s$ and the frequency bandwidth is $100 MHz$, the product of these two quantities is $100 \times 10^{-6} \times 100 \times 10^{-6} = 10^4$, and this number is the processing gain. This quantity is also referred to as the time-bandwidth product. Since a continuous wave (i.e., a microwave with a fixed frequency) has zero bandwidth, it has no processing gain.

This kind of radar must have a wide bandwidth to process the signal, and that is the price one has to pay.

## 2.12 Searching Radar

As explained in Section 2.5, the skin return can be very weak compared to the transmitted signal, so the radar antenna must have a very high gain to increase the received signal strength. Also, as described in Section 2.10, the radar uses the same antenna to transmit and receive signals.

If the antenna is omni-directional, it can detect targets in all directions instantly. However, the gain of this antenna is 1 (or we can say that it has identical gain in every direction). An antenna gain is often represented in decibels (dB) and the decibel value is calculated as:

$$dB = 10\log_{10}(Gain) \quad (2.4)$$

If the gain of an antenna is 1, we can also say its gain is 0 dB. When the antenna is omni-directional, if a target is detected, the direction of the target cannot be determined as the reflected signal can be from any direction.

To solve this ambiguity, instead of an omni-directional antenna, a directional antenna might be used. A radiation pattern of a directional antenna which has a main beam (main lobe) and side lobes is shown in Figure 2.7. The main beam of the antenna is the area where the transmitted/received signal receives maximum amplification. When a directional antenna is used in a radar system, the radar mainly looks for objects in the main beam. The side lobe is the area where signals are still transmitted or received, but the amplification the signal receives is much weaker.

One might want to use a high-gain directional antenna for a radar system. If a target is detected, the position of the target can be easily determined because the target is in the direction of the antenna's main beam. However, this arrangement can be difficult to use for detecting a target because the antenna gain and size of the main beam are related, and higher gain means a narrower main beam. The chance of hitting a target using a microwave signal with a very narrow main beam is, of course, small.

![](img/ff55c581d8704d3a62714cacfc830da5_46_0.png)

**Figure 2.7** Radiation pattern of a directional antenna.

The compromised approach is to use an antenna with medium gain and covering a reasonable angle. For example, a common approach is to create a vertical fan-shaped beam. The beam is narrow in the azimuth direction and wide in the elevation direction. To form this type of beam, the antenna will be wide in the horizontal direction but short in the elevation direction as shown in Figure 2.8. The beam shown in Figure 2.8 is called the fan beam, and a beam that is narrow in both azimuth and elevation directions is referred to as the pencil beam. This antenna will rotate in the horizontal direction. If a target is detected, the azimuth angle is known. The elevation can be found from a different antenna directed in the desired azimuth direction.

![](img/ff55c581d8704d3a62714cacfc830da5_47_0.png)

**Figure 2.8** An antenna generating a vertical fan-shaped beam.

The returned signal is displayed on a cathode ray tube in polar coordinates. The location of the radar is at the center. A radiation line is rotating around the center. Detected targets are shown as bright points on the display. The target's azimuth angle and distance can be determined by its coordinate on the display. Figure 2.9 shows an example of the display.

## 2.13 Conical Scan Radar [10]

Once a target is found, its detailed information including target's position and velocity are needed. The type of radar gathering such information can be referred to as the tracking radar. The searching radar described in Section 2.12 can provide the position of a target. The target's velocity can be determined from the history of the reflected signals. For example, the target’s velocity can be estimated via dividing the change in target position between two specific scans by the time interval between these two scans. Different approaches can be used to improve measurement accuracy, and some of them will be introduced in the following sections. First, let us discuss the conical scan radar.

![](img/ff55c581d8704d3a62714cacfc830da5_48_0.png)

**Figure 2.9** A radar screen. (https://static5.depositphotos.com/1000134/471/i/950/depositphotos_4713955-stock-photo-radar-screen.jpg).

The conical scan radar is used to find the accurate direction of the target and keep tracking it. Its antennas are usually horn-shaped. They are made of a rectangular waveguide and the dimensions of the waveguide increase into a rectangular horn, as shown in Figure 2.10. The conical scan radar’s signal beam is slightly off center from its antenna's midline and continuously rotates around it (scan). If the target is roughly at the boresight of the conical scan radar's antenna, the signal beam from the antenna makes a conical cone around the target, as shown in Figure 2.11. If the target is at the center of the cone, the reflected signal is strong and has constant magnitude during the rotation. If the received signal does not have constant amplitude during the rotation, the target is not at the center of the cone. An error signal is then generated to adjust the direction of the antenna. This approach can improve the accuracy of the direction measurement.

![](img/ff55c581d8704d3a62714cacfc830da5_48_1.png)

**Figure 2.10** A rectangular horn antenna.

## 2.14 Monopulse Radar

This type of radar usually uses four horn antennas to transmit and receive four signals. In order to explain this idea, a system with two antennas is used for illustration. In this specific case, two antennas emit two signals. The two antennas point at slightly different directions. The reflected signals are summed together to obtain the sum channel. Their difference is also obtained as the difference channel. If the target is in the middle of these two beams, the sum channel will have the maximum output and the difference channel should have the minimum output. The outputs of the sum and difference channels are shown in Figure 2.12. The sum channel provides the coarse information about target direction and the difference channel provides the fine information. The output of the difference channel can be used to control the antenna's direction.

In the system of two antennas, the difference channel can only be used to adjust the two antennas in one direction such as in the azimuth direction. If four channels are used, the antennas can move in both the azimuth and elevation directions. Figure 2.13 shows the arrangement of four horn antennas. The channels A and C can be summed and B and D can be summed. Their output (A+C) and (B+D) can be considered as two channels to move antennas
