functions specifically designed for hashing and checking passwords, and that’s what we’ll use here.

If you’re following along, please go ahead and download the latest version of the golang.org/x/crypto/bcrypt package:

```
$ go get golang.org/x/crypto/bcrypt@latest
go: downloading golang.org/x/crypto v0.26.0
go get: added golang.org/x/crypto v0.26.0
```

There are two functions that we’ll use in this book. The first is the bcrypt.GenerateFromPassword() function which lets us create a hash of a given plain-text password like so:

```
hash, err := bcrypt.GenerateFromPassword([]byte("my plain text password"), 12)
```

This function will return a 60-character long hash which looks a bit like this:

```
$2a$12$NuTjWXm3KNktReFwBVyHyuf/to.HEwTy.eS206TNfKgFr6GzGJSWG
```

The second parameter that we pass to bcrypt.GenerateFromPassword() indicates the cost, which is represented by an integer between 4 and 31. The example above uses a cost of 12, which means that 4096 (2^12) bcrypt iterations will be used to generate the password hash.

The higher the cost, the more expensive the hash will be for an attacker to crack (which is a good thing). But a higher cost also means that our application needs to do more work to create the password hash when a user signs up — and that means increased resource use by your application and additional latency for the end user. So choosing an appropriate cost value is a balancing act. A cost of 12 is a reasonable minimum, but if possible you should carry out load testing, and if you can set the cost higher without adversely affecting user experience then you should.

On the flip side, we can check that a plain-text password matches a particular hash using the bcrypt.CompareHashAndPassword() function like so:

```
hash := []byte("$2a$12$NuTjWXm3KNktReFwBVyHyuf/to.HEwTy.eS206TNfKgFr6GzGJSWG")
err := bcrypt.CompareHashAndPassword(hash, []byte("my plain text password"))
```

The bcrypt.CompareHashAndPassword() function will return nil if the plain-text password matches a particular hash, or an error if they don’t match.