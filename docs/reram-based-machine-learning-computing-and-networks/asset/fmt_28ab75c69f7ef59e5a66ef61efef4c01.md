
Since HP developed the first passive memristor in 2008 [62], there have been works on single-bit [160–162, 164] and multibit [165, 166] memory storages. The unique $I$–$V$ characteristic of memristors, however, leads to a nonlinear $q$–$\phi$ characteristic, which makes it difficult to determine the pulse size for achieving a certain state [165, 166]. Therefore, it has been seen as a problem for multilevel memory designs [165, 166]. To overcome this problem, researchers have developed methods, some fairly complicated, which use analog circuits and Opamps for both reading and writing [165, 166]. Using Opamps and analog circuits for readout seems to be inevitable [160, 165, 166]. However, as we will present, the aforementioned characteristic can be taken advantage of, to store more than one bit in memristors, using circuits which are compatible with digital designs. These circuits are hence less complex. Although digital bit streams have been used for setting synaptic values [167], the exact stored value and recovery of the stored value are not of high importance in such applications. In memory applications, on the other hand, this is of paramount importance. Therefore, in this chapter, we discuss the reliability of the storage and readout, as well as how encoding can help improving these parameters.

The rest of this chapter is organized as the following: In the next section, we briefly review the aforementioned unique characteristics of memristor and show how it can be taken advantage of, in order to store more than one bit in each memristor. In [Section 3.4.3](#Chapter3.html#c03_sec4-3), we present the digital writing method for storing two bits of data on a single memristor, as well as the readout circuit. Then, in [Section 3.4.4](#Chapter3.html#c03_sec4-4), we show the results of our simulations which confirm the feasibility of the proposed approach. In [Section 3.4.5](#Chapter3.html#c03_sec4-5), we improve the reliability of the storage, and the number of stored bits, using different proposed encoding schemes, especially regarding practical implementations and further verification of the proposed approach.

### 3.4.2 Multi-threshold resistance for data storage

It is a well-established phenomenon in the literature that the resistance of a memristor depends on the charge flown through it [160, 168]. This can be modeled in various ways, one of the most prominent of which is [168]:

$$M(q) = R_{off} - (R_{off} - R_{on}) \frac{q}{Q_0}$$

where $R_{off}$ and $R_{on}$ are the maximum and minimum resistance of the memristor, and $q$ is the charge flown through the memristor with the initial value of $q_0$. Finally, $Q_0$ is a constant which represents physical characteristics of the device such as doping of the semiconductor and its size.

According to (3.13), not only the resistance, but also changes of the resistance in a memristor due to identical voltage pulses depend on its current state [165, 169]. This characteristic seen as a hardship [165, 166] can be turned into an opportunity based on the following theorem.

**Theorem:** *Distinct output resistances correspond to distinct input patterns, which allows storage of more than one bit in a single memristor.*

**Short Proof**[[*]](#Chapter3.html#c03_fn1): Assume two distinct states A and B, seen in [Figure 3.16](#Chapter3.html#c03_fig16), with unequal resistance of $M_A \neq M_B$, where $M_A > M_B$. Now, we are interested in finding out the ratio of resistance change at these two points, due to the application of an input voltage pulse with the amplitude of $V_p$ and width of $T_p$. Based on Ohm's law, we have

$$i(t) = \frac{V_p}{M(q(t))}$$

where $M(q)$ of the memristor is given by (3.13). Solving this equation is rather complicated and out of the scope of this chapter. Therefore, in a simplified manner, we estimate the changes of resistance at each point by its slope, $\frac{dM}{dq}$. In other words, in the vicinity of point $q$, we estimate (3.13) by

$$M(q) \approx M(q_0) + \frac{dM}{dq}(q - q_0)$$

![Figure 3.16 Resistance of a memristor as a function of the charge stored in it](images/PBPC0390-03-f16.jpg)

By substituting (3.15) into (3.14), and integrating over the period, $T_p$, we have [169]

$$\Delta q = \int_0^{T_p} \frac{V_p}{M(q(t))} dt$$

Solving (3.16), we obtain

$$\Delta M \approx \frac{dM}{dq} \Delta q = \frac{dM}{dq} \frac{V_p T_p}{M(q_0)}$$

where

$$\frac{dM}{dq} = -\frac{R_{off} - R_{on}}{Q_0}$$

On the other hand, we can easily infer from (3.15) that $\frac{dM}{dq}$ is constant. Based on this, the ratio of resistance change due to charge change at point A and B is

$$\frac{\Delta M_A}{\Delta M_B} = \frac{M_B}{M_A}$$

This shows how the change of resistance of memristors at different stages due to identical pulses depends on its state (resistance) at the time. This ratio could be further simplified and approximated to the resistance ratio only [169].

Now, assuming that a positive pulse presents "1" and a negative pulse presents "0," if a memristor is fed by a positive input pulse followed by a negative input pulse ("10"), it will reach a different state ("$A_{10}$"), compared to the case where the negative pulse is applied before the positive pulse ("01" and hence $A_{01}$). The rationale behind it is that the resistance change due to an initial negative pulse (A to $A_0$) is different compared to the resistance change due to the same pulse, once the state of memristor has changed due to a previous positive pulse ($A_1$ to $A_{10}$). The same holds for changes due to positive pulses in two different states ($A_0$ to $A_{01}$ versus A to $A_1$). Therefore, we can conclude that, since the states of the memristor after application of "01" and "10" are different, based on the state of the memristor, its original input can be retrieved [169]. This will be verified in the next section.

### 3.4.3 Write and read

Based on the aforementioned concept, in this section, we present our read and write method and simulate them in [Section 3.4.4](#Chapter3.html#c03_sec4-4), to test the feasibility of successfully recovering a data value which was stored through digital streaming. For the array architecture, isolation and access to the memory cell, a 1T1R architecture similar to [166] is assumed. Since the Opamp (comparator) is the crucial part of the circuit determining the feasibility and reliability of this implementation, we have used a model of an existing off-the-shelf Opamp, namely `LT1012`, which takes into account nonideal characteristics such as offset.

#### 3.4.3.1 Write-in method

As previously discussed in order to distinguish the "1" input and "0" input, respectively, positive and negative pulses are used, which can be implemented through simple switches to reference voltages. This eliminates the need for the complex circuit proposed in [165] or the DAC used in [166]. The magnitude of these pulses for the current experiment is 0.5 V and the pulse widths are 10 ms. The inputs were applied based on the most-significant-bit first and the least-significant-bit last.
