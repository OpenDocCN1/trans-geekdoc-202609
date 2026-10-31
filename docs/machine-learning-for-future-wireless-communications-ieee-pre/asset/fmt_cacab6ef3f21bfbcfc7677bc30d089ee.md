
[Figure 19.5](#c19.xhtml#c19-fig-0005)b presents the average delay per `UT` against `V` for `PMOS`. It can be observed that the average delay experienced by per `UT` increases linearly with the control parameter `V`, which along with the observations in [Figure 19.5](#c19.xhtml#c19-fig-0005)a verifies the `O(1/V), O(V)` trade-off between average network throughput and average queue backlog derived in Theorem 1. This indicates that a proper `V` should be chosen to balance these two objects. We also observe that `PMOS` always generates a smaller average delay than the multi-tier operations scheduling without prediction (`D = 0`). As the predictive window size `D` increases, the average delay per `UT` decreases almost linearly in `D`, which is in accordance with the theoretical analysis in Theorem 4. The reason behind those observations is that the predictive information helps the operator design a better `FAN` assignment and bandwidth allocation strategy, which utilizes the network more efficiently.

## 19.5 A Multi‐tier Cost Model for User Scheduling in Fog Computing Networks

Although different aspects of user scheduling in multi‐tier fog computing networks have been widely discussed in the literature, such as Zhao et al. ([2018](#c19.xhtml#c19-bib-0057)), Shah‐Mansouri and Wong ([2018](#c19.xhtml#c19-bib-0039)), Liu et al. ([2018b,a](#c19.xhtml#c19-bib-0027)), the effective user scheduling scheme still faces challenges, especially when the cost model is considered. Generally, the `FCN` is operated by a telecom operator that signs a service contract with `UTs`, while the `FANs` belong to different individuals. To better motivate `FANs` to share resources and anticipate in caching, the cost model, especially for `FANs`, should be taken into consideration.

### 19.5.1 System Model and Problem Formulation

#### System Model

Just like [Figure 19.1](#c19.xhtml#c19-fig-0001), a multi‐tier fog computing network consisting of one `FCN`, `M` `FANs`, and `N` `UTs` is considered. As mentioned, the `FCN` is operated by a telecom service provider, which provides services to `N` `UTs`, i.e. service subscribers, while the `FANs` belong to different individual owners. To reduce service delay and improve `QoS`, the `FCN` is willing to pay money to `FANs` if they provide services to `UTs`. For ease of expression, we take caching as an example in the following context. [1](#c19.xhtml#c19-note-0001) In the fog‐enabled caching network, the `FCN` can allocate files to `FANs` during off‐peak time, i.e. file placement, and thus the `UTs` can be associated with proper `FANs` or `FCN` to download files during peak time, i.e. user scheduling.

![Figure 19.5 Performance comparison of PMOS and FEMOS,images, images.](images/c19f005.jpg)

[Figure 19.5](#c19.xhtml#R_c19-fig-0005) Performance comparison of `PMOS` and `FEMOS`, `A_max = 100 kbits`, `e = 0`.
