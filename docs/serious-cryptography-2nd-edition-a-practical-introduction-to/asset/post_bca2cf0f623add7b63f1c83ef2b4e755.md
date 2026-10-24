
such as encryption, signature, and key agreement faster than their classical counterparts. Most cryptographic applications that rely on the discrete logarithm problem (DLP) also work when based on its elliptic curve counterpart, ECDLP, with one notable exception: the Secure Remote Password (SRP) protocol.

This chapter focuses on applications of ECC and discusses when and why to use ECC over RSA or classical Diffie–Hellman, as well as how to choose the right elliptic curve for your application.

## What Is an Elliptic Curve?

An elliptic curve is a *curve* on a plane—a set of points with x- and y-coordinates. A curve’s equation defines all the points that belong to that curve. For example, the curve y = 3 is a horizontal line with the vertical coordinate 3, curves of the form y = ax + b with fixed numbers a and b are straight lines, x² + y² = 1 is a circle of radius 1 centered on the origin, and so on. Whatever the type of curve, the points on a curve are (x, y) pairs that satisfy the curve’s equation.

In cryptography, an elliptic curve typically has an equation in the form y² = x³ + ax + b (the *Weierstrass form*), where the constants a and b define the shape of the curve. For example, Figure 12-1 shows the elliptic curve that satisfies the equation y² = x³ − 4x.

![](img/ace4de942d037de8ea5835bc9fbe57cd_259_0.png)

*Figure 12-1: An elliptic curve with the equation y² = x³ − 4x, shown over the real numbers*

This figure displays all the points that make up the curve for x between −3 and 4, be they points on the left side of the curve, which looks like a circle, or on the right side, which looks like a parabola. All points have (x, y) coordinates that satisfy the curve’s equation y² = x³ − 4x. For example, when x = 0, then y² = x³ − 4x = 0³ − 4 × 0 = 0; hence, y = 0 is a solution, and the point (0, 0) belongs to the curve. Likewise, if x = 2, the solution to the equation is y = 0, meaning that the point (2, 0) belongs to the curve.

> **NOTE**
>
> *In this chapter, I focus on the simplest, most common type of elliptic curves—those with an equation like y² = x³ + ax + b—but other elliptic curves have equations in different forms. For example, Edwards curves have equations of the form x² + y² = 1 + d x² y². Cryptographers sometimes use Edwards curves (for example, in the Ed25519 scheme).*

When using elliptic curves for cryptography, it’s crucial to distinguish points that belong to the curve from other points, as points off the curve often present a security risk. However, the curve’s equation doesn’t always admit solutions, at least not in the natural number plane. For example, to find points with the horizontal coordinate x = 1, you solve y² = x³ − 4x and obtain y² = x³ − 4x = 1³ − 4 × 1, resulting in −3. But y² = −3 doesn’t have a solution because there’s no number for which y² = −3. There exists a solution in the complex numbers (√3i), but in practice, elliptic curve cryptography uses only natural numbers (ECC works with integer numbers modulo a prime number, either directly or via polynomials). Because there’s no solution to the curve’s equation for x = 1, the curve has no point at that position on the x-axis, as you can see in Figure 12-1.

If you try to solve for x = −1, you get the equation y² = −1 + 4 = 3, which has two solutions (y = √3 ≈ 1.73 and y = −√3 ≈ −1.73), the square root of 3 and its negative value. The square of both values is 3, and Figure 12-1 has two points with x = −1. More generally, the curve is symmetric with respect to the x-axis for all points that satisfy its equation (as are all elliptic curves of the form y² = x³ + ax + b, except for y = 0).

## Elliptic Curves over Integers

Here’s a bit of a twist: the curves in elliptic curve cryptography don’t actually look like Figure 12-1. They’re neither curves nor ellipses. They look instead like Figure 12-2, which is a cloud of points rather than a curve. What’s going on here?

![](img/ace4de942d037de8ea5835bc9fbe57cd_261_0.png)

*Figure 12-2: The elliptic curve with the equation \(y^2 = x^3 - 4x\) over \(\mathbb{Z}_{191}\), the set of integers modulo 191*

Figures 12-1 and 12-2 are based on the same curve equation, \(y^2 = x^3 - 4x\), but they show the curve’s points with respect to different sets of numbers: Figure 12-1 shows the curve’s points over the set of *real numbers*, which includes negative numbers, decimals, and so on. For example, as a continuous curve, it shows the points at \(x = 2.0, x = 2.1, x = 2.00002\), and so on. Figure 12-2, on the other hand, shows only *integers* that satisfy this equation, which excludes decimal numbers. Specifically, Figure 12-2 shows the curve \(y^2 = x^3 - 4x\) with respect to the integers *modulo 191*: 0, 1, 2, 3, up to 190. You can denote this set of numbers \(\mathbb{Z}_{191}\). (There’s nothing special with 191 here, except that it’s a prime number. I picked a small number to avoid having too many points on the graph.) The points in Figure 12-2 therefore all have x- and y-coordinates that are integers modulo 191 and that satisfy the equation \(y^2 = x^3 - 4x\). For example, for \(x = 2\), you have \(y^2 = 0\), for which \(y = 0\) is a valid solution. This tells you that the point \((2, 0)\) belongs to the curve.

If \(x = 3\), you get the equation \(y^2 = 27 - 12 = 15\), which admits two solutions in \(\mathbb{Z}_{191}\), 46 and 145. Indeed, \(46^2 = 2,116\), with \(2,116 \bmod 191 = 15\), and \(145^2 = 21,025\), with \(21,025 \bmod 191 = 15\). Thus, the points \((3, 46)\) and \((3, 145)\) both belong to the curve and appear as in Figure 12-2 (the two points circled on the left).

> **NOTE**
>
> Figure 12-2 considers points from the set denoted \(\mathbb{Z}_{191} = \{0, 1, 2, \ldots, 190\}\), which includes zero. This differs from the groups denoted \(\mathbb{Z}_p^*\) (with a star superscript) that we discussed in the context of RSA and Diffie–Hellman. The reason for this difference is that you’ll both multiply and add numbers, and you therefore need to ensure that the set of numbers includes addition’s identity element (namely 0, such that \(x + 0 = x\) for every \(x \in \mathbb{Z}_{191}\)).
>
> Also, every number \(x\) has an inverse with respect to addition, denoted \(-x\), such that \(x + (-x) = 0\). For example, the inverse of 100 in \(\mathbb{Z}_{191}\) is 91 because \(100 + 91 \mod 191 = 0\). Such a set of numbers, where addition and multiplication are possible and where each element \(x\) admits an inverse with respect to addition (denoted \(-x\)) as well as an inverse (except for the element zero) with respect to multiplication (denoted \(1/x\)), is called a field. When a field has a finite number of elements, as in \(\mathbb{Z}_{191}\) and as with all fields used for elliptic curve cryptography, it is a finite field.

## The Addition Law

Now that you know that the points on an elliptic curve are coordinates \((x, y)\) that satisfy the curve’s equation, \(y^2 = x^3 + ax + b\), let’s look at how to add elliptic curve points with the addition law.

### Adding Two Points

Say you want to add two points on the elliptic curve, \(P\) and \(Q\), to give a new point, \(R\), that is the sum of these two points. The simplest way to understand point addition is to determine the position of \(R = P + Q\) on the curve relative to \(P\) and \(Q\) based on a geometric rule: draw the line that connects \(P\) and \(Q\), find the other point of the curve that intersects with this line, and \(R\) is the reflection of this point with respect to the x-axis. For example, in Figure 12-3, the line connecting \(P\) and \(Q\) intersects the curve at a third point between \(P\) and \(Q\), and the point \(P + Q\) is at the same x-coordinate but the inverse y-coordinate.

![](img/ace4de942d037de8ea5835bc9fbe57cd_263_0.png)

*Figure 12-3: A general case of the geometric rule for adding points over an elliptic curve*

This geometric rule is simple, but it won’t directly give you the coordinates of the point R. You compute the coordinates (x_R, y_R) of R using the coordinates (x_P, y_P) of P and the coordinates (x_Q, y_Q) of Q using the formulas x_R = m² − x_P − x_Q and y_R = m(x_P − x_R) − y_P, where the value m = (y_Q − y_P) / (x_Q − x_P) is the slope of the line connecting P and Q.

Unfortunately, these formulas and the line-drawing trick in Figure 12-3 don’t always work. If, for example, P = Q, you can’t draw a line between two points (there’s only one), and if Q = −P, the line doesn’t cross the curve again, so there’s no point on the curve to mirror. We’ll explore these in the next sections.

### Adding a Point and Its Negative

The negative of a point P = (x_P, y_P) is the point −P = (x_P, −y_P), which is the point mirrored around the x-axis. For any P, you can say that P + (−P) = O, where O is the point at infinity. As in Figure 12-4, the line between P and −P runs to infinity and never intersects the curve. The point at infinity is to elliptic curves what zero is to integers, except that it’s only a “virtual” point that you can’t locate at a specific place, because it’s infinitely far.
