# 11.5. GENERATING REMEMBER TOKENS

```
package rand

import (
    "crypto/rand"
    "encoding/base64"
)
```

There are multiple rand packages in Go, so be sure that your code is using the crypto/rand package if you are using an auto-importer! The math/rand package is NOT a secure way to generate remember tokens, but the crypto/rand package is because because it is based on a cryptographically strong pseudo-random generator. This is done differently for each operating system, but the docs state:

On Linux, Reader uses getrandom(2) if available, /dev/urandom otherwise. On OpenBSD, Reader uses getentropy(2). On other Unix-like systems, Reader reads from /dev/urandom. On Windows systems, Reader uses the CryptGenRandom API.

Understanding exactly what this means isn't necessary, but the short version is that crypto/rand package will help us generate random values safe for authentication purposes.

While we are looking at the documentation for the crypto/rand package, we might also notice that it doesn't provide us with an obvious way to generate random strings. Instead, we are going to need to leverage the Read function (shown below) to create our strings.

```
func Read(b []byte) (n int, err error)
```

The Read function works by taking a byte slice and filling it with random values. It returns two values: an integer and an error. The integer will be

> 7https://golang.org/pkg/crypto/rand/
8https://golang.org/pkg/crypto/rand/#ReadRandom