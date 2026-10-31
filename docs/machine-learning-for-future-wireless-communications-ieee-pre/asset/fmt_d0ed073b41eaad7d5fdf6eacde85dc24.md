
where `r[t]` represents the received signal at time `t`, `s[t]` is the transmitted symbol, `n` stands for additive white Gaussian noise (`AWGN`), and `h[t]` denotes the channel gain. Due to feedback and processing delays, the channel condition at the time of selecting adaptive transmission parameters may be outdated before its actual usage, namely `h[t] ≠ h[t+τ]`, where `τ` denotes the delay. Outdated `CSI` imposes a severely negative impact on a wide variety of adaptive transmission systems. The aim of channel prediction is to get a predicted gain `ĥ[t+τ]` that is as close as possible to its actual value `h[t+τ]` at the instant `t+τ` when the actual transmission using the selected parameters happens.

### 16.5.2.1 Channel Gain Prediction with a Complex-Valued RNN

Since channel gains are complex-valued, a `RNN` with complex-valued weights (called a `complex-valued RNN` hereinafter) needs to be applied (Liu et al., [2006](#c16.xhtml#c16-bib-0025), Potter et al., [2008](#c16.xhtml#c16-bib-0031), Ding and Hirose, [2014](#c16.xhtml#c16-bib-0008)). At time `t`, `h[t]` is obtained through channel estimation, for example, while a number of `d` past values `h[t-1], h[t-2], ..., h[t-d]` can be stored through a tapped delay line, as illustrated in `Figure 16.6`. These `d+1` channel gains are fed into the `RNN` as the external input, i.e.

![Figure 16.6 (a) Schematics of applying a complex-valued recurrent neural network to predict one-step-ahead channel state information images; (b) applying a real-valued RNN to predict a channel gain by means of processing the real and imaginary parts separately.](images/c16f006.jpg)

`Figure 16.6` (a) Schematics of applying a complex-valued recurrent neural network to predict one-step-ahead channel state information `ĥ[t+1]`; (b) applying a real-valued RNN to predict a channel gain by means of processing the real and imaginary parts separately.

`(16.32)` `x_e[t] = [h[t], h[t-1], ..., h[t-d]]`

With the aid of the delayed feedback, the prediction of a future channel gain `ĥ[t+1]` at the next time instant `t+1` is obtained, as shown in `Figure 16.6`.

### 16.5.2.2 Channel Gain Prediction with a Real-Valued RNN

In comparison with a complex-valued RNN, a `RNN` with real-valued weights (called a `real-valued RNN`) has the advantages of lower computational complexity and higher prediction accuracy, but it can only deal with real-valued input. Fortunately, a complex-valued channel gain can be decomposed into two real values, namely the real and imaginary parts, i.e. `h = h^r + j h^i`, where `j^2 = -1` is the imaginary unit. Therefore, a real-valued RNN was proposed in (Jiang and Schotten, [2018a](#c16.xhtml#c16-bib-0015)) to build a simpler predictor with higher accuracy by means of separately predicting the real and imaginary parts and then combining them together. As shown in `Figure 16.6`, the external input of the `RNN` is then
