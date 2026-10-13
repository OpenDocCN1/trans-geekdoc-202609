
Figure 10.14 Each atom of the Gabor dictionary corresponds to a node in the time-frequency grid. That is, it is a sampled windowed sinusoid whose frequency and location in time are given by the coordinates of the respective node. In practice, this grid may be subsampled by factors `α` and `β` for the two axes, respectively, in order to reduce the number of the involved atoms.

Note that the windowing of a signal of finite duration inevitably introduces boundary effects, especially when the delay `m` gets close to the time segment edges, `0` and `l − 1`. A solution that facilitates the theoretical analysis is to use a modulo `l` arithmetic to wrap around at the edge points (this is equivalent to extending the signal periodically); see, for example, [113].

Once the atoms have been defined, they can be stacked one next to the other to form the columns of the `l × l²` Gabor dictionary, `G`. It can be shown that the Gabor dictionary is a tight frame [125].

### Time-frequency resolution

By definition of the Gabor dictionary, it is readily understood that the choice of the window spread, as measured by `σ`, must be a critical factor, since it controls the localization in time. As known from our Fourier transform basics, when the pulse becomes short, in order to increase the time resolution, its corresponding frequency content spreads out, and vice versa. From Heisenberg's principle, we know that we can never achieve high time and frequency resolution simultaneously; one is gained at the expense of the other. It is here where the Gaussian shape in the Gabor transform is justified. It can be shown that the Gaussian window gives the optimal tradeoff between time and frequency resolution [57,87]. The time-frequency resolution tradeoff is demonstrated in [Fig. 10.15](#Chp010_463-518_B9780443292385000160.xhtml#f0080), where three sinusoids are shown windowed with different pulse durations. The diagram shows the corresponding spread in the time-frequency plot. The value of `σ[t]` indicates the time spread and `σ[f]` the spread of the respective frequency content around the basic frequency of each sinusoid.

![Figure 10.15 The shorter the width of the pulsed (windowed) sinusoid is in time, the wider the spread of its frequency content around the frequency of the sinusoid. The Gaussian-like curves along the frequency axis indicate the energy spread in frequency of the respective pulses. The values of σt and σf indicate the spread in time and frequency, respectively.](images/B9780443292385000160/gr015.jpg)

[Figure 10.15](#Chp010_463-518_B9780443292385000160.xhtml#cf1000) The shorter the width of the pulsed (windowed) sinusoid is in time, the wider the spread of its frequency content around the frequency of the sinusoid. The Gaussian-like curves along the frequency axis indicate the energy spread in frequency of the respective pulses. The values of `σ[t]` and `σ[f]` indicate the spread in time and frequency, respectively.

### Gabor frames

In practice, `l²` can take large values, and it is desirable to see whether one can reduce the number of the involved atoms without sacrificing the frame-related properties. This can be achieved by an appropriate subsampling, as illustrated in [Fig. 10.14](#Chp010_463-518_B9780443292385000160.xhtml#f0075). We only keep the atoms that correspond to the red nodes. That is, we subsample by keeping every `α` nodes in time and every `β` nodes in frequency in order to form the dictionary, that is,

```
G_(α,β) = {g^(mα,iβ)},  m = 0,1,…,l/α − 1,  i = 0,1,…,l/β − 1,
```

where `α` and `β` are divisors of `l`. Then it can be shown (e.g., [57]) that if `αβ < l` the resulting dictionary retains its frame properties. Once `G(α,β)` is obtained, the canonical dual frame is readily available via Eq. (10.46) (adjusted for complex data) of the appendix associated with the chapter (which can be downloaded from the book's website), from which the corresponding set of expansion coefficients, `θ`, results.

### Time-frequency analysis of echolocation signals emitted by bats

Bats use echolocation for navigation (flying around at night), for prey detection (small insects), and for prey approaching and catching; each bat adaptively changes the shape and frequency content of its calls in order to better serve the previous tasks. Echolocation is used in a similar way for sonars. Bats emit calls as they fly, and “listen” to the returning echoes in order to build up a sonic map of their surroundings. In this way, bats can infer the distance and the size of obstacles as well as of other flying creatures/insects. Moreover, all bats emit special types of calls, called social calls, which are used for socializing, flirting, and so on. The fundamental characteristics of the echolocation calls, for example, the frequency range and average time duration, differ from species to species because, thanks to evolution, bats have adapted their calls in order to become better suited to the environment in which a species operates.
