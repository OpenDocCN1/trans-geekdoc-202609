| Age | Sex | Education Level | Poverty Income Ratio | Lead Level |
|---|---|---|---|---|
| 77 | Male | MoreThanHS | 5.00 | 5.0 |
| 49 | Male | MoreThanHS | 5.00 | 1.6 |
| 37 | Male | MoreThanHS | 4.93 | 2.4 |
| 70 | Male | LessThanHS | 1.07 | 1.6 |
| 81 | Male | LessThanHS | 2.67 | 5.5 |
| 38 | Female | MoreThanHS | 4.52 | 1.5 |

Figure 22.7: Head of the NHANES Sample Data.

easily by using their names: @fig-figname or @tab-tablename. The knitted pdf substitutes the appropriate figure or table number into your text. Additionally, we can reference sections by adding in labels to the section header. For example, we added the tag #sec-awesome for the section in the following text and can now reference it using @sec-awesome.

```
## Awesome Stuff {#sec-awesome}
```

# 22.4 Adding in Equations

Another useful option in Markdown is to add in mathematical equations. If you want to insert math equations, you can do so by writing LaTeX expressions. To write a math equation inline, you put a single dollar sign $ on either side of your equation, and to write a math equation on its own line, you put a double dollar sign $$ on either side of the equation, like so:

Here's an equation that is inline with the text: $5x^2 + 9x^3$ produces $5x^2 + 9x^3$. On the other hand, here's an equation that is on its own line: $$5x^2 + 9x^3$$ produces

$5x^2 + 9x^3$

Here is some other LaTeX notation that you should know in order to write common equations: * To create a fraction, type \frac{numerator}{denominator}. For example, \frac{2}{3} produces 2/3. * To create a subscript, type _. For