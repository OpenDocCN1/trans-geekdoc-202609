# 3.6. Other String-Related Packages

Table 3.16 The Regexp Package's Quantifiers

| Syntax | Description |
| e? or e{0,1} | Greedily match zero or one occurrence of expression e |
| e+ or e{1,} | Greedily match one or more occurrences of expression e |
| e* or e{0,} | Greedily match zero or more occurrences of expression e |
| e{m,} | Greedily match at least m occurrences of expression e |
| e{n} | Greedily match at most n occurrences of expression e |
| e{m,n} | Greedily match at least m and at most n occurrences of expression |
| e?? or e{0,1} | Nongreedily match zero or one occurrence of expression e |
| e+ or e{1,} | Nongreedily match one or more occurrences of expression e |
| e* or e{0,} | Nongreedily match zero or more occurrences of expression e |
| e{m,} | Nongreedily match at least m occurrences of expression e |
| e{n,} | Nongreedily match at most n occurrences of expression e |
| e{m,n?} | Nongreedily match at least m and at most n occurrences of expression e |

Table 3.17 The Regexp Package's Flags and Groups

| Syntax | Description |
| i | Match case-insensitively (the default is case-sensitive matching) |
| m | Multiline mode makes ^ and $ match at the start and end of every line (the default is single-line mode) |
| s | . match any character including newlines (the default is . to match any character except newlines) |
| U | Make greedy nongreedy and vice versa; i.e., swap the meaning of ? after a quantifier (the default is matches to be greedy unless their quantifier is followed by ? to make nongreedy) |
| (?flags) | Apply the given flags from this point on (precede the flag or flags with - to negate) |
| (?flags:e) | Apply the given flags to expression e (precede the flag or flags with - to negate) |
| (e) | Group and capture the match for expression e |
| (?P<name>e) | Group and capture the match for expression e using the capture name name |
| (::e) | Group don't capture the match for expression e |