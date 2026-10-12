
## 4.4 Signal Segmentation

Often it is necessary to label the EEG signals into segments of similar characteristics, particularly meaningful to clinicians and for assessment by neurophysiologists. Within each segment, the signals are considered statistically stationary, usually with similar time and frequency statistics. As an example, an EEG recorded from an epileptic patient may be divided into three segments: preictal, ictal, and postictal. Each may have a different duration. [Figure 4.1](#c04.xhtml#c4-fig-0001) represents an EEG sequence including all the above segments.

![Figure 4.1 An EEG set of tonic–clonic seizure signals including three segments of preictal, ictal, and postictal behaviour.](images/c04f001.gif)

[**Figure 4.1**](#c04.xhtml#R_c4-fig-0001) An EEG set of tonic–clonic seizure signals including three segments of preictal, ictal, and postictal behaviour.

In segmentation of EEGs, time or frequency properties of the signals may be exploited. This eventually leads to a dissimilarity measurement denoted as `d(m)` between adjacent EEG frames, where `m` is an integer value indexing the frame and the difference is calculated between the `m` and `(m − 1)`th (consecutive) signal frames. The boundary of the two different segments is then defined as the boundary between the `m` and `(m − 1)`th frames provided `d(m) > η[T]`, where `η[T]` is an empirical threshold level. An efficient segmentation is possible by highlighting and effectively exploiting the diagnostic information within the signals with the help of expert clinicians. However, access to such experts is not always possible; therefore, there is a need for algorithmic methods.

A number of different dissimilarity measures may be defined based on the fundamentals of signal processing. One criterion is based on the autocorrelations for segment `m` defined as:

**Equation (4.7)**
```
r_x(k, m) = E[x(n, m) x(n + k, m)]
```

The autocorrelation function of the `m`th length `N` frame for an assumed time interval `n, n + 1, …, n + (N − 1)` can be approximated as:

**Equation (4.8)**
```
r̂_x(k, m) = {
    (1/N) Σ_{l=0}^{N-1-k} x(l + m + k) x(l + m),  k = 0, …, N-1
    0,                                             k = N, N+1, …
}
```

Then the criterion is set to:

**Equation (4.9)**
```
d_1(m) = [ Σ_{k=-∞}^{∞} (r̂_x(k, m) - r̂_x(k, m-1))^2 ] / [ r̂_x(0, m) r̂_x(0, m-1) ]
```
