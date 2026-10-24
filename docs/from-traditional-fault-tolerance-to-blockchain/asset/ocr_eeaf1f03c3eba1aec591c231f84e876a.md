| G5 | Msgs Collected | Case 1: G0 and G6 are traitors | Case 2: G5 and G6 are traitors |
|---|---|---|---|
| G1-OM(1) | $M^{01}, M^{012}, M^{013}, M^{014}, M^{016}$ | $m(x, x, x, x, ?) = x$ | n/a |
| G2-OM(1) | $M^{02}, M^{021}, M^{023}, M^{024}, M^{026}$ | $m(x, x, x, x, ?) = x$ | n/a |
| G3-OM(1) | $M^{03}, M^{031}, M^{032}, M^{035}, M^{036}$ | $m(x, x, x, x, ?) = x$ | n/a |
| G4-OM(1) | $M^{04}, M^{041}, M^{042}, M^{043}, M^{046}$ | $m(y, y, y, y, ?) = y$ | n/a |
| G6-OM(1) | $M^{06}, M^{061}, M^{062}, M^{063}, M^{064}$ | $m(s5, s1, s2, s3, s4) = s$ | n/a |

Table 7.6 Messages received and step (3) calculation in two cases for instances of OM(1) at G5.

| Lieutenant | Case 1: G0 and G6 are traitors | Case 2: G5 and G6 are traitors |
|---|---|---|
| G1 | $m(x, x, x, y, y, s)$ | $m(v, v, v, v, ?, ?) = v$ |
| G2 | $m(x, x, x, y, y, s)$ | $m(v, v, v, v, ?, ?) = v$ |
| G3 | $m(x, x, x, y, y, s)$ | $m(v, v, v, v, ?, ?) = v$ |
| G4 | $m(x, x, x, y, y, s)$ | $m(v, v, v, v, ?, ?) = v$ |
| G5 | $m(x, x, x, y, y, s)$ | n/a |

Table 7.7 Final decision made at each lieutenant in step (3) of OM(2).

in case 2, the decision is clearly $v$, the same value sent by the loyal commander G0.

Recall that the $v$ variables for remote lieutenants have all been reset in step (3) of the $OM(1)$ instances at each lieutenant. In case 1, only the value for $v_6$ is changed to $s$ for all loyal lieutenants.

In case 2, the new values for the $v$ variables of loyal lieutenants remain the same because G0 is assumed loyal. The values for $v_5$ and $v_6$ may have changed. However, the values for $v_5$ and $v_6$ are not important in the final decision because the $v$ variables for the four loyal lieutenants (G1, G2, G3, and G4) have the same value $v$.