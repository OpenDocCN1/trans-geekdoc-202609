![](bbox=[0.25, 0.08, 0.86, 0.45])

Figure 12-3: A general case of the geometric rule for adding points over an elliptic curve

This geometric rule is simple, but it won’t directly give you the coordinates of the point R. You compute the coordinates (x_R, y_R) of R using the coordinates (x_P, y_P) of P and the coordinates (x_Q, y_Q) of Q using the formulas x_R = m² − x_P − x_Q and y_R = m(x_P − x_R) − y_P, where the value m = (y_Q − y_P) / (x_Q − x_P) is the slope of the line connecting P and Q.

Unfortunately, these formulas and the line-drawing trick in Figure 12-3 don’t always work. If, for example, P = Q, you can’t draw a line between two points (there’s only one), and if Q = −P, the line doesn’t cross the curve again, so there’s no point on the curve to mirror. We’ll explore these in the next sections.

# Adding a Point and Its Negative

The negative of a point P = (x_P, y_P) is the point −P = (x_P, −y_P), which is the point mirrored around the x-axis. For any P, you can say that P + (−P) = O, where O is the point at infinity. As in Figure 12-4, the line between P and −P runs to infinity and never intersects the curve. The point at infinity is to elliptic curves what zero is to integers, except that it’s only a “virtual” point that you can’t locate at a specific place, because it’s infinitely far.