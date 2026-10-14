
## 7.4.1.1 Motivation

An authentication scheme aims to prevent any unauthorized manipulations by verifying the integrity and source of data. In addition to the standard requirements of security, computational efficiency and communication efficiency, an authentication scheme for SVC codestreams should also provide the following properties:

- Robustness: robust or resilient to content-preserving manipulations which do not change the semantic meaning of a codestream.
- Sensitivity: able to detect content-changing manipulations which modify the semantic meaning of a codestream.
- Localization of tampering: able to pinpoint tampered regions if tampering indeed occurred.
- Scalability: preserving the scalability properties of the original SVC codestream. That is, the authentication scheme authenticates an SVC codestream once at the source, but allows verification of the codestream with different scalabilities by various user devices.

## 7.4.1.2 Hybrid Authentication Scheme of Scalable Video Coding

In an SVC codestream, the base layer consists of the lowest quality/resolution images, and it must be transmitted intact to the receiver in any case. Meanwhile, it is unnecessary to transcode (i.e., re-compress or re-sample) the base layer because it contains the very basic information. Therefore, the base layer can be protected by cryptographic authentication. Meanwhile, higher quality and resolution images are decoded from base layer and enhancement layers, and their content-based features are robust. If features are extracted from the highest quality and resolution images, content-based authentication is suitable for authenticating enhancement layers. Hence, it is reasonable to integrate cryptographic authentication and content-based authentication techniques in order to flexibly authenticate SVC codestreams. Operations of HAU are shown in Figure 7.13, where the provider creates an

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_225_0.png)

Figure 7.13 Diagram of HAU.

authentication tag for an SVC codestream and the receiver verifies the tag against the received codestream. MANE which receives feedback messages about the terminal capabilities and/or channel conditions, can remove the non-required parts from a scalable bit stream based on its DxQyTz, before forwarding it.

### 7.4.1.2.1 Authentication Tag Generation

The authentication tag generation process includes MAC generation and feature extraction, where MACs are constructed by taking the encoded image of the base layer and a secret key as inputs, while the features of each frame are extracted from the highest quality and resolution images of SVC bitstreams. Note that if an SVC codestream has spatial enhancement layers, HAU should initially downsample the largest resolution to the same resolution as the base layer, then extract features from the downsampled one. Hence, the length of the feature value is related to the base layer's resolution for each AU (Access Unit).

### Message Authentication Codes:

With a standard one-way hash function $\mathcal{H}(\cdot)$ for the encoded frame $\Phi$, the provider takes its base layer $\Phi_b$ and a key $k_b$ shared by provider and receiver as input to produce MAC $\varphi$ as:

$$\varphi = \mathcal{H}(k_b, \Phi_b)$$

### Feature Extraction:

HAU extracts content-based features which are sensitive to content-changing manipulation but robust to content-preserving manipulations in case of large QP. The candidate features include invariant histogram statistics and relation between low frequency DCT coefficients. HAU employs NMF-NMF-SQ (Non-negative matrix factorisation square) hashing to produce content based feature. After obtaining the hash vector $h$ of each AU, pseudorandom weight vectors $\{t_i\}_{i=1}^{u} (u \le v)$ are generated using AES with the secret key $k_e$ and an initialization vector IV. The $k_e$ is shared by the content sender and receiver and the initialization vector IV consists of scalable information (i.e., temporal identifiers) and slice header of base layer. At last, HAU executes inner product of vector $\mathbf{h}$ and vector $t_i$ to produce $V = \{V_1, V_2, \cdots, V_u\}$.

### 7.4.1.2.2 Tag Conveyance

It is necessary to deliver the authentication tag (i.e., feature hash $V$ and MAC $\varphi$) to the receiver together with the SVC codestream for verification. In HAU, we encapsulate the tag into SVC user data as a new SEI (Supplemental Enhancement Information) NALU. The payload type of the new SEI is Unregistered User Data Message so as to preserve SVC format. After receiving the SVC codestream embedded with the tag, the receiver can detect the new SEI based on its UUID

(Universally Unique Identifier) and directly obtain the tag, i.e., NMF-NMF-SQ hash and MAC.

### 7.4.1.2.3 Tag Verification

After receiving the codestream and obtaining the tag, the receiver performs HAU verification including the base layer verification and enhancement layer verification.

**Verification of the Base Layer:** For the base layer Ψ_b in a received frame Ψ, HAU first calculates its MAC value ψ as

ψ = ℋ(k_b, Ψ_b)

If ψ = φ, HAU accepts the base layer. Otherwise, the base layer is considered tampered and HAU directly rejects the base layer and all the enhancement layers of Ψ.

## 7.4.1.3 Experiments and Comparison

In our experiments, we choose twelve standard benchmark video sequences in order to cover different combinations of video characteristics, including motion (fast/slow, pan/zoom/rotation), color (bright/dull), contrast (high/low), and object type (vehicle, buildings, people). Bus (150 frames) and Foreman (300 frames) are of less camera motion while Football (260 frames), Container (300 frames) and Soccer (300 frames) demonstrate camera panning and zooming with object motion and background texture. Bridge-far (300 frames) and Bridge-close (500 frames) show images with smooth motion. Highway (1200 frames) is a sequence of fast motion while Silent (300 frames) and News (300 frames) are static sequences except of motion of partial fields. Mobile (300 frames) and Hall (300 frames) sequences display a still complex background with foreground motion. SVC GOP size and Intra period are set to 8; the QPs of enhancement layers are no more than 38 so that the features extracted with NMF-NMF-SQ are stable.

As HAU exploits the characteristics of SVC to ensure its authenticity, it is robust to content-preserving manipulations but sensitive to content-changing manipulations of enhancement layers. However, cryptographic authentication is sensitive to any bit change of SVC and watermarking-based is semi-fragile to content-preserving manipulations. In other words, HAU achieves a good balance between robustness and sensitivity as shown in the second column of Table 7.4. The third column indicates that cryptographic authentication cannot locate tampered areas. Furthermore, the fourth column of Table 7.4 shows that HAU only depends on base layer and content-based features of the highest quality/resolution images, while cryptographic authentication and watermarking-based authentication must involve every layer of SVC to prevent the attacks on unprotected layers. In the fifth column of Table 7.4, cryptographic authentication and watermarking-based authentication

## Table 7.4 Comparison with Other H.264/SVC Authentication Schemes

| Scheme | Robustness/Sensitivity | Tampered Location | Authentication Operation | Dependence on SVC Structure | Communication Overhead |
|---|---|---|---|---|---|
| Cryptographic authentication [10] | Sensitive to any bit change | No | All layer hash | Yes | Quality scalability 2.19%<br>Spatial scalability 2.62% |
| Watermarking authentication [14] | Semi-fragile | Yes | All layer watermarking | Yes | Quality scalability 8.66%<br>Spatial scalability 2.93% |
| HAU | Sensitive to base layer change robust to enhancement layers | Yes | Base layer hash content-based features | No | Quality scalability 2.42%<br>Spatial scalability 2.16% |
