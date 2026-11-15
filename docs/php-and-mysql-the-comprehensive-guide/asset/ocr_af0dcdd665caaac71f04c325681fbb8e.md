Two months and issues later, in May 1997, the overdue correction appeared in a small box in the margin. The author admitted that he had not checked his claims at all, although this would have been technically very easy. He also claimed to have had an idea for how to "steal" the cookie information, but printed the possible result (cookies are insecure) without checking it. As it turned out, it was not possible. The author violated crucial basic journalistic rules, but the damage had already been done. Even today, many people are still unaware of what cookies are and what risks they entail (see also Section 14.5)—and which risks are simply scaremongering. Completely free of all prejudices and concerns, we will now look at how cookies can be used in PHP.

# ## 14.3 Working with Cookies in PHP

As noted, cookie processing (read/write) takes place entirely via HTTP headers. But PHP would not be PHP if this laborious process had to be carried out by the user.

# ## 14.3.1 Set Cookies

The setcookie() function has two different syntax options. The most common is the following syntax (we will deal with the alternative later):

```
boolean setcookie ( string name [, string value [, int expires [, string path [, string domain [, bool secure[, bool httponly]]]]]])
```

Table 14.1 explains the meanings of the seven parameters. Based on that quantity, you will appreciate PHP’s feature of named function parameters, but this will have to wait a few more pages, because there is a special feature to consider first.

| Parameters | Description | Data type |
| :--- | :--- | :--- |
| name | The name of the cookie; this parameter is the only mandatory one. All others are optional. | String |
| value | The value of the cookie. | String |
| expires | The expiration date of the cookie as the number of seconds since 1.1.1970. | Integer |
| path | The directory from which the cookie may be read. | String |
| domain | The domain that has access to the cookie. | String |
| secure | A value that specifies whether the cookie may only be sent via HTTPS connections or not. | Boolean |
| httponly | Indicates whether the cookie is "invisible" for JavaScript or not. | Boolean |

Table 14.1 The Parameters for "setcookie()"