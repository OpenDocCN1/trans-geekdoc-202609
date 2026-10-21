large. First initialize the following four variables (with n = 1)

gA = \frac{e^{-z} z^{v}}{\Gamma(1+v)} = g(1+v, z),

gB = e^{-k} = g(1,k),

Sg = gB,

R = 1 - (gA)(Sg).

Then repeat the following loop beginning with n = 2 and increase increment n by one after each iteration. The loop is terminated when the contribution to the sum, R, is declining and is very small.

gA = gA\left(\frac{z}{n+v-1}\right) = g(n+v, z),

gB = gB\left(\frac{k}{n-1}\right) = g(n,k),

Sg = Sg + gB = g(1,k) + g(n,k),

R = R - (gA)(Sg) = the nth partial sum.

As each iteration, gA equals g(n+v,z), gB equals g(n,k) and Sg equals g(1,k)+⋯+g(n,k). The computation is easily done.

As for an approximation, Sankaran (1963) showed that the distribution of (χ′2_v/(v+k))^h is approximately normal with the expected value μ = 1 + h(h−1)P − h(2−h)mP^2/2 and variance σ^2 = h^2P(1+mP), where h = 1 − 2/3(v+k)(v+3k)(v+2k)^{-2}, P = (v+2k)/(v+k)^2 and m = (h−1)(1−3h). Using the approximation, we have approximately

Q(z,v,k) = Pr(χ′2 > z)

= Pr\left(\frac{χ′2}{v+k} > \frac{z}{v+k}\right)

= Pr\left(\left(\frac{χ′2}{v+k}\right)^h > \left(\frac{z}{v+k}\right)^h\right)

= Φ\left(\frac{1 - hP[1 - h + 0.5(2 - h)mP] - \left(\frac{z}{v+k}\right)^h}{h\sqrt{2P(1+mP)}}\right).