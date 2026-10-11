
## Phases 2, 3, and 4: The Offline Part

Phase 3, in particular, performs batch clustering based on the information collected in the CF tree. Phase 1 is the online process, and the one that actually works on the stream. For every arriving point, the algorithm descends the tree, updating the statistics at the CFs of the inner nodes traversed, to reach a leaf closest to the point. Then it checks whether the leaf can absorb it within radius `R`. If so, the point is “assigned” to the leaf by updating the leaf statistics. If not, a new leaf is created for the new point. This new leaf may cause the parent node to have more than `B` children; if so, it has to be split into two, and so recursively up to the root. A further rule, not described here, is applied to merge leaves and nodes that may have become too close in the process.

## BICO

**BICO** (an acronym for “BIRCH meets coresets for `k`-means clustering”) is due to Fichtenberger et al. [101]. It combines the data structure of BIRCH with the theoretical concept of coresets for clustering. Coresets are explained in detail in section 9.6. BIRCH decides heuristically how to group the points into subclusters. The goal of BICO is to find a reduced set that is not only small, but also offers guarantees of approximating the original point set.

## CLUSTREAM

**CLUSTREAM**, by Aggarwal et al. [6], is designed as an adaptive extension of BIRCH that can deal with changing streams. In CLUSTREAM, nodes of the CF tree maintain CF vectors of the form `(N, LS, SS, LT, ST)`, which extend BIRCH CFs with two additional temporal features:

*   `LT`: sum of the timestamps
*   `ST`: sum of squares of the timestamps

The offline phase of CLUSTREAM simply applies `k`-means periodically to the microclusters at the leaves of the CF tree. The online phase is similar to that of BIRCH, but it takes the recency of clusters into account. It keeps a maximum number of microclusters in memory. If a point requires creating a new microcluster (leaf) and there is no more space available, the algorithm either deletes the oldest microcluster or else merges two of the oldest microclusters. The notion of the “oldest” microcluster is defined taking into account whether there has been significant recent activity in the microcluster. More precisely, statistics `LT` and `ST` are used to compute average and standard deviation of its timestamps; assuming a normal distribution of the timestamps, the algorithm can use them to decide whether a desired fraction of the points in the microcluster are older than a desired recency threshold.

The fact that the oldest clusters, not the smallest ones, are chosen for deletion gives CLUSTREAM an interesting property: by looking at microclusters of similar timestamp distributions, we can obtain a snapshot of the clustering in a desired time frame, with more resolution for more recent time frames and less resolution as we move further back in time. This is sometimes called a *pyramidal* time frame.

# 9.4 Density-Based Methods: DBSCAN and Den-Stream

Density-based clusterers are based on the idea that clusters are formed not only by overall proximity in distance, but also by the density of connections. They may thus produce clusters that are not spherical, but rather have shapes that adapt to the specific data being clustered.

The **DBSCAN** algorithm [96], due to Ester et al., is the best-known density-based, offline algorithm. It is based on the idea that clusters should be built around points with a significant number of points in their neighborhoods. The following definitions formalize this idea:

*   The `ε`-neighborhood of `p` is the set of points at a distance `ε` or less from `p`.
*   A **core point** is one whose `ε`-neighborhood has an overall weight (fraction of dataset points) of at least `μ`.
*   A **density area** is the union of the `ε`-neighborhoods of core points.
*   A point `q` is **directly reachable** from `p` if `q` is in the `ε`-neighborhood of `p`. Point `q` is **reachable** from `p` if there is a sequence `p[1], …, p[n]` such that `p[1] = p`, `p[n] = q`, and each `p[i+1]` is directly reachable from `p[i]`.
*   A core point `p` forms a cluster with all the (core or non-core) points that are reachable from it.
*   All points that are not reachable from core points are considered **outliers**.

Note that a cluster is determined by any of the core points it contains, and that these definitions create a unique clustering for any dataset, for given values of `ε` and `μ`.

The DBSCAN algorithm has parameters `ε` and `μ` and uses these properties to find this unique clustering. It visits the points in the dataset in an arbitrary order. For a previously unvisited point `p`, it finds all the points that are directly `ε`-reachable from `p`. If `p` is found to be a `μ` core point, a new cluster is formed and all points reachable from `p` are added to the cluster and marked visited; otherwise, if `p` has weight below `μ`, it is temporarily marked as “outlier” and the method proceeds to the next unvisited point. An outlier may later be found to be reachable from a true core point, and declared “not outlier” and added to some cluster.

Observe that DBSCAN is strongly non-streaming, because each point may be repeatedly accessed.

**Den-Stream**, developed by Cao et al. [61], is a density-based streaming method based on ideas similar to DBSCAN, but using microclusters to compute online statistics quickly. It uses the damped window model, meaning that the weight of each data point decreases exponentially using a fading function `f(t) = 2^(-λt)` where `λ > 0`.

For a microcluster with center `c` and representing points `p[1], p[2], …, p[n]`, with timestamps `T[1], T[2], …, T[n]`, Den-Stream maintains the following information at time `t`:

*   **Weight**: ![](images/pg156-in-1.png)
*   **Center**: ![](images/pg156-in-2.png)
*   **Radius**: ![](images/pg156-in-3.png) (in fact, the sums of the squares of `p[i]` are kept, from which `r` can be computed when needed)

There are two types of microcluster: depending on whether the weight is larger or smaller than `μ`, the microcluster is called a **potential core microcluster (p-microcluster)** or an **outlier microcluster (o-microcluster)**. So an outlier microcluster is a microcluster that does not (yet) have enough weight to be considered a core.

The **DEN-STREAM** method has two phases, an online phase and an offline phase. Their pseudocode is shown in [figure 9.2](#chapter_9.xhtml#fig9-2). In the online phase, every time a new point arrives, DEN-STREAM first tries to merge it into one of the potential microclusters. If this is not possible, it then tries to merge the point with an outlier microcluster. If the weight of the outlier microcluster has increased enough to be a potential microcluster, the microcluster is promoted. Otherwise, DEN-STREAM starts a new outlier microcluster. The offline phase consists of removing the microclusters that have not reached a sufficient weight, and performing a batch DBSCAN clustering.

![Figure 9.2 The DEN-STREAM algorithm.](images/Fig9-2.png)

[**Figure 9.2**](#chapter_9.xhtml#rfig9-2)

The DEN-STREAM algorithm.

# 9.5 CLUSTREE

The streaming clustering algorithms presented up to now require an application of an offline phase in order to produce a cluster when requested. In contrast, **CLUSTREE** (Kranen et al. [150]) is an **anytime clustering** method, that is, it can deliver a clustering at any point in time. It is a parameter-free algorithm that automatically adapts to the speed of the stream and is capable of detecting concept drift, novelty, and outliers in the stream.

CLUSTREE uses a compact and self-adaptive index structure for maintaining stream summaries with a logarithmic insertion time. The structure is a balanced tree where each node contains a CF of a number of points, as in CLUSTREAM. This tree contains a hierarchy of microclusters at different levels of granularity. The balanced condition guarantees logarithmic access time for all microclusters.
