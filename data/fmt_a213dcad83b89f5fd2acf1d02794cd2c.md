
- [26] G. Piro, G. Boggia, L.A. Grieco, in: 符合 IEEE 802.15.4 网络的标准安全框架, Proceedings of IEEE World Forum on Internet of Things (WF-IoT), Seoul, South Korea, 2014, pp. 27–30.
- [27] J.-Y. Lee, W.-C. Lin, Y.-H. Huang, in: 面向物联网的轻量认证协议, 2014 International Symposium on Next-Generation Electronics, ISNE 2014, Kwei-Shan, 2014, pp. 1–2.
- [28] M. Turkanovi, B. Brumen, M. Hibl, 基于物联网概念的异构自治无线传感器网络的新型用户认证和密钥协议方案, Ad Hoc Netw. 20 (2014) 96–112.
- [29] N. Ye, Y. Zhu, R.-C.B. Wang, R. Malekian, Q.-M. Lin, 感知层的高效认证和访问控制方案, Appl. Math. Inf. Sci. 8 (4) (2014) 1617–1624.
- [30] A. Cherkoua, L. Bossuet, L. Seitz, G. Selander, R. Borgaonkar, in: 受约束环境中的访问控制新范式, 2014 9th International Symposium on Reconfigurable and Communication-Centric Systems-on-Chip (ReCoSoC), Montpellier, 2014, pp. 1–4.
- [31] S. Sicari, A. Rizzardi, C. Cappiello, A. Coen-Porisini, in: 面向物联网应用的 NEP 模型, Proceedings of IEEE WiMob, Larnaca, Cyprus, 2014, pp. 164–171.
- [32] X. Wang, J. Zhang, E. Schooler, M. Ion, in: 基于属性加密的性能评估：面向物联网的数据隐私, 2014 IEEE International Conference on Communications, ICC 2014, Sydney, NSW, 2014, pp. 725–730.
- [33] J. Su, D. Cao, B. Zhao, X. Wang, I. You, ePASS：具有隐私性和不可伪造性保证的属性基签名方案用于物联网, Futur. Gener. Comput. Syst. 33 (2014) 11–18.
- [34] L.B. Peng, W.B. Ru-chuan, S. Xiao-yu, C. Long, 基于密钥变更的互认认证协议在物联网中的隐私保护, Commun. Comput. Inf. Sci. 418 (CCIS) (2014) 345–355.
- [35] A. Ukil, S. Bandyopadhyay, A. Pal, in: 物联网隐私：是否要保持私密或不保持私密, Proceedings of IEEE INFOCOM, Toronto, ON, 2014, pp. 123–124.

# CHAPTER 14: Outlier Discrimination and Correction in Intelligent Transportation Systems

**Junqin Huang, Linghe Kong, and Guihai Chen**  
Shanghai Jiao Tong University, Shanghai, China

## 1 INTRODUCTION

The rapid growth of vehicles brings the problem of traffic congestion. Shanghai, New York, and Paris, for example, which are the largest cities in the world, suffer from constant traffic congestion. It is essential for drivers to check the traffic conditions before going out via navigation applications such as `AMAP`, `Google Maps`, `Baidu Map`, and so forth.

Traditionally, these navigation applications have provided traffic conditions by collecting location data from users or in-vehicle sensing devices in real time. Due to its openness, malicious users could upload fake data to the data center intentionally, which would make navigation applications provide misleading traffic information. As a result, the transportation system falls into chaos. On the other hand, hardware heterogeneity and failure [1] may cause bias or missing information in collected location data.

In Fig. 1, a snapshot of the road network in downtown Chengdu, which we research in this chapter, is shown. We collect traffic condition data of these roads from `AMAP` [2] every 5 min for 24 h. Fig. 2 shows the missing ratio of traffic condition data. By statistics, 42% of the total data are missing. The large missing ratio and potential faulty values increase the misleading traffic information. It is significant to discriminate the outliers to guarantee an efficient transportation system, which motivates us to propose a novel method to address it.

Lots of work has been contributed to this field, such as Yoon et al. [3] utilize traffic patterns on a specific road segment to estimate traffic conditions, which needs large datasets in identifying traffic conditions, and each road, which is analyzed independently, is not suitable for the real-time environment (e.g., navigation applications). Li et al. [4] propose a compressive sensing-based method to estimate missing values in urban traffic sensing; however, this method does not take faulty data into consideration, which may lead to reconstruction deviation. Cheng et al. [5] propose a `DECO` framework to improve data quality for crowd-sensing applications. They believe users who have a good reputation will not upload faulty data, which is impractical, too. In summary, although some algorithms and methods are proposed to address such problems, few of them are practical in real life.

In this chapter, we propose an outlier discrimination and correction (`ODC`) method to discriminate faulty data and reconstruct missing data in traffic condition datasets. Through simulations conducted on traffic condition datasets from `AMAP`, we observe that `ODC` can produce only about a 6 km/h reconstruction error, even with a missing data ratio `β = 50%` and faulty data ratio `α = 30%`.

Our contributions can be summarized as follows:

- We propose the `ODC` method, which is applied to outlier detection and missing data reconstruction in the field of traffic information. It only uses single dimension information, that is, the average speed for analysis, so it takes very little time and is suitable for real time applications.
- We mine temporal stability and spatial correlation features from traffic condition datasets, and utilize these hidden structures to improve performance of compressive sensing.
- We evaluate `ODC` based on real urban traffic condition datasets, demonstrating that it produces low reconstruction errors, even when the missing ratio is 50% and the faulty ratio is 30% in traffic condition datasets.

The rest of this chapter is organized as follows. In Section 2, we formulate the problem. In Section 3, we analyze the hidden structures in traffic condition datasets. The compressive sensing-based method, `ODC`, is proposed in Section 4. In Section 5, we evaluate the `ODC` method through real urban traffic traces. We introduce related work in Section 6 and conclude this chapter in Section 7.

## 2 PROBLEM FORMULATION

The better traffic conditions are, the higher the driving speed allowed, so we adopt the mean velocity of roads as the metric for quantifying traffic conditions in this chapter. As shown in Fig. 1, the road network consists of `n` roads (different directions of the same road are considered different roads). The sensing period includes `t` time slots. Each road updates its mean velocity once per time slot by calculating real-time changes of location data from users. `x(i, j)` denotes the mean velocity of road `i` at time slot `j`, where `i = 1, 2, ..., n` and `j = 1, 2, ..., t`.

**Definition 1. Traffic Condition Matrix (TCM)** describes the mean velocity of road `i` in time slot `j`. `TCM` is defined by `X = (x(i, j))_{n×t}`.

Each line of `X` represents a time series of mean velocity of one road. And every data point is valid, that is, no missing or faulty data points.

**Definition 2. Direct Sensory Matrix (DSM)** is an `n × t` matrix, which contains mean velocity calculated through raw data, where we may find missing or faulty data points. `DSM` is denoted by `S`, defined as follows:

```
S(i, j) = (s(i, j))_{n×t} = { 0 if x(i, j) is missing; x(i, j) + ξ otherwise } (1)
```

Data error is denoted by `ξ`, `s(i, j)` is considered a faulty data point if `|ξ| > η`, where `η` is a predefined threshold, otherwise as a normal one.

**Definition 3. Faulty Matrix (FM)** is an `n × t` matrix, denoted by `F`, set `F(i,j)` to 1 if `s(i,j)` is faulty, defined as:

```
F(i,j) = { 1 if s(i,j) is faulty; 0 otherwise } (2)
```

**Definition 4. Existence Matrix (EM)** is denoted by `E`, represents if `x(i,j)` is collected in `S`, defined as:

```
E(i,j) = (ε(i,j))_{n×t} = { 0 if x(i,j) is not in S; 1 otherwise } (3)
```

**Definition 5. Faulty Data Detection Matrix (FDM)** is an `n × t` matrix, denoted by `D`, marks out the faulty data detected through the `ODC` method, defined similar to `F`.

**Definition 6. Reconstruct Matrix (RM)** is generated by interpolating the missing or faulty values in `DSM` to approximate to `TCM`. `RM` is defined by `\hat{X}=(\hat{x}(i,j))_{n×t}`.

**Definition 7. Binary Index Matrix (BIM)** combines `E` and `D`, marks out trusted data, that is, not missing or faulty data. `BIM` is denoted by `B`, defined as:

```
B = (b(i,j))_{n×t} = E ∩ \overline{D} (4)
```

The first problem is to detect faulty data in `S`, formulated as:
