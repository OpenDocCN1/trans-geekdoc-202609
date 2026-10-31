**Step 12:** Calculate the standardized combined q-ROF assessment judgment matrix ($	ilde{S}$) by using Eq. (5.31).

$\tilde{S} = (\tilde{s}_{ij})_{m\times n} = [\tilde{U}_{ij}, \tilde{v}_{ij}] = \begin{cases} (\tilde{u}_{ij}, \tilde{v}_{ij}) & \text{if } i \in B \\ (\tilde{v}_{ij}, \tilde{u}_{ij}) & \text{if } i \in \check{C} \end{cases}$ (5.31)

where B indicates the group of advantage dimensions, and Ç denotes the group of cost dimensions.

**Step 13:** Compute the overall weighted comparability compromises ($\alpha$) for all cloud service providers by utilizing the Wq-ROFHA factor as exhibited in Eq. (5.24) and Eq. (5.25).

**Step 14:** Compute the complete power weight ($\beta$) of comparability compromises for all cloud service providers by utilizing the Wq-ROFHGM factor as exhibited in Eqs. (5.26) and (5.27).

**Step 15:** Compute the score values for all cloud service providers (alternatives) by utilizing the values of Wq-ROFHA and Wq-ROFHGM factors for each alternative by utilizing Eq. (5.20).

**Step 16:** Compute the proportionate weight of the cloud service providers (alternatives) with the help of Eqs. (5.32), (5.33), and (5.34).

$\gamma_{ja} = \frac{\alpha_j + \beta_j}{\sum_{j=1}^{n} (\alpha_j + \beta_j)}$ (5.32)

$\gamma_{jb} = \frac{\alpha_j}{\min(\alpha_j)} + \frac{\beta_j}{\min(\beta_j)}$ (5.33)

$\gamma_{jc} = \frac{\varphi\alpha_j + (1-\varphi)\beta_j}{\varphi\max(\alpha_j) + (1-\varphi)\max(\beta_j)}, \; 0 \le \varphi \le 1,$ (5.34)

where $\gamma_{ja}$ indicates the WSM and WPM scores. Then, $\gamma_{jb}$ refers to the total comparative scores of WSM and WPM. Also, $\gamma_{jc}$ indicates the established decisions of WSM and WPM scores.

**Step 17:** Compute the assessment values ($\gamma_j$) of all cloud service providers (alternatives) by utilizing Eq. (5.35). Then, rate the selected alternatives according to the most potential score of the assessment values ($\gamma_j$).

$\gamma_j = \sqrt[3]{\gamma_{ja}\gamma_{jb}\gamma_{jc}} + \frac{\gamma_{ja} + \gamma_{jb} + \gamma_{jc}}{3}$ (5.35)