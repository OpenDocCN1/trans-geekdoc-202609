Where

+   - Z is the objective function (summation of unwanted deviations);
+   - $h_l^+$ represents the positive deviational variable and is the amount above the desired $l^{th}$ goal;
+   - $h_l^-$ indicates the negative deviational variable and is the amount below the desired $l^{th}$ goal;
+   - $p_l$ represents the goals for $l = 1, 2, 3, 4, ..., m$;
+   - $y_i$ designates the decision variables;
+   - $E_{li}$ denotes the decision variable coefficients.

It should be noted that one or even both variables must be zero; that is,

$h_l^+ * h_l^- = 0$

Both of these variables also meet the non-negativity requirement; that is,

$h_l^+ * h_l^- \ge 0$

# 4.3.1 Weighted Goal Programming (WGP) or Archimedean Goal Programming

The objective function (Z) in the weighted goal programming approach is actually the weighted sum of the deviations for the related problem's desired targets, with weights assigned based on the decision-maker's choice. In terms of representation, the weighted goal programming strategy takes the following form (Charnes & Cooper, 1977; Ignizio, 1976; Romero, 2004):

Minimize:

$Z = \sum_{l=1}^{m} (f_l^+ h_l^+ + f_l^- h_l^-)$

Subject to:

Goal constraints:

$\sum_{i=1}^{n} E_{li} y_i + h_l^- - h_l^+ = p_l$ for $l = 1, 2, 3, ..., m$

Hard constraints:

$\sum_{i=1}^{n} E_{li} y_i \begin{pmatrix} \ge \\ = \\ \le \end{pmatrix} p_l$ for $l = m+1, ..., m+g$