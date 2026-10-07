
a desirable result for some situations, our initial tests on the performance show that the optimization pressure exerted by this objective increases the use of higher-order modulations. This effect helps trade off the solution space between low BER modulations and high data rate modulations. We prefer to keep the objectives as separate as possible in order to easily adjust selection pressure depending on QoS requirements. In the implementation, we currently use a simplified version of the throughput calculation that only relies on the raw data rate. This objective can be paired with the BER objective in different ratios to provide a proper balance. Equation (4.20) shows the simple throughput objective.

```
$$R_{th} = kR_s = R_b \quad (bps) \quad (4.20)$$
```

## 4.2.7 Power

### Dependencies

Knobs: Transmit power

Meters: none

Objectives: none

### Definitions

$P_T = \text{transmit power} (dBm)$

There are two ways to look at power as a resource. The first way is to think about power in terms of how the radio transmitter uses the external power in the spectrum. In this manner of speaking, power is a shared resource by all radio nodes, so radios should strive to reduce their transmission power. This objective balances efforts to reduce BER or maximize SINR. The transmitted power we use refers to the power of the signal sent to the antenna. In all of the calculations here, though, we have assumed EIRP such as when calculating the received power for the BER equations. In these calculations, we assume a 0-dB gain antenna, so the two are the same. The assumption is based on the lack of the antenna as a knob or even a parameter in the current analysis. In a more developed system that has a static antenna gain or a smart antenna capable of doing beamforming, the antenna gain would be used here to add to the transmit power as well as in the BER equations to calculate the EIRP.

## 4.2.8 Computational Complexity

### Dependencies

Knobs: modulation type, symbol rate

Meters: none

Objectives: none

### Definitions

$k =$ number of bits per symbol
$R_s = $ symbol rate (sps)

The second way to analyze power is to measure it in terms of power consumption by a radio. Each waveform consumes a certain amount of power that depends on the processes required to transmit and receive information correctly. For example, noncoherent reception requires less processing power than a coherent receiver, including the transmitter and phase correction, and faster symbols require faster processing speed, and therefore more power. The total power consumed includes all aspects of the transmitter and receiver of a waveform, including the transmitter power. However, the last objective in Section 4.2.7 takes care of that in its own way so that this second objective does not need to account for it.

As we deal with SDR technology, power consumption maps directly to the computational complexity of an algorithm. The mapping between these is not straightforward, especially given the low-power states and techniques available in most processors and hardware. Furthermore, different processors and implementations of the same waveform may consume different amounts of power. Unfortunately, a generalized solution or straightforward mathematical equation to understand or model the power consumption does not exist.

To solve this problem, we are forced to analyze the power consumption in terms of strict computational complexity of the known SDR modes. That is, break each piece of waveform down to its components, figure out the computational resources required to run those components, and then put together a lookup table for a given waveform's power requirements. Luckily, the task is simpler than trying to measure all possible waveforms since the great majority of the differences exist within the modulator and demodulator. These discrete values are easily calculated and used in a database for use by the optimizer. The computational analysis for the GNU Radio modulators used here is presented in Appendix C.

## Artificial Intelligence in Wireless Communications

The other aspect of computational power is mainly due to the sampling rate required. In this case, the symbol rate directly defines the sampling rate required and therefore the computational power required for a waveform.

All other aspects of the waveform involved in this work do not lead to an increase in computational power, though other concepts as channel coding, source coding, interleaving, or spreading will certainly affect this objective.

## 4.3 Multiobjective Optimization: A Different Perspective

The previous sections described the objective functions we focus on in this work. When reviewing these, there is overlap as well as interactions among certain objectives. When any one objective is optimized, it affects the performance of some other objectives, either positively or negatively. We find constructive to graphically represent these interactions to understand the complexity of the multiobjective environment. In Figure 4.2, we list each objective as a node and two types of edges. Solid edges with arrows define a direct relationship between two objectives, where one objective depends on the other objective being pointed to. The dashed edges with no directivity indicate some indirect dependence through one or more knobs. For example, BER, bandwidth, spectral efficiency, throughput, and computational complexity all depend on the type of modulation used, so changing the modulation affects all of these objectives in some way.

## 4.4 Multiobjective Analysis

Equation (4.1) provides the basic formula to describe a multiobjective optimization problem, and the preceding sections describe a set of possible objectives when optimizing the PHY layer of a radio. What remains to understand how the cognitive engine can use to analyze the behavior of different waveforms and select the best one. The method of performing this analysis is a large factor in the success of a multiobjective optimization problem.

## 4.4.1 Utility Functions

The most straightforward method of selection is to build a single utility function that combines the objectives into one number. The algorithm can then easily rank the solutions and select the solution that maximizes (or minimizes) the utility function. Utility functions are a core research area in economics and

## Optimization of Radio Resources

![4.2](img/4.2)

**Figure 4.2 Dependency**: Solid lines with arrows define a direct relationship between two objectives, where one objective depends on the other objective being pointed to. The dashed edges with no directivity indicate some indirect dependence through one or more knobs. For example, BER, bandwidth, spectral efficiency, throughput, and computational complexity all depend on the type of modulation used, so changing the modulation affects all of these objectives in some way.

The most straightforward method of selection is to build a single utility function that combines the objectives into one number. The algorithm can then easily rank the solutions and select the solution that maximizes (or minimizes) the utility function. Utility functions are a core research area in economics and

The most straightforward method of selection is to build a single utility function that combines the objectives into one number. The algorithm can then easily rank the solutions and select the solution that maximizes (or minimizes) the utility function. Utility functions are a core research area in economics and

The most straightforward method of selection is to build a single utility function that combines the objectives into one number. The algorithm can then easily rank the solutions and select the solution that maximizes (or minimizes) the utility function. Utility functions are a core research area in economics and

The most straightforward method of selection is to build a single utility function that combines the objectives into one number. The algorithm can then easily rank the solutions and select the solution that maximizes (or minimizes) the utility function. Utility functions are a core research area in economics and

The most straightforward method of selection is to build a single utility function that combines the objectives into one number. The algorithm can then easily rank the solutions and select the solution that maximizes (or minimizes) the utility function. Utility functions are a core research area in economics and

The most straightforward method of selection is to build a single utility function that combines the objectives into one number. The algorithm can then easily rank the solutions and select the solution that maximizes (or minimizes) the utility function. Utility functions are a core research area in economics and

The most straightforward method of selection is to build a single utility function that combines the objectives into one number. The algorithm can then easily rank the solutions and select the solution that maximizes (or minimizes) the utility function. Utility functions are a core research area in economics and

The most straightforward method of selection is to build a single utility function that combines the objectives into one number. The algorithm can then easily rank the solutions and select the solution that maximizes (or minimizes) the utility function. Utility functions are a core research area in economics and

The most straightforward method of selection is to build a single utility function that combines the objectives into one number. The algorithm can then easily rank the solutions and select the solution that maximizes (or minimizes) the utility function. Utility functions are a core research area in economics and

The most straightforward method of selection is to build a single utility function that combines the objectives into one number. The algorithm can then easily rank the solutions and select the solution that maximizes (or minimizes) the utility function. Utility functions are a core research area in economics and

The most straightforward method of selection is to build a single utility function that combines the objectives into one number. The algorithm can then easily rank the solutions and select the solution that maximizes (or minimizes) the utility function. Utility functions are a core research area in economics and

The most straightforward method of selection is to build a single utility function that combines the objectives into one number. The algorithm can then easily rank the solutions and select the solution that maximizes (or minimizes) the utility function. Utility functions are a core research area in economics and

The most straightforward method of selection is to build a single utility function that combines the objectives into one number. The algorithm can then easily rank the solutions and select the solution that maximizes (or minimizes) the utility function. Utility functions are a core research area in economics and

The most straightforward method of selection is to build a single utility function that combines the objectives into one number. The algorithm can then easily rank the solutions and select the solution that maximizes (or minimizes) the utility function. Utility functions are a core research area in economics and

The most straightforward method of selection is to build a single utility function that combines the objectives into one number. The algorithm can then easily rank the solutions and select the solution that maximizes (or minimizes) the utility function. Utility functions are a core research area in economics and

The most straightforward method of selection is to build a single utility function that combines the objectives into one number. The algorithm can then easily rank the solutions and select the solution that maximizes (or minimizes) the utility function. Utility functions are a core research area in economics and

The most straightforward method of selection is to build a single utility function that combines the objectives into one number. The algorithm can then easily rank the solutions and select the solution that maximizes (or minimizes) the utility function. Utility functions are a core research area in economics and

The most straightforward method of selection is to build a single utility function that combines the objectives into one number. The algorithm can then easily rank the solutions and select the solution that maximizes (or minimizes) the utility function. Utility functions are a core research area in economics and

The most straightforward method of selection is to build a single utility function that combines the objectives into one number. The algorithm can then easily rank the solutions and select the solution that maximizes (or minimizes) the utility function. Utility functions are a core research area in economics and

The most straightforward method of selection is to build a single utility function that combines the objectives into one number. The algorithm can then easily rank the solutions and select the solution that maximizes (or minimizes) the utility function. Utility functions are a core research area in economics and

The most straightforward method of selection is to build a single utility function that combines the objectives into one number. The algorithm can then easily rank the solutions and select the solution that maximizes (or minimizes) the utility function. Utility functions are a core research area in economics and
