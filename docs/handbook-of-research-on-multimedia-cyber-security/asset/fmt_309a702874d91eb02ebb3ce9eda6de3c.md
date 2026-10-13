
# At the Receiver End

At the receiver end, the processed pixel values need to be reconstructed. The pixel values are received in the format of a 1-dimensional array. To depict as a picture, the 1-dimensional array has to be converted into 2 dimensional. Thus, the `reshape array` block from the array palette is used where both the row and column dimensions are stated as 256. Thus, the 2D representation is obtained back. These pixels are flattened using the `Flatten pixmap` block from graphics and Sound palette. The corresponding colour chart for 8-bit grayscale image is also given as an input. The output can be written into a file or displayed using an indicator. Incorporating the above discussed block the transmitter and receiver block diagram of the proposed method is shown in figure 1a and figure 1b.

| Figure 1a. Transmitter block diagram |
| --- |
| ![Figure978-1-7998-2701-6.ch012.f01a](i/ch012.f01a.png) |

| Figure 1b. Receiver block diagram |
| --- |
| ![Figure978-1-7998-2701-6.ch012.f01b](i/ch012.f01b.png) |

# USRP Transmission

USRP is universally accepted prototype for wireless system. The experimental set up is shown in figure 2. Two USRP’s are utilized. One USRP functions as transmitter and another as receiver. The experiment is conducted indoor with air as the medium. The image to be transmitted into one dimensional array and transmitter. At the receiving end the reverse process is carried out and the image has been retrieved.

| Figure 2. Experimental setup |
| --- |
| ![Figure978-1-7998-2701-6.ch012.f02](i/ch012.f02.png) |

# RESULTS AND DISCUSSION

Software simulation involves appreciable transmission and reception of the input 256\*256 grayscale image and its proper reconstruction at the receiver end through a simulated AWGN Noise Channel model. The software simulation results incorporating the above obtained parameter values are tested on the `LabVIEW` platform. The proposed methodologies include the addition of modules in the given ordered series of low-level encryption using Hadamard matrix, BCH encoder, Permuter, symbol mapping, `IFFT` block, Cyclic prefix insertion and windowing in the transmitter section. The above modules are constructed using different modules present in various signal processing and RF Communication palettes present in `LabVIEW`. The simulated results obtained are illustrated in a closer view as below in the block diagram window and front panel window.

The image to be transmitted is acquired using image acquisition blocks present in the vision toolkit of `LabVIEW` and it is shown in figure 3. The image from the input file path is read and using the block `IMAQ Image to Pixel`, every pixel value is obtained in a 2 Dimensional array. These pixel values are further processed and sent for low level encryption with Hadamard matrix. Meanwhile the transmitter properties inputs are also entered which comprises of parameters like number of bits, number of subcarriers, word to symbol mapping, D/A rate, fundamental frequency, percentage of cyclic prefix and type of windowing method opted.

| Figure 3. Image acquisition |
| --- |
| ![Figure978-1-7998-2701-6.ch012.f03](i/ch012.f03.png) |

The 2-Dimensional array of pixels is multiplied with a 256 order Hadamard matrix to scramble the pixels. This image on further encryption using the permutation matrix gives rise to an appreciable amount of data hiding and it is shown in figure 4a and 4b respectively.

| Figure 4a. Post hadamard |
| --- |
| ![Figure978-1-7998-2701-6.ch012.f04a](i/ch012.f04a.png) |

| Figure 4b. Post permuter |
| --- |
| ![Figure978-1-7998-2701-6.ch012.f04b](i/ch012.f04b.png) |

Post low level encryption with Hadamard matrix and permuter, the pixels are converted into unsigned 8-bit binary values which are concatenated to each other to form the input bit stream. Then, the input bits are Huffman encoded as part of source coding and BCH encoded as part of channel coding. Since the addition of Hadamard matrix processing and channel coding increases the bandwidth usage it is of utmost importance to nullify this effect with lossless compression. Huffman encoding, a variable length encoding scheme is used. Figure 5 shows the front panel of source coded and channel coded data.

| Figure 5. Source and channel coding front panel |
| --- |
| ![Figure978-1-7998-2701-6.ch012.f05](i/ch012.f05.png) |

The output serial bits need to be converted from bit to word and from word to symbol to employ symbol mapping. Bit to word conversion can be employed by using `reshape array` and `slit 1D array` block from the array palette. Here number of bits per symbol is taken as 2. For software simulation QPSK mapping is employed. Further analysis can be employed for different modulation schemes like 4- and 16- QAM. The constellation positions of the appropriate symbols are given in the word to symbol mapping input parameter in the transmitter properties. The panel window is as shown in figure 6.

| Figure 6. Symbol mapping – front panel |
| --- |
| ![Figure978-1-7998-2701-6.ch012.f06](i/ch012.f06.png) |

`IFFT` processing is done to acquire and maintain orthogonality and for transformation of domains. Emulating the characteristic specifications of 802.11a, the size of FFT is fixed as 64. Post `IFFT` the signal is sent for cyclic prefix insertion. 25% of signal in the end is appended to the beginning with the help of array functions. The last step in the transmitter side is windowing and the signal is sent through the channel modelled as an AWGN Noise channel model. The front panel of cyclic prefix insertion is as shown in figure 7.

| Figure 7. Cyclic prefix insertion- front panel |
| --- |
| ![Figure978-1-7998-2701-6.ch012.f07](i/ch012.f07.png) |

The front panel window of the entire transmitter section is as shown in figure 8.

| Figure 8. Transmitter- front panel |
| --- |
| ![Figure978-1-7998-2701-6.ch012.f08](i/ch012.f08.png) |

The transmitted signal after passing through a modelled AWGN noise channel reaches the receiver for cyclic prefix removal, FFT processing with size 64 and symbol to bit conversion. The converted bit stream is further decoded and the image is reconstructed. The removal of cyclic prefix is shown in figure 9 and source decoding is shown in figure 10.

| Figure 9. Cyclic prefix removal- front panel |
| --- |
| ![Figure978-1-7998-2701-6.ch012.f09](i/ch012.f09.png) |

| Figure 10. Source and channel decoding with depermuter and image reconstruction |
| --- |
| ![Figure978-1-7998-2701-6.ch012.f10](i/ch012.f10.png) |

The front panel of USRP as shown in figure 11a and figure 11b.

| Figure 11a. USRP transmitter- front panel |
| --- |
| ![Figure978-1-7998-2701-6.ch012.f11a](i/ch012.f11a.png) |

| Figure 11b. USRP receiver – front panel |
| --- |
| ![Figure978-1-7998-2701-6.ch012.f11b](i/ch012.f11b.png) |

# PERFORMANCE METRICS

The performance metric considered in this work are Mean-Squared Error (MSE) (Romi Singh, Shipra Sharma & Shikha Singh, 2014) and Peak Signal-to-Noise Ratio. The MSE between two images can be calculated as:

![Mathtype978-1-7998-2701-6.ch012.m06](i/ch012.m06.svg)

Peak Signal-to-Noise Ratio (PSNR) is given by:

![Mathtype978-1-7998-2701-6.ch012.m07](i/ch012.m07.svg)

The results have been obtained to find the optimum value of BCH encoder parameters (n, k, t). All the results have been obtained by the assumption of the permutation array being `[2 0 1 3 4]`.

## Table 1. MSE and PSNR values for different (n,k,t) of BCH coding blocks

| S. No | BCH (n, k, t) | BCH Encoded Bits | Number of Words | MSE | PSNR |
| --- | --- | --- | --- | --- | --- |
| 1 | (7,4,1) | 875000 | 437500 | 3.7412 | 42.4006 |
| 2 | (15,11,1) | 681810 | 340905 | 4.4806 | 41.617 |
| 3 | (15,7,2) | 1071420 | 535710 | 4.1003 | 42.0027 |
| 4 | (15,5,3) | 1500000 | 750000 | 3.7412 | 42.4006 |
