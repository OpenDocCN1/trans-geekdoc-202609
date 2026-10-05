# 11.6.2 Using the crypto/hmac package

We discussed HMAC in Section 11.4.1, but the general idea behind HMAC is that it uses a secret key to sign data, and then uses a hashing function to hash the signed data. In doing this, it makes harder to figure out what data was used to construct the hash unless you know both the function used and the secret key.

Doing this manually is possible, but Go provides us with the crypto/hmac[`crypto/hmac`] package to make our lives a little easier. Inside of this package there is the New function, which takes two pieces of information - a function that returns a hash.Hash implementation and the secret key - and then returns an implementation of the hash.Hash interface.

```
func New(h func() hash.Hash, key []byte) hash.Hash
```

It is important to note that we have to provide a function that returns a hash here, not a hash itself.

What this means is that we can use the crypto/hmac package to construct a hash.Hash implementation, and then use it exactly like we discussed in Section 11.6.1.

Looking at the rest of the docs for the crypto/hmac package, there is an example in the overview that illustrates how to use the New function provided by the crypto/hmac package:

```
mac := hmac.New(sha256.New, key)
```

In this line of code we are stating that we want to create an HMAC hash that is backed by the secret key stored in the key variable, and we intend to use the SHA256 hashing function once the data is digitally signed. The SHA256