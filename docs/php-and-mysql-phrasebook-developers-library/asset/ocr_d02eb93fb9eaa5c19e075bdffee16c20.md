Which outputs:

`<p> <b> </b> </p>`

One advantage of PCRE or POSIX is that some special constructs are supported. For instance, usually regular expressions are matched greedily. Take, for instance, this regular expression:

`<.*>`

When trying to match this in the following string

`<p>Sex, drugs and <b>PHP</b>.</p>`

what do you get? You get the complete string. Of course, the pattern also matches on `<p>`, but regular expressions try to match as much as possible. Therefore, you usually have to do a clumsy workaround, such as `<[^>]*>`. However, it can be done more easily. You can use the ? modifier after the * quantifier to activate nongreedy matching.

# Validating Mandatory Input

```
function checkNotEmpty($s) {
  return (trim($s) != "");
}
```

When validating form fields (see Chapter 4 for more about HTML forms), several checks can be done. However, you should test as little as possible. For instance, when recently trying to order concert tickets for a U.S. concert, I failed to complete the order because the form expected a U.S. telephone number, which I could not provide.

The best check is to check whether there is any input at all. However, what is considered to be any input? If