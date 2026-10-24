![](bbox=[0.18, 0.1, 0.42, 0.3])

![](bbox=[0.55, 0.1, 0.83, 0.3])

![](bbox=[0.15, 0.35, 0.45, 0.55])

![](bbox=[0.55, 0.35, 0.85, 0.55])

Figure 3.2 The Coin image: (a) original version; (b) encrypted version; (c) original image histogram; (d) encrypted image histogram.

![](bbox=[0.15, 0.7, 0.4, 0.85])

![](bbox=[0.55, 0.7, 0.8, 0.85])

Figure 3.3 (a) The encrypted image with the RC6 algorithm; (b) the histogram.

The second image is obtained by encrypting the Coin image, which is a black-and-white image using the RC6 algorithm in the ECB mode. The image size is 340 × 400 pixels. Algorithms implemented in the ECB mode cannot encrypt a black-and-white image because of its localized histogram. This is shown in Figure 3.2. The third image is obtained by encrypting the Cameraman image using the RC6 algorithm in the CBC mode as shown in Figure 3.3.