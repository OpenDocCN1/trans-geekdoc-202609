# 9.4. A Brief Survey of the Go Standard Library

The encoding package contains several packages, one of which, encoding/binary, we have already used for reading and writing binary data (§8.1.5, 387). The other packages provide encoding and decoding for various formats—for example, the encoding/base64 package can be used to encode and decode URLs which often use this format.

# 9.4.5. Graphics-Related Packages

Go's image package provides some high-level functions and types for creating and holding image data. It also has a number of packages that provide encoders and decoders for various graphics file formats, such as image/jpeg and image/png. We discussed some of these earlier in this chapter (§9.1.2, 416) and in Chapter 7’s exercises.

The image/draw package provides basic drawing functionality as we saw in Chapter 6 (§.5.2, 289). The third-party freetype package adds more functions for drawing. The freetype package itself can draw text using any specified TrueType font, and the freetype/raster package can draw lines and cubic and quadratic curves (We discussed obtaining and installing the freetype package earlier; §9.2, 417)

# 9.4.6. Miscellaneous Packages

The math/big package provides unlimited (except by memory) size integers (big.Int) and rationals (big.Rat). These were discussed earlier (§2.3, 57). The pi_digits example shows the use of big.Ints (§2.3.1.1, 61). The math/big package also provides a big.ProbablyPrime() function.

The math package provides all the standard mathematical functions (based on float64s) and standard constants. See Tables 2.8, 2.9, and 2.10 (65–67)

The math/complex package provides some standard functions for complex numbers (based on complex128). See Table 2.21 (71)

# 9.4.7. Miscellaneous Packages

In addition to the packages that can be roughly grouped together, the standard library contains a number of packages that stand more or less alone.

The crypto package can provide hashes using the MD5, SHA-1, SHA-224, SHA-256, SHA-384, and SHA-512 algorithms. (For support each by a package, e.g., crypto/sha512.) In addition, the crypto package has packages that provide encryption and decryption using a variety of algorithms, such as AES, DES, and so on, in packages with corresponding names (e.g., crypto/aes, crypto/des).