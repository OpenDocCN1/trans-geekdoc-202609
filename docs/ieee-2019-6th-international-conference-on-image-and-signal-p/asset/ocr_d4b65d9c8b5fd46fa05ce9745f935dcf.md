Distance between serving SBS $V_Y$, at TUE, and TUE $R^{(out)}$ is given as

```
$f_{Y,TUE|R^{(out)}}(V_y) = \frac{2\lambda_Y e^{-\lambda_Y y}}{(1-e^{-\lambda_Y y})^2}$
```

The above conditional distributions are useful in characterizing association probabilities of a randomly located TUE in $R^{(in)}$ and of our proposed model.

# A. ASSOCIATION PROBABILITY OF A TUE WITH COUPLED/DECOUPLED-DOWNUPLINK ANALYSIS

# 1) ASSOCIATION PROBABILITY OF A TUE WITH CO-DU

The association probability via which a TUE associates with $V_S, U_{V}^{uncou}$, both in UL and DL direction can be calculated

```
$U_{V}^{uncou} = P_{V_S}(||V_Y|| - ||V_S||) > P_{V_Y}(||V_S|| - ||V_Y||)$
```

where $P_{V_S}(||V_Y|| - ||V_S||)$ and $P_{V_Y}(||V_S|| - ||V_Y||)$ are, and $V_Y \in \{M\}, \tau \in \{M\}$ and $	au \neq R$ are the DL and DL association events, respectively.

There are two cases to simplify:

CASE-I: If a TUE associates with MBS, i.e., if $v \in \{M\}, \tau \in \{S\}$ holds $P_{V_S}^{M} > P_{V_Y}^{M}$. The probability of the events in (10) is $||V_Y||_{-AM} > ||V_S||_{-AM}$, because $P_{M}^{uncou} < 1$. The association probability, is written as

```
$U_{M,M}^{uncou} = \frac{\lambda_M e^{-\lambda_M Z}}{\sum_{\Omega=M} \lambda_\Omega e^{-\lambda_\Omega Z}}$
```

Proof:

```
$U_{M,M}^{uncou} = P(||V_Y||_{-AM} > ||V_S||_{-AM}) \n= E_{V_Y}(P(V_S > V_Y|V_Y)) \n= \int_{0}^{\infty} P(V_S > y|V_Y=y) f_{V_Y}(y) f_{V_S}(y)$
```

Assuming $\alpha_v = \alpha_\alpha$ and substituting into (10) over, along with mathematical manipulations completes the proof of (11).

CASE-II: If TUE associates with SBSs of two types, i.e., biased and unbiased association.

Unbiased association: If a TUE associates with uncoupled-SBS, i.e., $v \in \{S\}, \tau \in \{M\}$ holds $P_{V_S}^{M} > P_{V_Y}^{M}$, as a consequence of the evented events in (10) is $||V_Y||_{-AM} > ||V_S||_{-AM}$, because, $P_{M}^{uncou} > 1$.

Therefore, the association probability, is written as

```
$U_{B,M}^{uncou} = \frac{\lambda_S e^{-\lambda_S Z}}{\sum_{\Omega=S,M} \lambda_\Omega e^{-\lambda_\Omega Z}} > 1.$
```

Where $P_S^M$ is the ratio of the interfering MBS to the SBS transmit power.

Biased association: If a TUE associates with biased-SBS, i.e., $v \in \{S\}$ and $	au \in \{M\}$ holds $P_{V_S}^{M} > P_{V_Y}^{M}$, as the consequence of the events in (10) is $P_{T_S}||V_S|| > P_{T_M}||V_M|| > P_{T_Y}||V_Y||$. Assuming identical path losses equal, $\alpha_{AM} = \alpha$, the association probability is

```
$U_{B-S}^{uncou} = \frac{\lambda_S e^{-\lambda_S Z (T_{\Omega} P_\Omega^M)}}{\sum_{\Omega=S,M} \lambda_\Omega e^{-\lambda_\Omega Z (T_\Omega P_\Omega^M)}}$
```

Eq.(14) indicates that increasing small-cell bias factor, $T_{UE}$, the average number of offloaded SBSs increases as $T_{B-S}$ increases.

# 2) ASSOCIATION PROBABILITY OF DE-DUA

In De-DU a TUE can associate with two different SBSs in BS and DL direction. Let us assume that the TUE associates with BS in DL direction and RBS in UL direction. The association probability can be

```
$U_{decup} = P_{T_S}(||V_Y||_{-AM} > ||V_S||_{-AM}) > P_{T_M}(||V_Y||_{-AM} > ||V_M||_{-AM}) \n||V_S||_{-AM} > ||V_Y||_{-AM})$
```

Here, $v \in \{S\}, \tau \in \{M\}$ and $v \neq 	au$. There are two ways to simplify (15).

a) If the TUE associates with MBS in DL direction, if $v \in \{M\}$ and SBS in UL direction, i.e., $	au \in \{S\}$,

```
$U_{decup,S.M} = \frac{\lambda_S e^{-\lambda_S Z}}{\sum_{\Omega=S,M} \lambda_\Omega e^{-\lambda_\Omega Z}}$
```

b) If the TUE associates with SBS in DL direction, if $v \in \{S\}$ and MBS in UL direction, i.e., $	au \in \{M\}$,

Since the above events can also intersect, the association probability is written as $||V_Y||_{-AM} > ||V_S||_{-AM}$. Using the above event the association probability $U_{decup}^{uncou}$ is given as

```
$U_{decup,S.M} = \frac{\lambda_M e^{-\lambda_M Z}}{\sum_{\Omega=S,M} \lambda_\Omega e^{-\lambda_\Omega Z}}$
```

Since the above events do not intersect, the association probability of the above case is 0, i.e., $U_{decup,S.M} = 0$.