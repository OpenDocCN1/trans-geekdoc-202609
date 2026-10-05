# F. Muhammad et al.: Decoupled-DL-UL Coverage Analysis with Interference Management

# IEEE Access

$E_{R_{R}^{(i)}}(s) = \exp\left(-s\sum_{y\in\Theta_{R}^{(i)}} P_{rx,y}^{(i)} P_{dl,y}^{(i)}\right) \text{for DL,

$M_{R_{v,coup}}^{(i)}}(s) = E_{R_{R}^{(i)}}(s) = \exp\left(-s\sum_{y\in\Theta_{R}^{(i)}} P_{rx,y}^{(i)} P_{dl,y}^{(i)}\right) \text{for UL.

$M_{R_{v,coup}}^{(i)}}(s) = E_{R_{R}^{(i)}}(s) = \exp\left(-s\sum_{y\in\Theta_{R}^{(i)}} M_{rx,y}^{(i)} M_{dl,y}^{(i)}\right) \text{for DL,

$M_{R_{v,coup}}^{(i)}}(s) = E_{R_{R}^{(i)}}(s) = \exp\left(-s\sum_{y\in\Theta_{R}^{(i)}} M_{rx,y}^{(i)} M_{dl,y}^{(i)}\right) \text{for UL.

$M_{R_{v,coup}}^{(i)}}(s) = \exp\left(-2\pi\lambda_{y_d} \int_{0}^{d_1} \frac{dx_l}{1+(S_{T_{tx,y_d})^{-1}x_l^2}}\right) \exp\left(-2\pi\lambda_{y_r} \int_{0}^{d_2} \frac{dx_l}{1+(S_{T_{tx,y_r})^{-1}x_l^2}\right) \text{for DL,

$M_{R_{v,coup}}^{(i)}}(s) = \exp\left(-2\pi\lambda_{y_d} \int_{0}^{d_1} \frac{dx_l}{1+(S_{T_{tx,y_d})^{-1}x_l^2}}\right) \exp\left(-2\pi\lambda_{y_r} \int_{0}^{d_2} \frac{dx_l}{1+(S_{T_{tx,y_r})^{-1}x_l^2}}\right) \text{for UL.

$P(Z_{R_{DL}^{(in)}}(y_v) > \tau_{BU} | T_{UE}^{(i)}) = \exp\left(-\frac{\beta_{v_u}}{\text{SNR}}\right) \exp\left(-\sum_{y\in\Theta_{R}^{(i)}} \lambda_{y} [L_{R,y}^{(i)} V_{R,y}^{(i)}]ight),

$P(Z_{R_{DL}^{(in)}}(y_v) > \tau_{BU} | T_{UE}^{(i)}) = \exp\left(-\frac{\beta_{v_u}}{\text{SNR}}\right) \exp\left(-\sum_{y\in\Theta_{R}^{(i)}} \lambda_{y} [L_{R,y}^{(i)} V_{R,y}^{(i)}]ight) \text{for UL.

Interference convergence $y_v, y_u$, which can be written there as (27), as shown at the top of this page, where $P_{R_{DL}}^{(i)}$, $P_{T_{UE}}^{(i)}\|x_i\|$ and $x_j$ and $P_{R_{UL}}^{(i)}$, $P_{T_{BS}}^{(i)}\|x_i\|$ and $x_j$ are the DL power received from UE in $R^{(i)}$ and UL power received from rBS in $R_{U}^{(i)}$, respectively. $P_{R_{DL}}^{(i)} = L_{R,y}^{(i)} V_{R,y}^{(i)}$ and $P_{R_{UL}}^{(i)} = L_{R,y}^{(i)} V_{R,y}^{(i)}$

Substituting ($y_v, y_u$), $a = (S_{T_{tx,y_u})^{-1}x_u^2$, $b = (S_{T_{tx,y_v})^{-1}y_v^2$, and $d = (S_{T_{tx,y_u})^{-1}x_u^2$, it is further simplified as:

\exp\left(-2\pi\lambda_{y_v} \int_{0}^{a} \frac{dx_l}{1+(S_{T_{tx,y_v})^{-1}x_l^2}}\right) \exp\left(-2\pi\lambda_{y_r} \int_{0}^{d} \frac{dx_l}{1+(S_{T_{tx,y_r})^{-1}x_l^2}}\right)

Assuming independence of channels in PDPL and DL channels, i.e., $(\mathcal{H}_{R}^{(i)}, \mathcal{H}_{U}^{(i)})$ and $\mathcal{H}_{R}^{(i)}$ are independent, (27) is further simplified in Step 5 as (28), as shown at the top of this page, where $\mathcal{M}_{R}^{(i)}}(\mathcal{O})$ and $\mathcal{M}_{U}^{(i)}}(\mathcal{O})$ are the MGFs of the interfering channels in $R^{(i)}$ and $U^{(i)}$, respectively.

where

$V_{R,y}^{(i)} = \int_{0}^{d_1} \frac{dx_l}{1+(S_{T_{tx,y})^{-1}x_l^2}} da = \frac{1}{2}\arctan(d_1\sqrt{S_{T_{tx,y}})$,

Assuming Rayleigh distribution for fading channels, (28) is further expressed as (29), as shown at the top of this page, here $y_v$ and $y_u$ represent the near-far distances:

$V_{U,y}^{(i)} = \int_{0}^{d_2} \frac{dx_l}{1+(S_{T_{tx,y})^{-1}x_l^2}} = \frac{1}{2}\arctan(d_2\sqrt{S_{T_{tx,y}}})$,

$P_{R_{DL}}^{(i)} > P_{R_{UL}}^{(i)} \iff P_{T_{UE}}^{(i)}}(S_{T_{tx,y_u})^{-1}y_v^2 > P_{T_{BS}}^{(i)}}(S_{T_{tx,y_v})^{-1}y_u^2$

$y_v > y_u$

$V_{R,y}^{(i)} = \int_{0}^{d_1} \frac{dx_l}{1+(S_{T_{tx,y})^{-1}x_l^2}} dy_n = \frac{1}{2}\arctan(d_1\sqrt{S_{T_{tx,y}}})$,

where ($T_{	au} \geq 1$), $y \in \{M, S\}$, $	au \in \{M, S\}$, and $y \neq \tau$.

and

$V_{U,y}^{(i)} = \int_{0}^{d_2} \frac{dx_l}{1+(S_{T_{tx,y})^{-1}x_l^2}} = \frac{1}{2}\arctan(d_2\sqrt{S_{T_{tx,y}}}) df.

Substituting (32) into (26), probability is expressed as (33), as shown at the top of this page. By substituting (33) into (25) completes the proof of (22).

VOLUME 4, 2016

6259