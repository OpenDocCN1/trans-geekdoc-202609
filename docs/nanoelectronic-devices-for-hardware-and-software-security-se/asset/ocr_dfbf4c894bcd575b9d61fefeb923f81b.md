6 • Memristor 121

![](bbox=[0.185, 0.093, 0.814, 0.335])

FIGURE **6.1** Device structure of memristor.

Titanium dioxide is an electrical insulator with high resistance, but altering the amount of oxygen in titanium oxide reduces its resistance. The TiO$_{2-x}$ layer is said to be ‘doped’, as these oxygen deficiency effects are similar to an adhered impurity atom in the semiconductor. In general, a memristor can be fabricated by a variety of insulating materials sandwiched between metal layers, including chalcogenides [3, 4], metal oxides [5, 6], perovskites [7, 8], and organic films [9, 10].

# 6.1.2 Memristors Operations

The operation of memristors can be understood by hydraulic analogies. In this analogy, memristors are compared to a fictitious pipe with a mobile sand filter in that it regulates the flow of water. When water flows through a bed of sand, sediment clogs the pores of the filter and restricts the flow of water. Reversing the flow flushes out the sediment, and water flows smoothly. It is important to note that in both cases it is the direction of flow that controls the state of the device, as the resistance of the sand filter is the same in both directions.

Similarly, the memristive resistive state is controlled by the applied voltage polarity in a bipolar memristor and voltage magnitude in unipolar [11]. Memristors are said to have two resistance sets; a high resistance state (HRS) referred to as OFF and a low resistance state (LSR) referred to as ON. In SET operation, a voltage of suitable polarity and magnitude, $V_{SET}$, must be applied to switch it from HRS to LSR. The RESET operation is done by switching LSR to HRS by applying a lower voltage, $V_{RESET}$. The polarity of $V_{SET}$ and $V_{RESET}$ is the same in unipolar and opposite in bipolar [12]. There are several simulated models of the memristor that adopting the principle of device physics behavior and the link between the memristance and the device $\phi(t)$ of the device, $M(\phi(t))$, can be noted as in equation 6.5 by Y.N. Joglekar et al. [13].

```
$M(\phi(t)) = \frac{HRS}{D} - 2- \eta \frac{LRS}{HRS} \phi(t) \mu \quad (6.5)$
```

$\eta$ defines the polarity of the applied bias +1 for positive voltage and -1 for negative bias, and the dopants’ mobility is $\mu$. The movement rates the domain wall estimated by S. Kvatinsky et al. [14] as in equation 6.6, when the current ($I$) is flowing through the memristor.