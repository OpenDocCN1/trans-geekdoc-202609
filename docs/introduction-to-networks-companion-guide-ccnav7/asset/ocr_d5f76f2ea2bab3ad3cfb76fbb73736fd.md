# Rule 1—Omit Leading Zeros (12.2.2)

The first rule to help reduce the number of digits in IPv6 addresses is to omit any leading 0s (zeros) in any hextet. Here are four examples of ways to omit leading 0s:

+   - 01ab can be represented as 1ab
- 09f0 can be represented as 9f0
- 0a00 can be represented as a00
- 00ab can be represented as ab

This rule only applies only to leading 0s—not to trailing 0s, which would make addresses ambiguous. For example, if both leading and trailing 0s could be omitted, the hextet abc could be either 0abc or abc0, but these do not represent the same value. Table 12-1 shows examples of omitting leading 0s.

Table 12-1 Omitting Leading 0s

| Type | Format |
|---|---|
| Preferred | 2001:0db8:0000:1111:0000:0000:0000:0200 |
| No leading 0s | 2001: db8: 0:1111: 0: 0: 0: 200 |
| Preferred | 2001:0db8:0000:00a3:ab00:0ab0:00ab:1234 |
| No leading 0s | 2001: db8: 0: a3:ab00: ab0: ab:1234 |
| Preferred | 2001:0db8:000a:0001:c012:90ff:fe90:0001 |
| No leading 0s | 2001: db8: a: 1:c012:90ff:fe90: 1 |
| Preferred | 2001:0db8:aaaa:0001:0000:0000:0000:0000 |
| No leading 0s | 2001: db8:aaaa: 1: 0: 0: 0: 0 |
| Preferred | fe80:0000:0000:0000:0123:4567:89ab:cdef |
| No leading 0s | fe80: 0: 0: 0: 123:4567:89ab:cdef |