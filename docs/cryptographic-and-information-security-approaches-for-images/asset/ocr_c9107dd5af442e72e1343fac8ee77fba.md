![](bbox=[0.1, 0.14, 0.9, 0.24])

# Figure 20.7 An example of Jonathan and Yan’s scheme. (a) Original secret (b) Share one with embedded (c) Share two with embedded (d) Recovered secret.

the secret transport mechanism which along string of alphanumeric characters can be embedded into the barcode.

An example of the scheme proposed can be seen as Figure 20.7. The shares are random in the scheme above, which may attract suspicion of encryption, due to embedding QR codes into VSS shares.

Wang et al. [13] proposed a scheme which embedding QR code into VC shares for authentication. The basic idea is to embed QR codes into given shares to prevent cheating. They search the best region of a given share where the QR code could be embedded into so as to keep the visual quality of the revealed secret and the embedding will not affect the visual cryptography secret revealing too much. The contribution of the scheme proposed is to authenticate the VC shares using a QR code by embedding it into the similar regions of the VC share, the embedding could not affect the VC secret revealing too much. An example of the scheme proposed can be seen as Figure 20.8. The shares are random so that we cannot get any information in the scheme above, which may attract suspicion of encryption, due to embedding QR codes into VSS shares. Also, the QR code embedded may be hard to extract.

The schemes proposed above is to embed QR codes into VC shares which can achieve the purpose of authentication. Unfortunately, it may attract suspicion of encryption. Our scheme proposed is to embed VC shares into cover QR codes which may reduce the likelihood of attracting the attention of potential attackers. Each output share can be scanned and decoded utilizing a QR code reader. The secret image can be revealed with the abilities of stacking and XOR lossless recovery.

Figure 20.9 shows the results of QR code version 4 with error correction level H by Chow et al.’s scheme [14] proposed. Figure 20.9a–c shows the cover QR codes, (d–f) shows the resulting QR code shares that can be decoded correctly,

![](bbox=[0.12, 0.77, 0.88, 0.88])

# Figure 20.8 An example of Wang et al.’s scheme. (a) Secret revealing using QR code (b) A VC share embedded with QR code having the string “AUT” (c) A VC share embedded with QR code having the URL “http://www.aut.ac.nz.”