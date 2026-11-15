# 10.4.3 Design Constraints

Design constraints are divided into some groups including the behavior, geometric and stability constraints. The behavior constraints are limits on natural frequencies that may be defined as follows:

\( fr_k^l \le fr_k \le fr_k^u \Rightarrow \left\{ \begin{array}{l} g_{bk}^l(X) = 1 - \frac{fr}{fr_k^l} \le 0 \\ g_{bk}^u(X) = \frac{fr}{fr_k^u} - 1 \le 0 \end{array} \right., k = 1, 2, \dots, n_{fr} \quad (10.10)\)

where \( fr_k, fr_k^l \) and \( fr_k^u \) are the \( kth \) natural frequency, lower and upper bounds on \( kth \) natural frequency, respectively. Also, \( n_{fr} \) is the number of natural frequencies that may be considered. The most important geometric constrains are those that prevent from intersection of upstream and downstream face as:

\( r_{di} \le r_{ui} \Rightarrow g_{gi}(X) = \frac{r_{di}}{r_{ui}} - 1 \le 0, i = 1, \dots, n + 1 \quad (10.11)\)

where \( r_{di} \) and \( r_{ui} \) are radii of curvatures at the down and upstream faces of the dam in \( i \)th position in \( z \) direction. The geometric constraint that is applied for facile construction is defined as:

\( s \le s_{all} \Rightarrow g_c(X) = \frac{s}{s_{all}} - 1 \le 0 \quad (10.12)\)

where \( s \) is the slope of overhang at the upstream face of dam and \( s_{all} \) is its allowable value. Also \( s_{all} \) is taken as 0.3 [2].

The constraints ensuring the sliding stability of the dam may be expressed as:

\( \varphi^l \le \varphi_i \le \varphi^u \Rightarrow \left\{ \begin{array}{l} g_{si}^u(X) = \frac{\varphi_i}{\varphi^u} - 1 \le 0 \\ g_{si}^l(X) = 1 - \frac{\varphi_i}{\varphi^l} \le 0 \end{array} \right., i = 1, \dots, n + 1 \quad (10.13)\)

where \( \varphi_i \) is the central angle of arch dam and usually \( 90 \le \varphi_i \le 130 \) [18].

# 10.4.4 Objective Function

In the present work, the cost of arch dam body is considered as objective function that may be expressed as:

\( w(X) = p_v v(X) + p_a a(X) \quad (10.14)\)