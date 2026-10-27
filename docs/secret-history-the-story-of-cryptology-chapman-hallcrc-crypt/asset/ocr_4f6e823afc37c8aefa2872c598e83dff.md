# Chapter 20

# Suite B All-Stars

In 2005, The National Security Agency (NSA) made public a list of recommended cryptographic algorithms and protocols. Known as “Suite B,” these are believed to be the best of the unclassified schemes of that era. Two of them are covered in the present chapter.

# 20.1 Elliptic Curve Cryptography

Following Diffie-Hellman and RSA, another method of carrying out public key cryptography was independently discovered in 1985 by Neal Koblitz (Figure 20.1) and Victor S. Miller (Figure 20.2). One of the advantages of their elliptic curve cryptography is the appearance (no proof yet!) of a level of security equivalent to RSA with much smaller keys. For example, it’s been estimated that a 313-bit elliptic curve key is as secure as a 4096-bit RSA key.¹

Before we can detail the cryptographic application of these curves, some background must be provided. An elliptic curve is the set of solutions to an equation of the form y² = x³ + ax + b, as well as a point at infinity, ∞. We refer to these as Weierstrass equations, in honor of Karl Weierstrass (Figure 20.3), who studied them in the 1800s, long before they were suspected of having any cryptographic applications.² So, as with the work of Fermat and Euler, we once again see that the eventual uses of mathematical results are impossible to predict! Despite the naming honor, work on elliptic curves goes back much farther than Weierstrass:³

Elliptic curves have a long, rich history in several areas of mathematics. The so-called “chord and tangent” method for adding points on an elliptic curve actually goes back to Diophantus in the third century.

The long history shouldn’t be surprising, because, as Koblitz pointed out, “Elliptic curves are the simplest type of curve that is more complicated than a conic section.”⁴ It’s just a small step from degree 2 to 3.

¹ Blake, Ian, Gadiel Seroussi, and Nigel Smart, Elliptic Curves in Cryptography, London Mathematical Society Lecture Note Series, Vol. 265, Cambridge University Press, Cambridge, UK, 1999, p. 9.

² Other “big names” who studied elliptic curves include Abel, Jacobi, Gauss, and Legendre.

³ Koblitz, Neal, Random Curves: Journeys of a Mathematician, Springer, Berlin, Germany, 2008, p. 313.

⁴ Koblitz, Neal, Random Curves: Journeys of a Mathematician, Springer, Berlin, Germany, 2008, p. 303.