Domain-specific hardware architecture: Reinforcing the need to invest in hardware streamlining to get the most out of many parallel processing engines, consistent with the recommendations of Hennessy, Patterson, and Dally [27, 63]. The ability to reduce transistor feature size (i.e., Moore’s Law; allowing more transistors to be packed into a given physical area), while at the same time operating at higher clock frequencies, has ended [67] (i.e., the end of Denard Scaling).

Leiserson al showed the potential orders of magnitude improvement performance gains in software coding and hardware instructions. Using the simple example of multiplying two 4096 × 4096 matrices, they demonstrated an absolute speed-up of 62,806x relative to software code written in Python, by exploiting several software- and hardware-related knobs, such as the C language, parallel loops, vectorization, and Intel’s Advanced Vector Extensions.

An absolute speed-up of 62,806x, for that simple example of multiplying two matrices, translates into the following observations:

+   - Moore’s Law had continued (at 2x every 1.5 years), it would have taken about 24 years to achieve that same absolute speed-up.

+   - As shown by Hennessy and Patterson [27], since about 2015, architectural hardware optimizations have reached a plateau, improving at about 2x twenty years (or about 3 percent every year). Therefore, at this rate, it would have taken about 318 years to achieve that same absolute speed-up!

We conclude this section by recalling one of the pitfalls highlighted by Dean et al., “designing ML hardware assuming the ML software is untouchable” [69]. Instead, as they pointed out, the goal should be a hardware and software system that more effectively solves the problem. ML models offer opportunity for coding by using domain-specific hardware together with software performance optimizations.

In the next section, we compare several modern microprocessors in terms of throughput and peak power for different levels of arithmetic precision. We also discuss classes of parallelism suitable for ML models. Since power usage is of paramount importance, we look briefly at energy consumption for chips targeted at embedded applications.

# 5.7 Contemporary Computing Engines and Integrated Systems

The background provided in sections 5.4–5.6 helps the reader better understand the capabilities available in contemporary microprocessors and cluster-level computing systems, specifically designed for high-performance applications (such as AI applications).