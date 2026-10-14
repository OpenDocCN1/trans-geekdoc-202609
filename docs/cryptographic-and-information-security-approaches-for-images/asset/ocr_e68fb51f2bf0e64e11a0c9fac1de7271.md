until 16 elements are completed, the last element $c_{i6}$ corresponding to the element $e_{j+15}$ that is referred to as the position $d_{i,j+15}$ of vector $D$,

$E = [c_1, c_2, ..., c_{16}] = [d_{i,j}, d_{i,j+1}, ..., d_{i,j+15}] = [e_j, e_{j+1}, ..., e_{j+15}]. \quad (10.13)$

# 10.3.3 Transmission of Encrypted Messages

The encryption algorithm is processed on U1. The encrypted information of $m(t)$ is contained in the row vector $E$, where the 16 elements are equivalent to one word of 16 bits, and when this word is transmitted it corresponds to one iteration $n$.

Now, Table 10.1 shows the SPI configuration mode of U1 and U2. U1 is connected with U2 using the pins: SS2 connected with SS1, SDO2 connected with SDI2, and SCK, which is the common clock to synchronize the smart display Mikromedia dsPIC33s. Finally, the word contained in vector $E$ is transmitted iteration-by-iteration $n$ from U1 to U2.

# 10.4 Cryptogram

In this section, we describe the statistical tests to prove the hypothesis that $m(t)$ is secure from the observer stand point. In order to show whether the proposed algorithm reproduces PR sequences, we performed the statistical tests to the cryptogram extracted from U1.

Figure 10.5 shows the block diagram of the ES where an intruder intervenes in the SPI protocol by using an external Mikromedia for dsPIC33EP U3. U1 is connected with U3 using the pins: SS2 connected with SS1, SDO2 connected with SDI1, and SCK is the common clock to synchronize the dsPIC33EPs. The rebuilt encrypted message $m(t)$ is obtained, but the intruder cannot read the data.

# 10.4.1 Statistical Tests

We present test results of the behavioral analysis of the sequence generator obtained from the proposed encryption algorithm. Here, we consider encrypted binary sequences with length $n = 20000$ bits generated from U1. The binary sequence is read and stored by a computer, then we calculate the statistical tests using MATLAB®. We performed statistical tests to check whether the encrypted algorithm generates sufficiently secure PR sequences [30,31]. Table 10.5 shows the results of five basic tests [32]. In addition, Table 10.6 shows the Federal Information Processing Standards (FIPS) 140-1 statistical test for randomness in encrypted binary sequences with length $n = 20000$ bits generated from U1 [32]. Figure 10.6 shows graphical results of FIPS 140-1 by using histogram in poker and runs tests.