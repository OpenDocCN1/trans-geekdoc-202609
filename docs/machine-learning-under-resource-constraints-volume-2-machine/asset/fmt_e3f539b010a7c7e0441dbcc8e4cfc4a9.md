
## Abstract

In astroparticle physics, we naturally face machines with long lifetimes and long-running processes since a detector instrument such as a telescope is often built, used, and maintained for several decades. Thus, it is imperative to monitor the behavior of the detector in order to assure a certain data quality during its lifetime. While operators closely monitor the behavior of their detectors, they cannot possibly review, e.g., 60 events per second in real time. However, a small and well-chosen sample of the measurements can help to monitor the behavior of the detector and pinpoint unexpected results early in the processing pipeline. To be meaningful, such a data summary must be small, comprehensive, and computed on time. Due to their compelling theoretical properties, submodular functions have been the focus of data summarization algorithms as they naturally capture many aspects of data summarization while offering theoretical guarantees. However, one challenge in applying submodular functions for data summarization in astrophysics is the data representation. As we will discuss, submodular functions require a notion of similarity between measurements to select the most informative events from the data stream for the summary. Thus, an appropriate representation of the events must be obtained before the summary selection. Such a representation can be obtained through autoencoders, which embed the high-dimensional raw feature space into a meaningful lower-dimensional embedding space. However, there is no guarantee that the embedding space is well suited for data summarization. In this section, we will first review submodular functions in the context of data summarization and then present an autoencoder algorithm that computes embeddings that are tailored to the summarization tasks.

## 7.4.1 Introduction

Astroparticle physics experiments naturally deal with large volumes of data measured over years of continuous observation. Over time, the measurements are subjected to a natural concept drift by, say, broken sensors, changes in the environment, or changes in the telescope's operation. Thus, the health status and the actual observations must be closely monitored to detect changes and interesting events early on.

While numerous concept drift detection mechanisms exist, they do not give direct feedback to the operator by, say, characterizing the type of concept drift occurring. One way to visualize large amounts of data and possible concept drifts is to give a human operator a small, comprehensive summary of the measurements. This way, the operator can interact with the data by looking at the data summary and directly reason about possible changes in the data or detector.

Submodular optimization has become a valuable tool in machine learning and data mining. Submodular functions reward adding a new element to a smaller set more than adding the same element to a larger set. This makes them ideal for solving data summarization tasks in which a submodular set function `f` assigns a utility score `f(S)` to a summary `S`. Then, using submodular maximization, the optimal summary can be selected. Submodular functions designed for data summarization utilize a notion of distance between two observations `x[i]` and `x[j]`. Unfortunately, distance metrics lose their expressiveness with higher dimensions, so data summarization through submodular optimizations becomes more and more difficult with increasing numbers of dimensions [[82]](#9783110785951_034588.xhtml#b_9783110785968-011_ref_082).

One way to circumvent this problem is to embed the high-dimensional data into a lower-dimensional embedding space. To do so, we can use a specialized Deep Learning architecture (see [Chapter 9](#9783110785951_027842.xhtml#b_9783110785968-009)) called autoencoders that consists of two parts, namely the encoder and the decoder. The encoder tries to encode the data into a lower-dimensional space, whereas the decoder tries to reconstruct the original data from the output of the encoder. Both parts are trained jointly in an end-to-end fashion so that the encoder tries to encode most of the information about the data into the lower-dimensional space. By contrast, the decoder tries to reconstruct the original data as much as possible (see [[183]](#9783110785951_034588.xhtml#b_9783110785968-011_ref_183), Chapter 14). Autoencoders and their variations have been studied extensively with great practical success for embedding tasks. Unfortunately, while autoencoders perform well, there is no guarantee that the embedding space retains the same notion of similarity as the original data space. Simply put, there is no way to guarantee that objects that are close in the original space are still close to each other in the embedding space, making it difficult to use them with data summarization techniques.

In this section, we discuss how to apply autoencoders for subsequent data summarization. First, we introduce the framework of submodular functions in the next section. Then, we discuss autoencoders in general and their application to the related tasks of cluster analysis. From these clustering autoencoders, we derive submodular autoencoders specifically targeted for data summarization tasks. Finally, we present experimental summaries of the FACT data and conclude the section.

## 7.4.2 Data Summarization with Submodular Functions

Submodular optimization offers a well-established mathematical framework to select small and comprehensive summaries for various tasks in linear time. Formally, we consider the problem of selecting `K` representative elements from a ground set `V` into a summary set `S ⊆ V`. To do so, we maximize a non-negative, monotone submodular set function `f : 2^V → ℝ[+]` which assigns a utility score to each subset:

![](graphic/b_9783110785968-007_ingr_024.png)

For the empty set, we assume zero utility `f(∅) = 0`. We denote the maximum of `f` with `OPT = f(S*)`. A set function can be associated with a marginal gain which represents the increase of `f(S)` when adding an element `x ∈ V` to `S`:

![](graphic/b_9783110785968-007_ingr_025.png)

We call `f` submodular iff for all `A ⊆ B ⊆ V` it holds that:

(7.10) `Δ[f](x | A) ≥ Δ[f](x | B)`

The function `f` is called monotone, iff for all `x ∈ V` and for all `S ⊆ V` it holds that `Δ[f](x|S) ≥ 0`. In general, the maximization of a submodular set function is NP-hard [[160]](#9783110785951_034588.xhtml#b_9783110785968-011_ref_160), which makes solving Equation 7.8 difficult. Therefore, a natural approach is to find an approximate solution. Nemhauser et al. presented in [[164]](#9783110785951_034588.xhtml#b_9783110785968-011_ref_164) a simple `(1 − (1/exp(1))) ≈ 63%` greedy approximation algorithm called Greedy for solving Equation 7.8, which runs in linear time and requires a fixed memory budget. Greedy offers a constant approximation guarantee and only requires `𝒪(K)` memory. As the name suggests, it works in a greedy fashion. Starting from an empty summary, it computes the marginal gain `Δ[f](x|S)` of each element in the ground set and picks the one with the largest gain. This process is repeated `K` times until the summary is full. The algorithm is depicted in Algorithm 7.1.

**Algorithm 7.1:** Greedy algorithm.

```
1 S ← ∅
2 for 1, ..., K do
3     x = arg max{Δ[f](x|S) | x ∈ V}
4     S ← S ∪ {x}
5 end
6 return S
```
