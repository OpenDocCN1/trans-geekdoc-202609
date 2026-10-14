(Universally Unique Identifier) and directly obtain the tag, i.e., NMF-NMF-SQ hash and MAC.

# 7.4.1.2.3 Tag Verification

After receiving the codestream and obtaining the tag, the receiver performs HAU verification including the base layer verification and enhancement layer verification.

**Verification of the Base Layer:** For the base layer Ψ_b in a received frame Ψ, HAU first calculates its MAC value ψ as

ψ = ℋ(k_b, Ψ_b)

If ψ = φ, HAU accepts the base. Otherwise, the base layer is considered tampered and HAU directly rejects the base layer and all the enhancement layers of Ψ.

# 7.4.1.3 Experiments and Comparison

In our experiments, we choose twelve standard benchmark video sequences in order to cover different combinations of video characteristics, including motion (fast/slow, pan/zoom/rotation), color (bright/dull), contrast (high/low), and object type (vehicle, buildings, people). Bus (150 frames) and Foreman (300 frames) are of less camera motion while Football (260 frames), Container (300 frames) and Soccer (300 frames) demonstrate camera panning and zooming with object motion and background texture. Bridge-far (300 frames) and Bridge-close (500 frames) show images with smooth motion. Highway (1200 frames) is a sequence of fast motion while Silent (300 frames) and News (300 frames) are static sequences except of motion of partial fields. Mobile (300 frames) and Hall (300 frames) sequences display a still complex background with foreground motion. SVC GOP size and Intra period are set to 8; the QPs of enhancement layers are no more than 38 so that the features extracted with NMF-NMF-SQ are stable.

As HAU exploits the characteristics of SVC to ensure its authenticity, it is robust to content-preserving manipulations but sensitive to content-changing manipulations of enhancement layers. However, cryptographic authentication is sensitive to any bit change of SVC and watermarking-based is semi-fragile to content-preserving manipulations. In other words, HAU achieves a good balance between robustness and sensitivity as shown in the second column of Table 7.4. The third column indicates that cryptographic authentication cannot locate tampered areas. Furthermore, the fourth column of Table 7.4 shows that HAU only depends on base layer and content-based features of the highest quality/resolution images, while cryptographic authentication and watermarking-based authentication must involve every layer of SVC to prevent the attacks on unprotected layers. In the fifth column of Table 7.4, cryptographic authentication and watermarking-based authentication