
According to the results shown in Tables 10.7 and 10.8, the TC of T_Q(U1) is higher than T_Q(U2). The condition (10.24) to synchronize U1 and U2 is fulfilled.

Now, the next sections show experimental results of the proposed test and the necessary conditions to obtain the multimedia contents encrypted and decrypted in U1 and U2, respectively, considering the symmetric master keys. Two kinds of messages are considered to carry out three experimental tests on the ES. The first message is referred to as m₁(t) and the second message is referred to as m₂(t). Their examples are described in next sections. The recovered messages of m₁(t) and m₂(t) are referred to as m₁′(t) and m₂′(t), respectively.

### 10.6.2.2 First Test: Sensitivity of Secret Keys

The sensitivity test is carried out using the secret keys K₁, K₂, and K₃ in Table 10.4. The secret keys are entered by directly programming the algorithms of U1 and U2, but the secret keys can be registered using touch-screen routines or external keyboard connected to dsPIC33s U1 and U2. Table 10.9 shows the combination of secret keys K₁, K₂, and K₃ to carry out the sensitivity test. The message m₁(t) is reproduced using the initial conditions and parameters proposed in the animation (10.22) where the MACM OS is used to represent the phase plane x₃(n) vs y₃(n) as an example.

**Table 10.9 Sensitivity Test Secret Keys on the Smart-Displays**

| Case | Secret Key on U1 | Secret Key on U2 |
|------|------------------|------------------|
| 1 | K₁ | K₁ |
| 2 | K₁ | K₂ |
| 3 | K₁ | K₃ |

Figure 10.9 shows the result of the sensitivity test among the set of three secret keys. We conclude that the definition of secret key supports the hypothesis that its construction of 217 bits is secure because for slight variations of the initial conditions and parameters of secret keys, the result of the recovered message m₁′(t) is different than the original message m₁(t) for different secret keys; similar results are reported in Liu et al. (2016).

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_310_0.png)

Figure 10.9 Test results of sensitivity of secret keys on ES using the MACM OS and the phase plane of x₃(n) vs y₃(n). Case 1: (a) original m₁(t), (b) cryptogram, (c) reception of m₁′(t), Case 2: (d) original m₁(t), (e) cryptogram, (f) reception of m₁′(t), and Case 3: (g) original m₁(t), (h) cryptogram, and (i) reception of m₁′(t).

### 10.6.2.3 Second Test: Animation of the Chaotic Oscillator as Message m₁(t)

We use the initial conditions and parameters of MACM chaotic oscillator described in Equation 10.22 to reproduce m₁(t). For this test we use the MACM OS, the same secret key K₁ is considered for U1 and U2, and the recovered message m₁′(t) is shown in Figure 10.10a. The K₂ is entered in U2, and K₁ is conserved in U1, where Figure 10.10b shows the animation (10.22) encrypted in U2.

Tables 10.8 and 10.9 showed the algorithm performance of this example using graphic interface mode in the MACM OS. Therefore, according to the graphic-processing capacity of U1 and U2, the proposed MACM OS supports 1689 pixels per second considering the animation of MACM chaotic oscillator (10.22).

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_311_0.png)

Figure 10.10 Animation of the chaotic oscillator (10.22) used as message m₁(t): (a) animation recovered in U2 using same K₁ in U1 and U2, and (b) animation encrypted in U2 using K₁ in U1, and K₂ used in U2.

### 10.6.2.4 Third Test: MP3 Audio File as Voice Message m₂(t)

We propose to manage external block-memory segments where the multimedia contents are stored. An external Micro SD card is considered to store one file where the multimedia contents are loaded from Micro SD Slot of U1. The MP3 audio file with the information “Hello World” is stored in the Micro SD with the name: SOUND.MP3. Table 10.10 shows the characteristics of SOUND.MP3 file.

**Table 10.10 Characteristics of MP3 Audio File: SOUND.MP3**

| Property | Value |
|---|---|
| Size | 17.8 KB (18240 bytes) |
| File format | MPEG 1 Layer 3 File |
| Audio | 160 kbps |
| Sample Rate | 32000 Hz |
| Configuration | Stereo |
| Time length | 0:00:00.865 s |

Cubase 5 professional audio software is used to obtain the voice recorder MP3 audio file. Figure 10.11 shows the block diagram where the MACM OS is configured in “Text Interface” to show the encryption process of MP3 file in U1, and decryption process to recover the MP3 data file in U2. In order to resume the process, Table 10.11 shows the steps with the processes description in U1, and Table 10.12 describes the process in U2.

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_312_0.png)

Figure 10.11 Test results on the MACM OS using external Micro SD Card to encrypt MP3 audio file.

Now, the package according to the size of file m₂(t) is sent. In this stage, the intruder can read or copy the encrypted message, it is impossible to identify the format, the MP3 file has one format according to the standard, and it is impossible to reproduce the file using one MP3 player.

Finally, the m₂′(t) MP3 audio file was recovered; this message has the same audio characteristics of the original audio file. We conclude that MACM OS allows to encrypt, decrypt, and transfer data from U1 to U2 6250 times per second for data with structure of 16 bits (or 2 bytes).

**Table 10.11 Description of the Processes to Encrypt the MP3 File in U1**

| Step | Process | Description |
|------|---------|-------------|
| 1 | Initializing SD Card | We configured the SPI port 2 only to use the MMC library. |
| 2 | SD Card ready to use | The file SOUND.MP3 is loaded from external Micro SD card. |
| 3 | Audio file transfer to dsPIC Mem | The MP3 audio file is transferred to dsPIC memory. |
| 4 | Initializing VS1053B Audio Codec | Now, the SPI port 2 is configured to control audio codec VS1053B. |
| 5 | Play Audio: SOUND. MP3 file | MP3 file is reproduced by using audio out VS1053B. |
| 6 | Start encryption of the Message | MP3 file was encrypted using the inner memory of dsPIC33, and the SPI port 2 is configured to transmit data package. |
| 7 | Encrypted message transmitted | The encrypted message m₂(t) was satisfactorily transmitted. |

**Table 10.12 Description of the Processes to Decrypt the MP3 File in U2**

| Step | Process | Description |
|------|---------|-------------|
| 1 | Waiting... | SPI port 1 of U2 was configured in slave-mode to wait the data link from U1. |
| 2 | Reception Ready (file size in bytes) | The complete encrypted message m₂′(t) is received by using the inner dsPIC33 U2 memory. |
| 3 | Message Received is decrypted | Message m₂′(t) was decrypted byte to byte by using the inner dsPIC33EP memory. |
| 4 | Initializing VS1053B Audio Codec | We use SPI port 2 to control the audio codec VS1053B. |
| 5 | Play Audio: SOUND. MP3 file | MP3 file is reproduced by using the audio out of VS1053B. |
| 6 | Finish | The complete process was conducted. |

## 10.7 Conclusions

We proposed the design and experimental implementation of chaotic encryption algorithm by using the communication protocol SPI 16-bit on smart-displays to acquire, process, encrypt, transmit, synchronize, receive, decrypt, and reproduce multimedia contents with one friendly graphic interface, where MACM OS was implemented. Three kinds of tests were carried out to prove the message performance in the ES: sensitivity secret key, animation of MACM chaotic oscillator, and MP3 audio file transferred. The cryptogram was subjected to statistical test generating PR sequences. This algorithm can be used in an integrated circuit (IC) and smart-displays that has the standard SPI protocol.

The numerical results were verified with MikroC Pro for the dsPIC compiler that includes the properties of standard IEEE-754, AN575 of 32 bits into the dsPICs. The quality of message depends on the processing capacity of the smart display. The Mikromedia for dsPIC33EP smart display is easy to install and it has a low cost implementation because the system costs less than 99 USD.

In future work, we will test with other multimedia contents and apply the encrypted and decrypted algorithms with other communication protocols such as I2C, USB-CAN, or Ethernet with larger quantity of bits using other smart displays, with more processing capacity.

## Acknowledgments

This work was supported by the CONACYT, México, under Research Grant 166654.

## References

- 1. Feredj, M. 2016. A smart display component model for embedded systems modeling and simulation. 2016 SAI Computing Conference 452–457.
- 2. Barr, M. and Massa, A. 2006. Programming Embedded Systems: With C and GNU Development Tools. 2nd edition. Newton, MA: O’Reilly Media.
- 3. Philips Semiconductors, 1995. The I2C-bus and how to use it. http://www.i2cbus.org/fileadmin/tp/i2c_bus_specification_1995.pdf (accessed November 10, 2016).
- 4. Philips Semiconductors, 2003. AN10216-01 I2C Manual. http://www.nxp.com/documents/application_note/AN10216.pdf (accessed November 10, 2016).
- 5. Motorola, Inc., 2003. SPI Block Guide V03.06. Document Number S12SPIV3/D.
- 6. Oudjida, A.K., Berrandjia, M.L., Tiar, R. et al. 2009. FPGA implementation of I2C & SPI protocols: A comparative study. 16th IEEE International Conference Electronics, Circuits, and Systems, 507–510.
- 7. Méndez-Ramírez, R., Arellano-Delgado, A., Cruz-Hernández, C., Abundiz-Pérez, F., and Martínez-Clark, R. 2018. Chaotic digital cryptosystem by using SPI protocol and its dsPICs implementation. Front Inform Tech 19:165–179.
