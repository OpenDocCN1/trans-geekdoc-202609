
# IEEE Access

Received August 28, 2016, accepted September 11, 2016, date of publication September 23, 2016, date of current version October 31, 2016.

Digital Object Identifier: 10.1109/ACCESS.2016.2623128

# Decoupled Downlink-Uplink Coverage Analysis with Interference Management for Enhanced Heterogeneous Cellular Networks

FAZAL MUHAMMAD¹, (Student Member, IEEE), ZIAEL HAQ ABBAS², GHULAM ABBAS², (Senior Member, IEEE), AND LEI JAO³, (Member, IEEE)

*Faculty of Engineering, Gushk Iqbal Khan Institute of Engineering Sciences and Technology, Top 236-60, Pakistan
²Faculty of Engineering, Gushk Iqbal Khan Institute of Engineering Sciences and Technology, Top 236-60, Pakistan
³Department of Information and Communication Technology, University of Agder, N-466 Grimstad, Norway
Corresponding author: F. Muhammad (fazal_engr@giki.edu)

**ABSTRACT** Heterogeneous networks (HetNCs) offer a promising solution to cope with the current cellular network crunch. Due to the large transport power disparity, while favoring maximum power (MPR) association scheme, a higher number of users are associated with macro-cell BS (MBS) than small-cell BS (SBS). Hence, an imbalance allocation takes places across the HetNCs. Using cell range expansion-based association, we can balance the load across the HetNCs. However, using MPR association scheme, users leads to two challenges: 1) macro-cell interference, in which the MBS interferes with the overloaded users, and 2) decoupled downlink-uplink association, where a random user associates with a single tier's base station (BS) in uplink (UL) and downlink (DL) directions. This paper addresses these problems while considering a two-tier scenario. We employ a reverse frequency allocation (RFA) scheme. Besides Coupled DL-UL association (Co-DU), this paper also highlights the notion of decoupled DL-UL association. In De-DU, a random user associates with two different tiers BS, with one tier's BS in DL and the other tier's BS in UL. Our results illustrate that, in comparison with the Co-DU, De-DU with RFA employment achieves a better coverage performance.

- **INDEX TERMS** Heterogeneous cellular networks, small-cell BS, reverse frequency allocation, downlink-uplink association, coverage performance.

# I. INTRODUCTION

To meet the current wireless data deluge, cellular networks enter into a new paradigm where the low power small-cells, i.e., pico-cells and femto-cells, utilize the existing infrastructure of high power macro-cells in heterogeneous cellular networks (HetNCs) [1]. Different types of BS differ from each other in their transmit power, BS densities, user densities associated and cell selection offsets. Due to the higher transmit power, coverage of macro-cells are larger compared with low power small-cells. Fewer number of users are associated with small-cells. Cell range expansion (CRE) [2], is one of the popular load balancing methods, where a cell selection offset (also referred as the association) is added to small-cells reference signals to increase their coverage range in order to push a fraction of users from macro-cells towards small-cells. Load balancing brings benefits to the HetNets, i.e., macro-congestion and overloaded users to small-cells to utilize their resources efficiently. However, these besides critical challenges faced by HetNCs, i.e., the macro-cells interference towards the overloaded users and downlink cell association.

6250
2168-1556/IEEE.2016.2623128 Transactions and content mining are permitted for academic purposes only. Personal use is permitted, but publication/redistribution permission requires IEEE permission.

VOLUME 4, 2016

sub frames (ABSs) ABSs are completely assigned to the offloaded users in the MCI Cloud, this scheme results in decrease of macro-resources, these ABSs are used by small cells. Frequency-based resource partitioning is presented in [5], where the MBS is on a fraction of sub-bands, which are allocated to offloaded users. In [6], the authors investigate to interference plus noise (SINR) based analysis for resource partitioning. However, i.e., loading is not considered in their working scheme of frames. In [7] extend the work presented in [6], and observe the effect of load balancing and resource-based partitioning on the performance metrics. However, the previous studies [4]–[7] consider UL association, in which a random user is associated with a single BS [8]. Furthermore, [10]–[12] specify that UL association is not considered in their models. In these models, the authors associate their user with one BS in DL link direction to connect to any other BS in UL direction. This is referred to as de-coupled. In [13] the authors consider DL and UL user association. The authors in [14] consider rate and performance rates considering different DL and UL association strategies. The studies in [15] and [16] illustrate their theoretical results by showing that de-coupling achieves better performance in terms of capacity. However, our proposed model aims to study the impact of decoupled-uplink-downlink (De-UA) with load balancing, while considering reverse frequency allocation (RFA) [17] to mitigate MCI and achieve better performance.

In this paper, we consider a two-tier scenario. We employ a reverse frequency allocation (RFA) scheme. Besides Coupled DL-UL association (Co-DU), this paper also highlights the notion of decoupled DL-UL association. In De-DU, a random user associates with two different tiers BS, with one tier's BS in DL and the other tier's BS in UL. Our results illustrate that, in comparison with the Co-DU, De-DU with RFA employment achieves a better coverage performance.

In this paper, we consider a two-tier scenario. We employ a reverse frequency allocation (RFA) scheme. Besides Coupled DL-UL association (Co-DU), this paper also highlights the notion of decoupled DL-UL association. In De-DU, a random user associates with two different tiers BS, with one tier's BS in DL and the other tier's BS in UL. Our results illustrate that, in comparison with the Co-DU, De-DU with RFA employment achieves a better coverage performance.

The main contributions of this paper can be summarized as:
- We consider a two-tier HetNet model with resource partitioning, i.e., two association modes: coupled (Co) and decoupled (De) association.
- We probabilistically characterize the performance of the proposed association with RFA.
- Our results show De-UA surpasses coverage performance over other methods, such as Co-UA and without RFA.

The rest of the paper is organized as follows. The system model is presented in Section II. Section III presents the SIR distribution and user association. Our association is described in Section IV. Section V presents the numerical results. The paper is concluded in VI.

# II. SYSTEM MODEL

### A. BASE STATION AND USER DISTRIBUTION

Consider a two-tier HetNet model, where each BS is deployed in terms of densities and transmit power. BSs of both tiers are deployed through independent PPP, $\Phi_i$, with densities $\lambda_i \in \{M, S\}$ and $M$ and SBS, respectively. As the HetNet is also distributed via another homogeneous PPP, $\Phi_u$; According to Slnyak's Theorem [20], the analysis remains unchanged if carried out typical location.

### B. CHANNEL MODEL AND USER ASSOCIATION

DL received power by UE from BS, and UL received power by BS from UE, $P_{R,u}^{DL} = T_{BS}h_u$, $P_{R,b}^{UL} = T_{UE}h_b$, respectively. Here, $T_{BS}$ and $T_{UE}$ represent the transmit power of BSs and the associated users, and $H_h$ is the channel of BS, and $H_v$ denote the fading of the UE. The channel between BS and UE is modeled with path loss represented by an exponential. Rayleigh fading with unit mean is used for all channels, e.g., the direct and interfering channels, $H_i \sim \exp(1)$, where $X$ is a random variable with probability density function $f_X(x) = e^{-x}$ for $x \ge 0$, and $H_i = H \sim \exp(1)$, since the fading is independent of the BS site.

### C. REVERSE FREQUENCY ALLOCATION SCHEME

In the co-coupled deployed multi-tier, transmissions in DL and UL direction of a tier co-occur with the transmissions of other tier, which causes MCI. The mitigation of such type of interference is one of the challenges in HetNets. Several approaches are presented in state-of-the-art (e.g., see [4] and references in [5]). However, in this paper, we present our work, we use the RFA scheme to abate MCI. De-UA to achieve maximum performance gain. To employ RFA, we split the available region $R$ into two subregions, $R^{(\alpha)}$ and an outer subregion, $R^{(1-\alpha)}=R$, where $R^{(\alpha)}$ is the subregion where the MBS provides reasonable coverage to its associated users.
