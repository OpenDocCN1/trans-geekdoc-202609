This implies that

4 ≤ 2dK ≤ 2d5<sup>d</sup> ≤<sup>2dA</sup>/<sub>2d</sub> = A.

Combining this and the fact that \textbf{L} ≥ 1 + ( [log<sub>2</sub>(A/(2d)) + 1] \textbf{1}<sup>(d,\infty)</sup>(A) = [log<sub>2</sub>(A/(2d)) + 2 therefore demonstrates that [log<sub>2</sub>(K)] ≤ [log<sub>2</sub>(A/(2d))] ≤ \textbf{L} - 2. This, (4.209), the assumption that \textbf{1}<sub>L</sub> ≥ A\textbf{1}<sup>(d,\infty)</sup>(A) = A, and the assumption that \forall i \in {2, 3, \ldots, \textbf{L}-1}: \textbf{1}<sub>i</sub> ≥ 3[<sup>A</sup>/(2<sup>d</sup>)] \textbf{1}<sup>(d,\infty)</sup>(A) = 3[<sup>A</sup>/(2<sup>d</sup>)] prove that for all i \in {2, 3, \ldots, \textbf{L}-1} it holds that

\textbf{L} ≥ [log<sub>2</sub>(K)] + 2, \textbf{1}<sub>L</sub> ≥ A ≥ 2dK, and \textbf{1}<sub>i</sub> ≥ 3[<sup>A</sup>/(2<sup>d</sup>)] ≥ 3[<sup>K</sup>/(2<sup>i-1</sup>)].

Let \textbf{f}<sub>1</sub>, \textbf{f}<sub>2</sub>, \ldots, \textbf{f}<sub>K</sub> \in [a, b]<sup>d</sup> satisfy

sup<sub>x \in [a,b]<sup>d</sup></sub> [inf<sub>k \in {1,2,\ldots,K}</sub> \delta(x, \textbf{f}<sub>k</sub>)] ≤ r.

Observe that (4.210), the assumptions that \textbf{1}<sub>0</sub> = d, \textbf{1}<sub>1</sub> = 1, \textbf{d} ≥ \sum<sub>i=1</sub><sup>L</sup> \textbf{1}<sub>i</sub>(\textbf{1}<sub>i-1</sub> + 1), and \forall x, y \in [a, b]<sup>d</sup>: |f(x) - f(y)| ≤ L||x - y||<sub>1</sub>, and Corollary 4.4.10 establish that there exists \vartheta \in \mathbb{R}<sup>d</sup> such that

||\vartheta||<sub>\infty</sub> ≤ max{1, L, max<sub>k \in {1,2,\ldots,K}</sub>||\textbf{f}<sub>k</sub>||<sub>\infty</sub>, 2 max<sub>k \in {1,2,\ldots,K}</sub> f(\textbf{f}<sub>k</sub>)}

and

sup<sub>x \in [a,b]<sup>d</sup></sub> |\mathcal{N}<sup>\vartheta,1</sup><sub>a,b</sub>(x) - f(x)| ≤ 2L[sup<sub>x \in [a,b]<sup>d</sup></sub>(inf<sub>k \in {1,2,\ldots,K}</sub>||x - \textbf{f}<sub>k</sub>||<sub>1</sub>)]
= 2L[sup<sub>x \in [a,b]<sup>d</sup></sub>(inf<sub>k \in {1,2,\ldots,K}</sub> \delta(x, \textbf{f}<sub>k</sub>))].

Note that (4.212) shows that

||\vartheta||<sub>\infty</sub> ≤ max{1, L, |a|, |b|, 2 sup<sub>x \in [a,b]<sup>d</sup></sub>|f(x)|},

Furthermore, observe that (4.213), (4.207), (4.211), and the fact that for all k \in \mathbb{N} it holds that 2k ≤ 2(2<sup>k</sup>-1) = 2<sup>k</sup> ensure that

sup<sub>x \in [a,b]<sup>d</sup></sub> |\mathcal{N}<sup>\vartheta,1</sup><sub>a,b</sub>(x) - f(x)| ≤ 2L[sup<sub>x \in [a,b]<sup>d</sup></sub>(inf<sub>k \in {1,2,\ldots,K}</sub> \delta(x, \textbf{f}<sub>k</sub>))]
≤ 2Lr = <sup>dL(b-a)</sup>/<sub>3</sub> ≤ <sup>dL(b-a)</sup>/<sub>(2/3)(<sup>A</sup>/(2<sup>d</sup>))<sup>1/d</sup></sub> = <sup>(2<sup>d</sup>)<sup>1/d</sup>3dL(b-a)</sup>/<sub>2A<sup>1/d</sup></sub> ≤ <sup>3dL(b-a)</sup>/<sub>A<sup>1/d</sup></sub>.

Combining this with (4.214) implies (4.206). The proof of Proposition 4.4.12 is thus complete.

Corollary 4.4.13. Let d \in \mathbb{N}, a \in \mathbb{R}, b \in (a, \infty), L \in (0, \infty) and let f: [a, b]<sup>d</sup> \rightarrow \mathbb{R} satisfy for all x, y \in [a, b]<sup>d</sup> that

|f(x) - f(y)| ≤ L||x - y||<sub>1</sub>