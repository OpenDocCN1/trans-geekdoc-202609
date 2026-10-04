| Type | Format |
|---|---|
| Preferred | fe80:0000:0000:0000:0000:0000:0000:0001 |
| No leading 0s | fe80: 0: 0: 0: 0: 0: 0: 1 |
| Preferred | 0000:0000:0000:0000:0000:0000:0000:0001 |
| No leading 0s | 0: 0: 0: 0: 0: 0: 0: 1 |
| Preferred | 0000:0000:0000:0000:0000:0000:0000:0000 |
| No leading 0s | 0: 0: 0: 0: 0: 0: 0: 0 |

# Rule 2—Double Colon (12.2.3)

The second rule to help reduce the number of digits in IPv6 addresses is that a double colon (::) can replace any single, contiguous string of one or more 16-bit hextets consisting of all 0s. For example, 2001:db8:cafe:1:0:0:0:1 (leading 0s omitted) could be represented as 2001:db8:cafe:1::1. The double colon (::) is used in place of the three all-0 hextets (0:0:0).

The double colon (::) can be used only once in an address; if it could be used more than once, the address could expand to more than one possible result. Using the double colon rule and also omitting leading 0s—commonly known as compressed format—often allows you to greatly reduce the number of characters in an IPv6 address.

Here is an example of the incorrect use of the double colon: 2001:db8::abcd::1234. The double colon is used twice in this example, which you know violates the rule. This incorrect compressed format address could be expanded multiple ways:

+   - 2001:db8::abcd:0000:0000:1234
- 2001:db8::abcd:0000:0000:0000:1234
- 2001:db8:0000:abcd::1234
- 2001:db8:0000:0000:abcd::1234

If an address has more than one contiguous string of all-0 hextets, best practice is to use the double colon (::) on the longest string. If the strings are equal, the first string should use the double colon (::). Table 12-2 shows examples of omitting leading 0s and all 0 segments.