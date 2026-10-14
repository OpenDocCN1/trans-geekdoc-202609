
to (117,117). The processing QR₁ will be altered in the region of A[1] and A[4], the processing QR₂ will be altered in the region of A[2] and A[5] while the processing QR₃ will be altered in the region of A[3] and A[6]. According to the principle of the error correction mechanism [18] in the QR code and the tests, the cover QR codes above can be recognized correctly with the data of rectangular region altered completely. As the secret image with the size of 110 × 110 pixels, we divide the secret image into six regions that matching the QR codes regions, A[1]... A[6]. QR code shares will be generated according to the proposed scheme as steps above. This means that the QR code shares can be recognized correctly in any case and the secret image can be recovered by stacking two or three QR code shares without any computation. On the other hand, if the light-weight computation device is available, the secret image can be revealed with better visual quality based on XOR operation and could be lossless revealed when sufficient shares are collected.

As a result, in the experiments, through looking up Figures 20.3 through 20.6, the following conclusions are obtained:

- 1. When t < k shadow images are collected, there is no information of the secret image could be recognized, which shows the security of the proposed scheme.
- 2. When t (k ≤ t ≤ n) shadow images are reconstructed by stacking, the secret image could be recognized. When k shadow images are reconstructed by XORing, the secret image can be revealed with better visual quality or lossless revealed.
- 3. The secret image can be recovered by stacking k or more shares based on the human visual system without any computation and QR code readers. In addition, the secret image can also be revealed with better visual quality based on XOR operation and could be lossless revealed when sufficient shares are collected with light-weight computation device.
- 4. The scheme proposed can reach (k,n) VSS threshold with the abilities of stacking and XOR lossless recovery.

## 20.4.4 Compared with Related Schemes

In the section, we compare the proposed scheme with other related schemes especially Jonathan and Yan’s scheme [12] and Wang et al.’s scheme [13], and Chow et al.’s scheme [14].

Jonathan and Yan [12] presented a scheme that uses a QR code to authenticate the shares. The basic idea is to embed the verification information into the recovered secret in the form of a QR code. In this way, when cheating is suspected, the QR code wouldn’t verify the invalid share after it is used to recover the secret. The reason is that the QR code wouldn’t be guessed or that after a cheater has used his own share, the QR code may not even be recovered as part of the secret. Additionally, an extended form of this secret sharing is presented which embeds the QR code as part of the cover image. In their scheme, the QR code can be used as

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_614_0.png)

## Figure 20.7 An example of Jonathan and Yan’s scheme. (a) Original secret (b) Share one with embedded (c) Share two with embedded (d) Recovered secret.

the secret transport mechanism which a long string of alphanumeric characters can be embedded into the barcode.

An example of the scheme proposed can be seen as Figure 20.7. The shares are random in the scheme above, which may attract suspicion of encryption, due to embedding QR codes into VSS shares.

Wang et al. [13] proposed a scheme which embeds QR code into VC shares for authentication. The basic idea is to embed QR codes into given shares to prevent cheating. They search the best region of a given share where the QR code could be embedded into so as to keep the visual quality of the revealed secret and the embedding will not affect the visual cryptography secret revealing too much. The contribution of the scheme proposed is to authenticate the VC shares using a QR code by embedding it into the similar regions of the VC share, the embedding could not affect the VC secret revealing too much. An example of the scheme proposed can be seen as Figure 20.8. The shares are random so that we cannot get any information in the scheme above, which may attract suspicion of encryption, due to embedding QR codes into VSS shares. Also, the QR code embedded may be hard to extract.

The schemes proposed above are to embed QR codes into VC shares which can achieve the purpose of authentication. Unfortunately, it may attract suspicion of encryption. Our scheme proposed is to embed VC shares into cover QR codes which may reduce the likelihood of attracting the attention of potential attackers. Each output share can be scanned and decoded utilizing a QR code reader. The secret image can be revealed with the abilities of stacking and XOR lossless recovery.

Figure 20.9 shows the results of QR code version 4 with error correction level H by Chow et al.’s scheme [14] proposed. Figure 20.9a–c show the cover QR codes, (d–f) shows the resulting QR code shares that can be decoded correctly,

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_614_1.png)

## Figure 20.8 An example of Wang et al.’s scheme. (a) Secret revealing using QR code (b) A VC share embedded with QR code having the string “AUT” (c) A VC share embedded with QR code having the URL “http://www.aut.ac.nz.”

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_615_0.png)

Figure 20.9 The results of QR code version 4 with error correction level H by Chow, et al.'s scheme proposed. (a) Cover image C₁ (b) Cover image C₂ (c) Cover image C₃ (d) QR share S₁ (e) QR share S₂ (f) QR share S₃ (g) Difference image between C₁ and S₁ (h) Difference image between C₂ and S₂ (i) Difference image between C₃ and S₃ (j) Original QR code with secret message secret S (k) Reconstructed QR code S' (l) Difference image between S and S'.

(g–i) shows the respective difference images between the cover QR codes and the resulting QR code shares. Figure 20.9j shows the original QR code containing the secret message while the reconstructed secret QR code which can be decoded as the same with the original message is shown in Figure 20.9k. Figure 20.9l shows the differences between the reconstructed secret QR code and the secret QR code.

Figure 20.10 shows the results of QR code version 4 with error correction level H by our scheme proposed. Figure 20.10a shows the secret image. Figure 20.10b–c shows the QR code shares resulting from the proposed VSSQR scheme, SC₁, SC₂. Figure 20.10d–e shows the decoding information for SC₁, SC₂, which are random noise-like. We can see that the shares are valid QR codes which can be decoded by

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_616_0.png)

## Figure 20.10 The results of QR code version 4 with error correction level H by our scheme proposed. (a) Secret image S (b) QR share SC₁ (c) QR share SC₂ (d) The decoding information for SC₁ (e) The decoding information for SC₂ (f) Reconstructed QR code by stacking, Sr (g) Reconstructed QR code by XORing, Sr₁.

any standard decoding software into the original messages. Figure 20.10f shows the reconstructed QR code, Sr, which is recovered by stacking two QR code shares. The secret message can be seen directly from the reconstructed QR code. Figure 20.10g shows the revealed QR code, Sr₁, which is recovered by XORing two QR code shares with a light-weight device. The secret message can be seen that it is recovered lossless.

We can see that Chow et al.'s scheme distributes and encodes the information of a QR code containing a secret message into a set of QR codes so as to reduce the likelihood of attracting the attention of potential attackers. Each QR code share is a valid QR code that can be recognized by a QR code reader. However, the secret can only be recovered by XORing the light and dark modules contained in the encoding region of all the n QR code shares and adding the function patterns with a computational device and a QR code reader as well as is only for cases (n,n) where n is equal to or greater than 3.

Compared with the Chow et al.'s scheme above, there are some superior performances as follows. It can be seen that the secret could be revealed with abilities of stacking and XOR lossless recovery by the VSSQR scheme proposed. When stacking two QR code shares which can be decoded correctly, it can be seen directly by HVS without any computational device. On the other hand, the secret image can be also recovered based on XOR operation with lossless recovery when two shares are collected with light-weight computation device.
