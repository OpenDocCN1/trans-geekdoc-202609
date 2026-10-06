# 5 Memristors and Their Applications 111

+   3. Storage encryption.
4. Trusted configuration of FPGAs.

The inherent process variations in memristors can be used to create PUFs called NanoPUFs [12], which have three main sections:

+   i. A memristor-based crossbar.
ii. The challenge (Input) circuit: They enable the application of an input to the decoders. A memristor is selected by the challenge circuit through the column and row decoders. A particular column is selected by the column decoder and then connected to the load resistance ($R_{load}$). A voltage of $V_{dd}$ magnitude is applied to a particular row by the row decoder. At the same time, the rest of the columns and rows standing float.
iii. The response circuit: This gathers the response for a challenge from the crossbar. The response circuit consists of a current comparator and load resistance ($R_{load}$). The comparator compares I_{out}$ (the current which is flowing out of the column) with $I_{ref}$ (the reference current). The response bit is 0 when $I_{out}$ is less than $I_{ref}$, else the logic is 1.

![](bbox=[0.238, 0.395, 0.762, 0.705])

FIGURE 5.13 Memristor-based NanoPUF [12].

Advantages: As memristors are more dense as compared to SRAM, for the same amount of area, NanoPUFs based on memristors generate more response bits. They also consume less power.

# 5.8.2 Nanoelectronic Public Unclonable Functions (NanoPUFs)

While the simulation models of PUFs are hidden from an attacker, the simulation models of a PFAF are public. However, if an attacker tries to simulate the PPUF, the simulation time would be very large – could even several years – as compared to PUF primitive, whose simulation time could be just a few nanoseconds.