# NOT gate

The diagram below illustrates a NOT gate (inverter) using a transistor. In this configuration, the input line is connected to the gate of the transistor, the output line is connected to the source and the drain is connected to ground.

![](bbox=[0.08, 0.07, 0.48, 0.26])

![](bbox=[0.505, 0.17, 0.7, 0.21])

When the input is high (1), the transistor turns on, allowing current to flow from the source to the drain, effectively grounding the output and resulting in a low voltage at the output (0). When the input is low (0), the transistor turns off, preventing current from flowing to the ground. In this state, the output then outputs a high voltage (1).

**Input and output rules:** The NOT gate outputs the opposite value of the input

| Input A | Output X |
| :--- | :--- |
| 0 | 1 |
| 1 | 0 |

Boolean algebra: X = $\overline{A}$

![](bbox=[0.08, 0.27, 0.48, 0.46])

Transistor-level schematic of a NOT gate

# Derived (complex) gates

The following gates – NAND, NOR, XOR and XNOR – are examples of derived gates. Derived gates are combinations of the basic gates and provide more complex logic functions. To show these, we will move up a level of abstraction and, rather than examine the transistor schematic, we will look at how the basic gates are combined to create them.

# NAND gate (NOT AND)

A NAND gate is constructed with an AND gate followed by a NOT gate. Due to this, it gives the opposite output to an AND gate. If both inputs are high (1), the output is low (0). In all other cases, the output is high (1).

![](bbox=[0.27, 0.67, 0.45, 0.71])

![](bbox=[0.76, 0.67, 0.93, 0.71])

**How a NAND gate is constructed:** an AND gate followed by a NOT gate

**NAND gate**

**Input and output rules:** The NAND gate outputs 1 unless both inputs are 1

| Input A | Input B | Output X |
| :--- | :--- | :--- |
| 0 | 0 | 1 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 0 |

Boolean algebra: X = $\overline{A \cdot B}$