# Appendix 97C: Derivation of Equation (97.21)

This appendix presents a detailed derivation of the solution to equation (97.21). Partial differential equation, equation (97.20), is a logistic equation (or Verhulst model) first published by Pierre Verhulst (1845, 1847). To solve the logistic equation, we first rewrite equation (97.20) as a standard form of logistic equation.

dg(t)/dt = A g(t) (1 - g(t)/B). (97C.1)
where
A = λ r̄ / (2 - λ) and B = r̄.

Using separation of variables to separate g and t:
A dt = dg(t) / [g(t) (1 - g(t)/B)]
= dg(t)/g(t) + [dg(t)/B] / (1 - g(t)/B). (97C.2)

We next integrate both sides of equation (97C.2),
At + C = ln(g(t)) - ln(1 - g(t)/B). (97C.3)

Taking the exponential on both sides of equation (97C.3),
C · exp(At) = g(t) / (1 - g(t)/B). (97C.4)

When t = 0, g(t) = g0 and equation (97C.4) can be written as
C = g0 / (1 - g0/B) = B g0 / (B - g0). (97C.5)

Substitute equation (97C.5) into equation (97C.4),
(B g0)/(B - g0) · exp(At) = g(t) / (1 - g(t)/B). (97C.6)

Solving for g(t),
g(t) = [ (B g0)/(B - g0) exp(At) ] / [ 1 + ( (B g0)/(B - g0) exp(At) ) / B ]