![](bbox=[0.265, 0.105, 0.82, 0.345])

# Exercises

to-do ... more on the way ...

+   12.1. Suppose Enc-then-MAC+AD is instantiated with CBC mode and any secure MAC, as described in Construction 12.4. The scheme is secure for fixed-length associated data. Show that if variable-length associated data is allowed, then the scheme does **not** provide AEAD security.
+   
+   Note: you are not attacking the MAC! Take advantage of the fact that \(d||c\) is ambiguous when the length of \(d\) is not fixed and publicly known.

+   12.2. Suggest a way to make Construction 12.4 secure for variable-length associated data. Prove that your construction is secure.

+   12.3. Show that if you know the salt s of the Poly-UHF construction (Construction 12.9), you can efficiently find a collision.

+   12.4. Show that if you are allowed to see only the output of Poly-UHF (i.e., the salt remains hidden), on chosen inputs then you can compute the salt.