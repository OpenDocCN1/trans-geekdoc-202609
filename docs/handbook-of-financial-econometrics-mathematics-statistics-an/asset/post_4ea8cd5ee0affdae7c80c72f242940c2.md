
Note that even though this MC²DM transfer pricing model includes only four specific groups of objectives for presentation purposes, the modeling process easily adapts to all international transfer pricing problems with multiple criteria and multiple constraint levels such as maximization of after-tax profit for the parent company as another criterion or minimization of foreign taxes and tariffs as additional constraints.

The above models (54.1) and (54.2) are MC² problems with four objectives and four constraint levels. Solving this type of real-world problem is quite complicated. Therefore, this chapter proposes a fuzzy set approach to make the computational task as practical as possible.

## 54.4 A Fuzzy Solution Method

Based on a compromise solution approach for multiple objective decision-making problems, Shi and Liu (1993) propose fuzzy MC² linear programming. Their fuzzy approach adopts the compromise solution or the “satisficing solution” between upper and lower bounds of acceptability for objective payoffs. The following section presents the fuzzy set approach for an international transfer pricing problem:

**Step 1:** Given the models (54.1) and (54.2), we may use any available computer software to solve the following series of LP programs. For illustration purposes, let’s assume \(t = 5\), \(i = 5\), and \(u = 5\):

(i) Max (and Min) \(\sum_{j=1}^{5} P_j X_j\) (54.3)

subject to:

\[
\sum_{j=1}^{5} b_{ij}x_j \le (c_{1i},\dots,c_{5i})(\gamma_1,\dots,\gamma_5)^T \tag{54.4}
\]

\[
\sum_{p=1}^{5}\gamma_p = 1, \quad \gamma_p > 0, \quad p=1,\dots,5,
\]

\[
x_j \ge 0, \quad j=1,\dots,5.
\]

(ii) Max (and Min) \(\sum_{j=1}^{5} m_{ij}x_j,\ i=1,\dots,5\) (54.5)

subject to: (54.4)

(iii) Max (and Min) \(\sum_{j=1}^{5} s_{ij}x_j,\ i=1,\dots,5\) (54.6)

subject to: (54.4)

(iv) Max (and Min) \(\sum_{j=1}^{5} c_{ij}x_{ij},\ i=1,\dots,5\) (54.7)

subject to: (54.4).

Group (i) of the above LP problems has two types of optimization: one is maximization and the other is minimization. Groups (ii), (iii) and (iv) have six problems, respectively. All of them use the same constraints (54.4). The total number of problems is eight. We define the objective value of the maximization problems by \(\mathbf{U}_i\) as the upper bound of DMs’ acceptability for the objective payoff; and the objective value of the minimization problems by \(\mathbf{L}_i\) as the lower bound of DMs’ acceptability for the objective payoff, \(i = 1,\dots,12\).

**Step 2:** Let \(f(x)_i\), \(i=1,\dots,12\), be the objective functions in Step 1. Then, we solve the following linear program:

Max \(\beta\) (54.8)

subject to:

\[
\beta \le \frac{f(x)_i - L_i}{U_i - L_i}, \quad i=1,\dots,12, \tag{54.9}
\]

\[
\beta \ge 0,
\]

\[
\sum_{j=1}^{5} b_{ij}x_j \le (c_{1i},\dots,c_{5i})(\gamma_1,\dots,\gamma_5)^T
\]

\[
x_j \ge 0, \quad j=1,\dots,5.
\]

The resulting values of \(x_j\) are the fuzzy optimal solution and the value of \(\beta\) is the satisficing level of the solution for the DMs.

The above fuzzy solution method has systematically reduced the complexity of the MC²DM capital budgeting model (54.1) and (54.2) because it transforms the MC² LP problem into an LP problem. The above two solution steps can be easily implemented by employing available commercial computer software. In the following section, a prototype of the transfer pricing model in a multinational corporation will be illustrated to demonstrate the implications for decision makers.

## 54.5 Model Implications

### 54.5.1 Numerical example

As an illustration of the multiple factor transfer pricing model, the Union Plastic Corporation has two divisions that process raw materials into intermediate or final products. Division 1, which is located in Taipei, Taiwan, manufactures two kinds of plastics, called Products 1 and 2. Product 1 in Division 1 is an intermediate product and cannot be sold externally. It can, however, be processed further by Division 2 into a final product. Division 2, which is located in Omaha, Nebraska, USA, processes Product 2 and finalizes Product 1 from Division 1. Central management and two divisional managers agree on the following multiple objectives:

- (i) Maximize the overall company’s after-tax profit.
- (ii) Maximize the market share goal of Product 2 in Division 1, and Products 1 and 2 in Division 2.
- (iii) Maximize the utilized production capacity of the company so that each division manager can avoid any underutilization of normal production capacity.

The data related to these objectives is given in Table 54.1.

**Table 54.1: United Chemical Corporation.**

|  | Division 1 |  | Division 2 |  |
|---|---|---|---|---|
|  | Product 1 | Product 2 | Product 1 | Product 2 |
| Unit profit ($) | −4 | 8 | 13 | 5 |
| Market price | 0 | 40 | 46.2 | 38 |
| Production capacity (hours) | 4 | 4 | 3 | 2 |

In Table 54.1, Product 1 of Division 1 is a byproduct which has no sale value in Division 1 at all. The unit profit −$4 of this product means its production cost. All other products generate profits. We use the market price of each product to maximize the market share goal. Note that the market prices of three products in Table 54.1 are different.

In this example, besides central management, the selling divisional manager and the purchasing divisional manager may have different interpretations of the same resource availability across the divisions. The selling divisional manager views the constraint level based on the material, manpower, and equipment under control, while the purchasing divisional manager views the constraint level based on the available cash flow. Central management will make the final decision for the company’s transfer price setting on the basis of the compromises of both managers. All divisional managers will carry out central management’s decision, although they have their autonomy to provide the information about the divisional profits and costs for central management. The interpretations of both managers for the resource constraint levels are summarized in Table 54.2.

All executives and divisional managers agree on the units of resources consumed to produce the products. The data is given in Table 54.3.

Let \(x_{ij}\) be the units of the \(j\)th product produced by the \(i\)th division, \(i = 1, 2; j = 1, 2\). Then:

**Table 54.2: The constraint levels of the vice presidents.**

|  | The selling divisional manager | The purchasing divisional manager |
|---|---:|---:|
| Transfer Product Constraint: | 0 | 100 |
| Budget Constraint ($): | 45,000 | 40,000 |
| Production Capacity of Product 2 in Division 1: | 38,000 | 12,000 |
| Production Capacity of Product 1 in Division 2: | 45,000 | 50,000 |
| Production Capacity of Product 2 in Division 2: | 36,000 | 10,000 |

**Table 54.3: The unit consumptions of resources.**

|  | Division 1 |  | Division 2 |  |
|---|---:|---:|---:|---:|
|  | Product 1 | Product 2 | Product 1 | Product 2 |
| Transfer Product Constraint: | −1.0 | 0 | 1.0 | 0 |
| Budget Constraint ($): | 0 | 0.4 | 0.4 | 0.4 |
| Production Capacity of Product 2 in Division 1: |  | 1.0 |  |  |
| Production Capacity of Product 1 in Division 2: |  |  | 1.0 |  |
| Production Capacity of Product 2 in Division 2: |  |  |  | 1.0 |

**Step 1:**

We use the LINDO (Schrage, 1991) computer software to solve three maximization problems and three minimization problems for three objectives, respectively. The results are:

\(U_1 = 856{,}900\), \(U_2 = 4{,}720{,}000\), \(U_3 = 546{,}000\); and \(L_1 = −20{,}000\), \(L_2 = 0\), \(L_3 = 0\). To see more concentrated value on \(\gamma_1\) and \(\gamma_2\), we add \(\gamma_1 \ge 0.3\) and \(\gamma_2 \ge 0.3\) on each problem. Then, the results are: \(U_1^* = 801{,}380\), \(U_2^* = 4{,}427{,}900\), \(U_3^* = 516{,}700\); \(L_1^* = −20{,}000\), \(L_2^* = 0\), \(L_3^* = 0\). The LINDO software yields slack and dual prices, which are an opportunity cost or marginal cost of transfer prices. When \(\gamma_1 + \gamma_2 = 1\), the objective function value of this example is $856,900 for the first objective maximization. Slacks for \(\gamma_1 = 6{,}500\) and transfer prices of \(\{x_{11}, x_{12}, x_{21}, x_{22}\}\) are $4.00, $12.50, $3.00, and $4.00, respectively. When \(\gamma_1 \ge 0.3\) and \(\gamma_2 \ge 0.3\), the objective function value is $801,380. Slacks for \(x_{12} = 1{,}540\), and transfer prices of \(x_{11} = \$4.00\), \(x_{21} = \$8.00\), and \(x_{22} = \$9.00\) will be produced to achieve the objective payoff \(V(J_1)\) and the resource of \(x_{22}\) has the amount of \(s_5\) unused. Generally, if we let \(p_q(J_i)\), \(q = 1, \dots, 5\); \(i = 1, 2\), be the shadow price of \(J_i\) for the \(q\)th constraint. According to the marginal cost pricing approach, the optimal transfer prices of \(\{J_1, J_2\}\) are designated as the shadow prices of \(\{J_1, J_2\}\).

**Step 2:**

Let \(\beta\) be the satisficing level of the fuzzy optimal solution for the DMs. Then, we have the fuzzy solution problem as shown in the Appendix. Solving this problem, we obtain: \(\beta = 0.987\), \(x_{11} = 48{,}262.7\), \(x_{12} = 38{,}000\), \(x_{21} = 45{,}000\), and \(x_{22} = 29{,}500\) units and \(\gamma_1 = 1\) and \(\gamma_2 = 0\). If we impose the preference parameters of the decision makers \(\gamma_i \ge 0.3\), then the solution will be \(\beta = 0.991\), \(x_{11} = 48{,}784\), \(x_{12} = 30{,}200\), \(x_{21} = 46{,}500\), and \(x_{22} = 28{,}200\) units and \(\gamma_1 = 0.7\) and \(\gamma_2 = 0.3\). Here \(\gamma_1 =\) the preference of the selling divisional manager and \(\gamma_2 =\) the preference of the purchasing divisional manager. However, the current fuzzy solution does not provide shadow prices. For the current solution with both managers’ preferences, we only find fuzzy optimum units for each product. For example, if we transfer \(x_{11}\) at $4.00, \(x_{12}\) at $12.50, \(x_{21}\) at $3.00, and \(x_{22}\) at $4.00, the objective function value will be $791,964, which is less than the optimum value for the achievement of the goal of maximization of profits, but we can satisfy both managers according to their other preferences. With the above shadow prices (or transfer prices), the constraints in Step 2 are satisfied. However, other shadow prices in Step 1 do not satisfy the constraints in Step 2.

### 54.5.2 Managerial implications

The fuzzy set approach for the transfer pricing problems as we discussed in this chapter has some managerial implications. First, the model integrates
