![](bbox=[0.11, 0.08, 0.88, 0.31])

FIGURE 18.1 SHS architecture.

# 18.2.1 Formal Modeling of SHS

We perform formal abstraction of the ML models of an SHS for analyzing its security. Formally modeling the PSCM and ADM requires acquiring constraints from them, which are fed into a first-order logic solver for threat analysis. Let P be the set of a patient’s sensor measurements with the patient status/label, j. We aim to detect and analyze critical attack samples that can bypass both PSCM- and ADM-driven constraints. The entire write-up will follow the notations described in Table 18.1.

# TABLE 18.1 Modeling Notations

| MODEL TYPE | ML MODEL | SYMBOL | DESCRIPTION | TYPE |
|---|---|---|---|---|
| All | All |  | Total sensor count | Integer |
| All | All |  | Total considered patient status | Integer |
| All | All |  | Pair of sensor measurement | String |
| All | All |  | A particular patient status | String |
| All | All |  | Set of all sensor measurements | Set |
| All | All |  | Set of all patient status | Set |
| PSCM | DT |  | Set of nodes in the path | Set |
| PSCM | DT |  | Set of all nodes | Set |
| PSCM | DT |  | Set of all paths starting from root to all leaves | Set |
| PSCM | DT |  | Model parameter (weight) associated with g-th patient status and i-th sensor measurement | Real |
| PSCM | DT |  | Set of all model parameter (weight) associated with g-th patient status | Set |
| PSCM | DT |  | Set of all model parameters (weight) |  |
| PSCM | DT |  | Model parameter (bias) for g-th patient status | Set |
| PSCM | DT | intercept | Set of all model parameter (bias) | Real |