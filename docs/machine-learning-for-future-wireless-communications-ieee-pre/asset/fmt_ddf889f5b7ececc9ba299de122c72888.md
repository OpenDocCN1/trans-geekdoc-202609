
Another similar work is shown in (Doan et al., [2018](#c14.xhtml#c14-bib-0005)). In this paper, the authors propose `NSC` (neural `SC`) decoding, which is constructed of multiple `NNDs` connected with `SC` decoding in a way similar to the previous paper (Cammerer et al., [2017](#c14.xhtml#c14-bib-0003)). The result shows that the `NSC` decoder has similar `BER` and `FER` performance in comparison with `PNN` in (Cammerer et al., [2017](#c14.xhtml#c14-bib-0003)), `SC`, and `BP` decoders. However, from the perspective of complexity, the `NSC` decoder can reduce the number of time steps required for the `PNN` decoder with the same error‐correction performance. The decoding architecture (`N=8`) is shown in [Figure 14.9](#c14.xhtml#c14-fig-0009). For more detailed information, readers can refer to (Doan et al., [2018](#c14.xhtml#c14-bib-0005)).

### 14.2.3 DNNs for Joint Equalization and Channel Decoding

In addition to channel decoding, training multiple modules (such as equalization and decoding) simultaneously in a communication system has also become a subject of research. This is because neural networks (such as `DNNs`) are essentially black boxes that can simultaneously learn the features of these modules.

In practical communication systems, inter‐symbol interference (`ISI`) exists because the channel has memory and nonlinear distortions that are introduced by amplifiers and converters. Channel equalization is used to deal with `ISI` and recover the transmitted signals. But the noise will no longer be Gaussian white noise after the equalization step. As a result, it is hard to make sure performance is still good when considering equalization and decoding. Instead, a `DL`‐based approach for joint consideration of these two steps may deal with this problem.

![Figure 14.10 The architecture for jointly equalizing and decoding using neural networks.](images/c14f010.jpg)

[Figure 14.10](#c14.xhtml#R_c14-fig-0010) The architecture for jointly equalizing and decoding using neural networks.

The initial results on this subject are shown in (Hao Ye, [2017](#c14.xhtml#c14-bib-0012)). [Figure 14.10](#c14.xhtml#c14-fig-0010) is the schematic architecture of this proposed solution for `NN`‐based joint equalization and decoding. We can see that all the equalization and decoding parts are replaced by neural networks, which can realize a one‐shot equalization and decoding approach. Under this circumstance, the authors consider two scenarios: dispersive channels with nonlinear distortion, the frequency‐selective time‐varying channels.

The input data of the network is the received signal `y` suffering from `ISI`, and the original messages `b` serve as the true labels. The loss function is `MSE` to measure performance.

In the first scenario, e.g. dispersive channels with nonlinear distortion, let us use ![images](images/c14-i0012.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><mi>g</mi></mrow></math>, ![images](images/c14-i0013.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><mi>h</mi></mrow></math> to denote the nonlinear function caused by amplifiers and the channel impulse response, respectively. As an illustration example, the channel impulse ![images](images/c14-i0014.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><mi>h</mi></mrow></math> can be:

(14.3)![equation](images/c14-math-0003.png)<math display="block" xmlns="http://www.w3.org/1998/Math/MathML" overflow="scroll"> <mrow> <mtable> <mtr> <mtd> <mi>h</mi> <mo stretchy="false">(</mo> <mi>z</mi> <mo stretchy="false">)</mo> <mo>=</mo> <mn>0.3482</mn> <mo>+</mo> <mn>0.8704</mn> <msup> <mi>z</mi> <mrow> <mo>&#8722;</mo> <mn>1</mn> </mrow> </msup> <mo>+</mo> <mn>0.3482</mn> <msup> <mi>z</mi> <mrow> <mo>&#8722;</mo> <mn>1</mn> </mrow> </msup> </mtd> </mtr> </mtable> </mrow> </math>

while the nonlinear distortion function of the channel is:

(14.4)![equation](images/c14-math-0004.png)<math display="block" xmlns="http://www.w3.org/1998/Math/MathML" overflow="scroll"> <mrow> <mtable> <mtr> <mtd> <mo stretchy="false">&#124;</mo> <mi>g</mi> <mo stretchy="false">(</mo> <mi>v</mi> <mo stretchy="false">)</mo> <mo stretchy="false">&#124;</mo> <mo>=</mo> <mo stretchy="false">&#124;</mo> <mi>v</mi> <mo stretchy="false">&#124;</mo> <mo>+</mo> <mn>0.2</mn> <mo stretchy="false">&#124;</mo> <mi>v</mi> <msup> <mo stretchy="false">&#124;</mo> <mn>2</mn> </msup> <mo>&#8722;</mo> <mn>0.1</mn> <mo stretchy="false">&#124;</mo> <mi>v</mi> <msup> <mo stretchy="false">&#124;</mo> <mn>3</mn> </msup> <mo>+</mo> <mn>0.5</mn> <mi>c</mi> <mi>o</mi> <mi>s</mi> <mo stretchy="false">(</mo> <mi>&#960;</mi> <mo stretchy="false">&#124;</mo> <mi>v</mi> <mo stretchy="false">&#124;</mo> <mo stretchy="false">)</mo> </mtd> </mtr> </mtable> </mrow> </math>

A six‐layer `DNN` with (16, 256, 128, 64, 32, 8) is used in the previous reference to jointly equalize and decode polar codes with size (16, 8). In terms of `BER` performance, this joint solution is compared with a baseline system that uses a Gaussian process for classification (`GPC`) algorithm for equalization and a `SC` algorithm for decoding. Under this channel model, the performance of the `DNN` is better than the baseline `GPC+SC` system, with a gain of about 1‐2 dB; this shows the advantages of the `DNN` approach.

In the second scenario, frequency‐selective time‐varying channels are considered, where channel responses are constantly changing. In this scenario, a `DNN` model is trained to decode information under an `OFDM` system, where channel estimation is achieved simultaneously. An `OFDM` system with 64 subcarriers and 16 cyclic‐prefixes is used. In this reference work, `QAM` serves as the the modulation method, and 16 pilots are used for channel estimation. The `DNN` model is the same as the former one, other than the number of inputs being changed to fit the number of `OFDM` symbols.

The authors of this reference work compare the proposed `DL`‐based detection method with a traditional `MMSE` estimator with identity matrix (`MMSE-I`) and `MMSE` estimator with perfect channel statistics information (`MMSE-S`). The `DL` method outperforms the `MMSE-I` method, but there is still a performance gap compared to `MMSE-S`. As for decoding, the `DL`‐based method has better performance compared to `MMSE` with the `SC` decoder, which shows the advantage of using a neural network to take both detection and decoding into consideration. Readers can refer to (Hao Ye, [2017](#c14.xhtml#c14-bib-0012)) to see detailed simulation results.

![Figure 14.11 System architecture for equalizing and decoding, respectively.](images/c14f011.jpg)

[Figure 14.11](#c14.xhtml#R_c14-fig-0011) System architecture for equalizing and decoding, respectively.

To further improve performance, another paper (Xu et al., [2018](#c14.xhtml#c14-bib-0029)) proposes a joint channel equalizer and decoder. Unlike the previous architecture, they use a `CNN` for equalization and a `DNN` for decoding, respectively. The architecture is shown in [Figure 14.11](#c14.xhtml#c14-fig-0011).

The `CNN` equalizer is first used to compensate for the signal distortion. Then the other polar `DNN` decoder is concatenated after the `CNN` to decode the recovered sequence. The reason for using `CNN` for equalization is that a `CNN` has strong feature‐extraction capabilities. `CNNs` can deal with the nonlinear channel model, since `ISI` exists only between consecutive bits of the transmitted sequence, and the effects of nonlinear distortion are independent for each bit.

Under the circumstances of channel equalization, the input format of `CNN` is a 1‐D vector instead of a typical 2‐D image in the field of image processing. Then a multiple‐layer `DNN` can be used to decode the output of the `CNN` network equalizer. In other words, the input of the `DNN` is a 1‐D vector from the `CNN` equalizer.
