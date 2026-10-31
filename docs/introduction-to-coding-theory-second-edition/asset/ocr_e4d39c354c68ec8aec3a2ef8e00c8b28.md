1 = 1
ε = ε
ε² = ε²
ε³ = ε³
ε⁴ = ε + 1
ε⁵ = ε² + ε
ε⁶ = ε³ + ε²
ε⁷ = ε³ + ε + 1
ε⁸ = ε² - ε + 1
ε⁹ = ε³ - ε² + ε
ε¹⁰ = -ε³ + ε² + ε + 1
ε¹¹ = ε³ + ε²
ε¹² = -ε³ + 1
ε¹³ = -ε + 1
ε¹⁴ = -ε² + ε
ε¹⁵ = -ε³ + ε²
ε¹⁶ = -ε³ - ε - 1
ε¹⁷ = -ε² + 1
ε¹⁸ = -ε³ + ε
ε¹⁹ = ε² - ε - 1
ε²⁰ = ε³ - ε² - ε

ε²¹ = -ε³ - ε² + ε + 1
ε²² = -ε³ + ε² - 1
ε²³ = ε³ + ε - 1
ε²⁴ = ε² + 1
ε²⁵ = ε³ + ε
ε²⁶ = ε² + ε + 1
ε²⁷ = ε³ + ε² + ε
ε²⁸ = ε³ + ε² + ε + 1
ε²⁹ = ε³ + ε² - ε + 1
ε³⁰ = ε³ - ε² - ε + 1
ε³¹ = -ε³ - ε² - ε + 1
ε³² = -ε³ - ε² - 1
ε³³ = -ε³ + ε - 1
ε³⁴ = ε² + ε - 1
ε³⁵ = ε³ + ε² - ε
ε³⁶ = ε³ - ε² + ε + 1
ε³⁷ = -ε³ + ε² - ε + 1
ε³⁸ = ε³ - ε² - 1
ε³⁹ = -ε³ + 1
ε⁴⁰ = -1

For exponents higher than 40, use ε^{40+i} = -ε^{i}. In particular, ε is a primitive element.

The cyclotomic cosets in case q = 3, n = 20 are {0}, {10} and

{1, 3, 9, 7}, {2, 6, 18, 14}, {4, 12, 16, 8}, {5, 15}, {11, 13, 19, 17}.

Choose A = {1, …, 10}. The cyclotomic cosets avoiding Ã are C(0) and C(19), so C(A) is a [20,5,11]_3 code. We can choose as rows of a generator matrix G the words v(0,0) and v(j,1), j = 0,1,2,3. In order to write out the generator matrix, we just need to determine the trace function. As tr(x) = tr(x³) and tr(-x) = -tr(x), it suffices to calculate tr(ε^i), where i varies over representatives < 40 of the cyclotomic cosets C₈₀(i). We have

tr(0) = tr(ε) = tr(ε²) = tr(ε⁵) = tr(ε¹⁴) = tr(ε²⁰) = tr(ε²⁵) = 0
tr(1) = tr(ε⁴) = tr(ε⁷) = tr(ε⁸) = tr(ε¹⁰) = tr(ε¹³) = tr(ε¹⁷) = tr(ε²⁶) = 1
tr(ε¹¹) = tr(ε¹⁶) = tr(ε²²) = tr(ε²³) = -1

Choose α = ε⁴ as the generator of W. The following generator matrix for C(A) is obtained: