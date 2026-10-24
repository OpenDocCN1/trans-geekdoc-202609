the Go language has the following function in its crypto package (from *https://go.dev/src/crypto/rsa/rsa.go*):

```
func EncryptOAEP(hash hash.Hash, random io.Reader, pub *PublicKey, msg []byte,
label []byte) (out []byte, err error)
```

The function EncryptOAEP() takes a hash function, a PRNG, a public key, a message, and a label (an optional parameter of OAEP) and returns a ciphertext and an error code. When you call EncryptOAEP(), it calls encrypt() to compute the RSA function given the padded data, as Listing 10-3 shows.

```
func encrypt(c *big.Int, pub *PublicKey, m *big.Int) *big.Int {
    e := big.NewInt(int64(pub.E))
    c.Exp(m, e, pub.N)
    return c
}
```

*Listing 10-3: The implementation of the core RSA encryption function from the Go language cryptography library*

The main operation here is `c.Exp(m, e, pub.N)`, which raises a message, m, to the power e modulo pub.N, and assigns the result to the variable c.

If you choose to implement RSA instead of using a readily available library function, be sure to rely on an existing *big-number* library, which is a set of functions and types that allow you to define and compute arithmetic operations on large numbers thousands of bits long. For example, you might use the GNU Multiple Precision (GMP) arithmetic library in C or in Go’s big package. (Believe me, you don’t want to implement big-number arithmetic yourself.)

Even if you just use a library function when implementing RSA, ensure you understand how the internals work so you can assess the risk and whether it matches the application’s security requirements.

# A Fast Exponentiation Algorithm

*Exponentiation* is the operation of raising x to the power e, when computing x^e mod n. When working with big numbers, as with RSA, this operation can be extremely slow if naively implemented. How to efficiently compute exponentiations?

The naive way to compute x^e mod n takes e − 1 multiplications, as the pseudocode algorithm in Listing 10-4 demonstrates.

```
expModNaive(x, e, n) {
    y = x
    for i = 1 to e − 1 {
        y = y * x mod n
    }
}
```