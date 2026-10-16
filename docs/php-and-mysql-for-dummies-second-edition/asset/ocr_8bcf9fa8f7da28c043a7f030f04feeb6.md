| Character | Meaning | Example | Match | Not a Match |
|---|---|---|---|---|
| `{ , }` | The starting and ending number of a range of repetitions. | `a{2,5}` | `aa, aaaaa` | `a, xx3` |
| `\` | The following character is literal. | `m\*n` | `m*n` | `men, mean` |
| `( | | )` | A set of alternate strings. | `(Tom|Tommy)` | `Tom, Tommy` | `Thomas, To` |

Literal and special characters are combined to make patterns, which are sometimes long, complicated patterns. A string is compared to the pattern, and if it matches, the comparison is true. Some example patterns follow with a breakdown of the pattern and some sample matching and nonmatching strings:

+   `^[A-Z].*` — **Strings that begin with an uppercase letter**
+   
+   - `^[A-Z]` — Uppercase letter at the beginning of the string
+   - `.*` — A string of characters that is one or more characters long
+   
+   Strings that match:
+   
+   - Play it again, Sam
+   - I
+   
+   Strings that do not match:
+   
+   - play it again, Sam
+   - i

+   `Dear (son|daughter)` — **Two alternate strings**
+   
+   - `Dear` — Literal characters
+   - `(son|daughter)` — Either son or daughter
+   
+   Strings that match:
+   
+   - Dear son
+   - My Dear daughter
+   
+   Strings that do not match:
+   
+   - Dear Goliath
+   - son