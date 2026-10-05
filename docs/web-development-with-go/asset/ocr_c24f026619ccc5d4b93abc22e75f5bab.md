# 11.5. GENERATING REMEMBER TOKENS

```
User:
ID: 1
Email: jon@calhoun.io
```

The first thing we would do when this user logs in is to create a random string for a remember token. We will be writing code to do this shortly, but for now assume that it is 0f08bc520e71. Once we create this string, we would map it to a user and store that information in our database.

```
User:
ID: 1
Email: jon@calhoun.io
RememberToken: 0f08bc520e71
```

The next thing we would do is set a cookie on the user with the name remember_token and the value 0f08bc520e71. When the user logs in, we now have a way to look up the user in our database without using anything easily faked like an email address or an ID.

# 11.5 Generating remember tokens

In order to create remember tokens we need to do a few things, but the first we need is a way to generate our remember tokens. As mentioned in Section 11.4.2, we need to generate these randomly so that they can't easily faked and lead to users pretending to be someone they are not. In this section we will focus on writing a package that will allow us to generate random strings that we can use as remember tokens.

To do this, we are going to need to cover some more advanced topics that might not be easy to grasp at first. Unfortunately, this isn't something we can easily simplify. Cutting any corners in this section could ultimately leave your