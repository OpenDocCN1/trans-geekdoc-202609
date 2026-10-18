

where `N` is the dimension of the square level 1 decompressed image matrix; `z` is the variable ranging from 1 to `N`/2, increases in every alternate column; `x` is the variable ranging from 1 to `N`, increases in every row. Equation ([A.31](#AppendixA.html#APPA_eqn31)) is used for calculating the pixel value of odd columns and Equation ([A.32](#AppendixA.html#APPA_eqn32)) is used for calculating the pixel value of even columns of the level 1 decompressed image. The corresponding level 2 decompressed image in the form of matrix "`C`" is shown in Equation ([A.29](#AppendixA.html#APPA_eqn29)) where calculation of each pixel is performed based on the aforementioned equations.

![image](OEBPS/images/PBCS0600-APP1-e33.jpg)

**Sengupta–Roy HAAR decompression reduction functions**

![image](OEBPS/images/APPA_eqn34.gif)

![image](OEBPS/images/APPA_eqn35.gif)

![image](OEBPS/images/APPA_eqn36.gif)

![image](OEBPS/images/APPA_eqn37.gif)

**DFG of HWT-based image decompression and scheduled DFG based on four adder–subtractor units, two adders, and two subtractors**

![image](OEBPS/images/PBCS0600-APP1-u02.jpg)

HAAR LOSSLESS CODEC

![image](OEBPS/images/PBCS0600-APP1-e38.jpg)

![image](OEBPS/images/APPA_eqn39.gif)

![image](OEBPS/images/APPA_eqn40.gif)

![image](OEBPS/images/APPA_eqn41.gif)

![image](OEBPS/images/APPA_eqn42.gif)

To generate the compressed image matrix "`B`," Equation ([A.39](#AppendixA.html#APPA_eqn39)) is used for calculating the intensity of pixels corresponding to both row and column index 1 to `N`/2; Equation ([A.40](#AppendixA.html#APPA_eqn40)) is used for calculating the intensity of pixels corresponding to row index 1 to `N`/2 and column index greater than `N`/2 to `N`; Equation ([A.41](#AppendixA.html#APPA_eqn41)) is used for calculating the intensity of pixels corresponding to row index greater than `N`/2 to `N` and column index 1 to `N`/2; Equation ([A.42](#AppendixA.html#APPA_eqn42)) is used for calculating the intensity of pixels corresponding to both row and column index greater than `N`/2 to `N`.

**Sengupta–Roy HAAR lossless image reconstruction reduction functions**

![image](OEBPS/images/APPA_eqn43.gif)

![image](OEBPS/images/APPA_eqn44.gif)

![image](OEBPS/images/APPA_eqn45.gif)

![image](OEBPS/images/APPA_eqn46.gif)

**Sengupta–Roy HAAR image CODEC validation functions**

![image](OEBPS/images/APPA_eqn47.gif)

![image](OEBPS/images/APPA_eqn48.gif)

![image](OEBPS/images/APPA_eqn49.gif)

![image](OEBPS/images/APPA_eqn50.gif)

Corresponding DFG below represents the validation function as shown in Equations ([A.47](#AppendixA.html#APPA_eqn47))–([A.50](#AppendixA.html#APPA_eqn50)), where `N` is the dimension of the square input image matrix; `n` is the variable ranging from 1 to `N`/2, increases in every alternate row; `i` is the variable ranging from 1 to `N`/2, increases in every alternate row; `p` is the odd variable ranging from 1 to `N`, increases in every alternate column; `q` is the even variable ranging from 2 to `N`, increases in every alternate column; `j` is the variable ranging from `N`/2 to 1, decreases as ‘`i`’ increases. Equation ([A.43](#AppendixA.html#APPA_eqn43)) is used for calculating the intensity of pixels corresponding to odd rows and odd columns. Equation ([A.44](#AppendixA.html#APPA_eqn44)) is used for calculating the intensity of pixels corresponding to odd rows and even columns. Equation ([A.45](#AppendixA.html#APPA_eqn45)) is used for calculating the intensity of pixels corresponding to even rows and odd columns. Equation ([A.46](#AppendixA.html#APPA_eqn46)) is used for calculating the intensity of pixels corresponding to even rows and even columns.

![image](OEBPS/images/PBCS0600-APP1-u03.jpg)

![image](OEBPS/images/taba.jpg)

## Appendix B

### Part A: Controller design details for JPEG codec IP core

![image](OEBPS/images/taba1.jpg)

![image](OEBPS/images/taba2.jpg)

![image](OEBPS/images/taba3.jpg)

![image](OEBPS/images/taba4.jpg)

![image](OEBPS/images/taba5.jpg)

![image](OEBPS/images/taba6.jpg)

![image](OEBPS/images/taba7.jpg)

![image](OEBPS/images/tabab1.jpg)

![image](OEBPS/images/tabab2.jpg)

![image](OEBPS/images/tabab3.jpg)

![image](OEBPS/images/tabab4.jpg)

![image](OEBPS/images/tabab5.jpg)

![image](OEBPS/images/tabab6.jpg)

![image](OEBPS/images/tabab7.jpg)

![image](OEBPS/images/tabab8.jpg)

![image](OEBPS/images/tabab9.jpg)

![image](OEBPS/images/tabc1.jpg)

![image](OEBPS/images/tabc2.jpg)

![image](OEBPS/images/tabc3.jpg)

![image](OEBPS/images/tabc4.jpg)

![image](OEBPS/images/tabc5.jpg)

![image](OEBPS/images/tabc6.jpg)

![image](OEBPS/images/tabc7.jpg)

![image](OEBPS/images/tabc8.jpg)

![image](OEBPS/images/tabc9.jpg)

Control signals of Registers `Reg_1` to `Reg_40`:

| Registers || Enable at count # |

| --- | --- |

| `Reg_1` || 10 |

| --- | --- |

| `Reg_2` || 21 |

| `Reg_3` || 32 |

| `Reg_4` || 32 |

| `Reg_5` || 43 |

| `Reg_6` || 54 |

| `Reg_7` || 65 |

| `Reg_8` || 65 |

| `Reg_9` || 65 |

| `Reg_0` || 76 |

| `Reg_11` || 76 |

| `Reg_12` || 87 |

| `Reg_13` || 98 |

| `Reg_14` || 98 |

| `Reg_15` || 109 |

| `Reg_16` || 109 |

| `Reg_17` || 120 |

| `Reg_18` || 120 |

| `Reg_19` || 120 |

| `Reg_20` || 131 |

| `Reg_21` || 142 |

| `Reg_22` || 153 |

| `Reg_23` || 153 |

| `Reg_24` || 153 |

| `Reg_25` || 164 |

| `Reg_26` || 164 |

| `Reg_27` || 175 |

| `Reg_28` || 186 |

| `Reg_29` || 186 |

| `Reg_30` || 197 |

| `Reg_31` || 197 |

| `Reg_32` || 208 |

| `Reg_33` || 208 |

| `Reg_34` || 208 |

| `Reg_35` || 218 |

| `Reg_36` || 229 |

| `Reg_37` || 240 |

| `Reg_38` || 240 |

| `Reg_39` || 240 |

| `Reg_40` || 251 |

### Part B: Transfer functions and control data flow graph of DSP cores

#### 1. Four-point DCT

**Transfer functions of four-point DCT:**

![image](OEBPS/images/a2-Eqn-disp-1.gif)

**The generic equation of four-point DCT to compute the first sample:**

![image](OEBPS/images/a2-Eqn-disp-2.gif)

**DFG of four-point DCT based on generic representation to compute the first sample:**

![image](OEBPS/images/PBCS0600-APP2-u01.jpg)

#### 2. Four-point DIT-FFT

**Transfer functions of four-point DIT-FFT:**

![image](OEBPS/images/a2-Eqn-disp-3.gif)

**DFG of four-point DIT-FFT:**

![image](OEBPS/images/PBCS0600-APP2-u02.jpg)

#### 3. Four-point IDCT

**Transfer functions of four-point IDCT:**

![image](OEBPS/images/a2-Eqn-disp-4.gif)

**The generic equation of four-point IDCT to compute the first sample:**

![image](OEBPS/images/a2-Eqn-disp-5.gif)

**DFG of four-point IDCT based on generic representation to compute the first sample:**

![image](OEBPS/images/PBCS0600-APP2-u03.jpg)

#### 4. Eight-point DCT

**Functions of eight-point DCT**

![image](OEBPS/images/a2-Eqn-disp-6.gif)

**Generic representation of eight-point DCT to compute first sample:**

![image](OEBPS/images/a2-Eqn-disp-7.gif)

![image](OEBPS/images/PBCS0600-APP2-u04.jpg)

#### 5. Eight-point DIT-FFT

**Functions of eight-point DIT-FFT:**

![image](OEBPS/images/a2-Eqn-disp-8.gif)

**DFG of eight-point DIT-FFT:**

![image](OEBPS/images/PBCS0600-APP2-u05.jpg)

#### 6. Eight-point IDCT

**Functions of eight-point IDCT:**

![image](OEBPS/images/a2-Eqn-disp-9.gif)

**Generic representation of eight-point IDCT to compute the first sample:**

![image](OEBPS/images/a2-Eqn-disp-10.gif)

**DFG of generic representation of eight-point IDCT to compute the first sample:**

![image](OEBPS/images/PBCS0600-APP2-u06.jpg)

#### 7. Third-order FIR filter

**FIR transfer function:**

![image](OEBPS/images/a2-Eqn-disp-11.gif)

**DFG of FIR:**

![image](OEBPS/images/PBCS0600-APP2-u07.jpg)

#### 8. Third-order IIR filter

**IIR transfer function:**

![image](OEBPS/images/a2-Eqn-disp-12.gif)

**DFG of IIR:**

![image](OEBPS/images/PBCS0600-APP2-u08.jpg)

## Index

active attack 60

additive technique 347

Address Space Layout Randomization (ASLR) 63

advanced encryption standard (AES) 12, 261, 317, 383–4

