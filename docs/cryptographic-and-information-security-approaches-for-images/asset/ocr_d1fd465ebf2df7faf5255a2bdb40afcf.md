# Table 10.7 Time Complexity of U1

| Process | Algorithm | $T_{Q(U1)}(\mu s)$ | $f_{Q(U1)}(Hz)$ | Denotation |
|---|---|---|---|---|
| Multimedia content | Chaotic Oscillator MACM in DV | 108 | 9259 | A |
| Data encryption 48 bits | TFT Dot function to drawn one pixel on the TFT LCD | 480 | 2083 | B → C → D |
| Transmission | Encrypted message for 6 bytes | 4 | 250000 | E |
| Total |  | 592 | 1689 | - |

reproduce the DV of MACM oscillator (10.22) in U1. The algorithm is designed to encrypt one pixel using the TFT Dot function, where three words in REG1 format are considered to represent one dot using 48 bits or 6 bytes.

According to Table 10.7, the algorithm of U1 presents TC=592 μs and f_Q(U1)=1689 Hz. For our study, we considered f_Q(U1) as n=1689 iterations per second.

In the case of U2, we need the minor TC in all processes; the configuration of U2 is accelerated with the modification of the internal PPL. This allows processing to be faster in the decryption algorithm. Therefore, the TC of U2 must be less than that of U1

$T_{Q(U1)} > T_{Q(U2)}$ (10.24)

Table 10.8 shows the experimental results of the decryption algorithm.

# Table 10.8 Time Complexity of U2

| Process | Algorithm | $T_{Q(U2)}(\mu s)$ | Denotation |
|---|---|---|---|
| Reception | Encrypted message | 4 | F |
| Decryption stage 6 bytes | Decryption of pixel: X, Y coordinates, and color | 480 | G → H → P |
| Transmission of recovered message | Draw one pixel on the TFT LCD | 25 | Q |
| Total |  | 509 | — |