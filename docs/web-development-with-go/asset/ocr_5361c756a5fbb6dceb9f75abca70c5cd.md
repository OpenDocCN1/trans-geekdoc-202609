Run it and verify that your output matches the output below. If you change the secret key your output will change, but as long as you have the same secret key it should be him same.

```
$ go run exp/main.go
```

```
4waUC1cnuxomoM2UoJfpGGLPlasj35y?teweSFgPy=
```

# Source code

The links below have the completed source code and a diff of all the code changed in this section.

Completed - book.usegolang.com/11.6.3

Changes - book.usegolang.com/11.6.3-diff

# 11.7 Hashing remember tokens in the user service

We have all the tools in our application to generate and hash remember tokens. The next step towards completing our authentication system is to update our user service to utilize these pieces when updating and creating users, and then expose a function that allows us to lookup a user by their remember token.

This section is broken into several smaller subsections, and then we will test all of the changes in the final section using our experimental main.go source file.