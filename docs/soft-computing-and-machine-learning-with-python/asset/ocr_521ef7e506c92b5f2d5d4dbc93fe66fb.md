# A Python 2.7 Programming Tutorial 181

```
>>> ticket_no = 147
>>> "Ticket {num:0{w}d}".format(num=ticket_no, w=how_wide)
'Ticket 00000147'
```

Here, where the width is expected, "{w}" appears. Because there is a keyword argument that is effectively w=8, the value "8" is used for the width.

# Note

The string .format() method has been available only since Python 2.6. If you are looking at older code, you may see a different technique using the "%%" operator. For example, 'Attila the %s' %Bun' yields 'Attila the bun'. For an explanation, see the Python library documentation. However, the old format operator is deprecated.

# SEQUENCE TYPES

Mathematically, a sequence in Python represents an ordered set.
Sequences are an example of container classes: values that contain values inside them.

| Type name | Contains | Examples | Mutable |
|---|---|---||}{
| str | 8-bit characters | "abc" 'abc' '"' '\\n\x00' | No |
| unicode | 32-bit characters | u'abc' u\u000c' | No |
| list | Any values | [23, "Ruth", 69.8] [] | Yes |
| tuple | Any values | (23, "Ruth", 69.8) (44,) | No |

str and unicode are used to hold text, that is, strings of characters.

+   - list and tuple are used for sequences of zero or more values of any type. Use a list if the contents of the sequence may change; use a tuple if the contents will not change, and in certain places where tuples are required. For example, the right-hand argument of the string format operator (see Section 3.4, "The string format method") must be a tuple if you are formatting more than one value.
- To create a list, use an expression of the form
- [ expr1, expr_j, ... ] with a list of zero or more values between square brackets, "[...".