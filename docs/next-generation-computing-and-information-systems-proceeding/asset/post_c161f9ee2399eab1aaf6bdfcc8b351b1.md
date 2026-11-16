
Clustering can be utilized in these networks to mitigate these detrimental consequences. Moving autos in the same direction are regarded as part of a cluster. It mitigates the harmful impact of recurrent clustering. This essay considers the link between the size of the cluster, speed of the vehicle, traffic, and the CW’s size on the hand and their influence on output efficiency and closure losses. Another issue in creating such networks is selecting the appropriate cluster.

This procedure was used to choose the cluster based on the weighted method. Furthermore, the average signal strength received according to Friis’ rule is recognized throughout the preceding experiments (1).

$$
E(p_{re}) = \frac{P_{tr}G_{tr}G_{re}\lambda_c^2}{16\pi^2 d^2} \tag{1}
$$

In this regard, d denotes the distance of the transmitter with the receiver, as well as Ptr, Gtr, and Gre of the transmitter and reception antennas (previously specified). Equation will be used to calculate the wavelength of the wireless signal (2).

$$
\lambda_c = \frac{c}{f} \tag{2}
$$

(2) denotes the speed of light as c and the frequency of the wireless channel as f (5.850 GHz to 5.926 GHz), with one channel especially tailored to boost automobile safety and other channels for car-specific applications. To simplify, we’ll suppose the frequency is in the 5.890 GHz range. Regarding the channel considerations, the probability density function can be computed as below for the delivered signal:

$$
F_{re}(p_{re}) = \frac{1}{E(p_{re})} e^{-\frac{p_{re}}{E(p_{re})}} \tag{3}
$$

The emergency message is decrypted if the received signal intensity is higher than the lowest sensitivity (P_{min}). If this is not done, emergency communication will be lost (Yao et al. 2021). The receiver calculates the signal intensity when the emergency message is received. Consequently, the possibility of receiving an emergency message within the distance L_{tr} is calculated using the equation (4).

$$
pr_{succ(d)} = pr\{p_{re} > p_{min} | l_{ir} = d\} = 1 - pr\{p_{re} \le p_{min} | l_{ir} = d\}
= 1 - \int_{0}^{p_{min}} \frac{1}{E(p_{re})} e^{-\frac{p_{re}}{E(p_{re})}} d(p_{re}) = \exp \left[ -\frac{p_{min}}{E(p_{re})} \right]
$$

Even though the processing units placed in automobiles are capable, this cannot eliminate the delay caused by vehicle propagation since wireless networks’ limited resources produce this delay. As a result, the emission delay (T_{tr}) is the time elapsed between back-off and retransmission in the MAC layer.

According to the equation, the unscreened applicants’ number for channel access is determined as N_c if an automobile plans to transmit an emergency message.

$$
N_c = n\tau + 1 \tag{4}
$$

Back-off is meant to avoid interference when autos issue emergency notifications. The forwarding probability of the collision.

In this equation, w_{min} denotes the least conceivable CW size, which is often believed to be 32. The average number of transmitted entries will be specified in the equation concerning the maximum transmitting value (l_{re})

$$
E(N) = \sum_{N=1}^{l_w} N \left(1 - Pr_{r_0}^N \right)^{N-1} Pr_{r_0} \tag{5}
$$

CW doubles its maximum value \( w_{max} = 2^m w_{min} \), if there is no interference channel. Assume a system parameter, which is presumed to be 5 in this case. As \( w_{con} \) approaches its maximum value of \( w_{max} m + 1 \), the CW will be used as the maximum in the following computations. As a result, the equation defines the average latency for a successful post \( \eta \) represents the back-off slots’ length. The data transmission length (\( T_{data} \)) is defined as the product of the packet’s size message (\( L_{size} \)) and the data transfer rate (\( M \)) and can be calculated as equation (9).

$$
T_{data} = \frac{L_{size}}{M} \tag{6}
$$

Combining equations, in the form of equation (7).

$$
T_{trs} = T_{back} + \frac{L_{size}}{M} \tag{7}
$$

In this part, a parameter called M* will be added to define the relay node in the cluster to link the nodes inside the cluster to each other. The capabilities of Neighbor and Node Relay will be fully utilized. The maximum delay of \( T_{max} \) is 100 ms based on the reference number. Also, to compute the delay factor in one step, the parameter \( D^* \) is introduced that has a symmetrical connection with the \( T_{tr} \) emission delay variable. Thus, if \( T_{tr} \) is 0, \( D^* \) will be 1, and vice versa. The minor \( D^* \), the larger the delayed \( T_n \) release. As a result, in general, the parameter \( D^* \) will be specified by equation (8).

$$
D^* = \begin{cases} 0; T_{tr} > T_{max} \\ 1 - \frac{T_{tr}}{T_{max}}; else \end{cases} \tag{8}
$$

The parameter \( D^* \) will have a value between 0 and 1. Furthermore, suppose the \( T_{tr} \) diffusion delay in one phase is more significant than \( T_{max} \). In that case, \( D^* \) will be 0, the worst-case situation. The parameter value \( M*\alpha \) and \( \beta \) indicate the propagation’s reliability and latency properties. The parameter \( M* \)’s of changes is similarly between 0 and 1.

## 4 SIMULATION AND RESULTS

The problem of capturing vehicle distances and speeds on straight and steep mountain bumps must be solved (Jairath et al. 2022; Lei et al. 2022). It is determining traffic bottlenecks, traffic, and any accidents over high terrain is difficult since it looks like a series of amplifiers are necessary. Specifying the Smart City’s first parameters with the Internet of Things setup and infrastructure is required. Table 3 depicts the starting parameters of a Smart City with the Internet of Things setup and infrastructure, as specified by a reference paper in this field (Rida et al. 2015).

Table 3. Smart city with internet of things configuration and infrastructure parameters.

| Network Dimension | 500 × 500 m² or 1000 × 1000 m² |
| :--- | :--- |
| Each packet’s size | 1000 byte |
| Numbers of Vehicles | 300 |
| Cars with the slowest speeds (in mountainous roads) | 30.0 km/h |
| Cars with the slowest speeds (in tunnels) | 25.0 km/h |
| The range of each vehicle’s radio signal | 20 m |
| The energy of each vehicle’s sender | 0.02 J |
| The energy received by each vehicle | 0.04 J |
| Per-second fuel usage | 2 sec |
| Network port count | 4000 |
| Paths' lengths | 5.0 m |
| Modulation Diagram | OFDM |
| Data transmission power | 21 dB |
| Transfer speed | 6 MB/s |

OFDM channels use QPSK and 64QAM in the roads and tunnels, respectively. At first, PDR will be shown. PDR is calculated by equation (9).

```
PacketDrop_{Calculation} = \frac{SentPacket\_Number}{ReceivedPacket\_Number} \quad (9)
```

i is the index of summation according to the above two relations. When network resources are shared, the outcome reveals a high rate of PDR. PDR is evaluated at zero intervals just one vehicle is in the covered zone and resources (simulation start). This does not imply that the PDR will be assessed just for an automobile, even if a car fills the area (Abbas et al. 2021; Rida et al. 2014). The equation calculates the average end-to-end latency.

```
n - to - n_{delay} = \frac{decrease\ in\ delay}{4}, \quad unit = ms \quad (10)
```

The simulation's throughput is determined depending on runtime, input condition, and vehicle unavailability to the network coverage region. Average throughput computed using equation (4.4).

```
Throughput_{Avg} = \left( \sum_{i=1}^{4} \frac{ReceivedPacket_{Number} \times PacketSize}{Total\ Simulation\ Time} \right) \times 100 \quad (11)
```

According to an analysis, the ID 1 vehicle was withdrawn from the envelope in 1.1 seconds, whereas the vehicle with ID 2 began sending data in 20 seconds. The results of two-time delays demonstrate a significant decrease in bit rate. The outcomes are as follows: The protocol's delivery and data loss rates were compared to AODV and AOMDV, before a recommended technique, SPA-(S, P), was implemented for enhanced resilience in each segment (Javed et al. 2018; Mazhar et al. 2023).

The suggested technique has a higher packet delivery rate than AODV and AOMDV protocols and is more suited to packet loss rates. As a result, the permeability is comparatively more elevated, and data transmission and reception are faster (Mazhar et al. 2023). A sustained routing comparison is presented in the Figure below (2).

![](img/9eefc6d2972274efeb1680c6a31895e5_79_0.png)

Figure 2. A comparison of routing stability.

This section has been added in the OFDM channels, the modulation type is separated into two parts: The figure shows a bit error rate (Figure 3).
