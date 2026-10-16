The code looks better to me and describes the domain as we know it right now.

# The Romans were into DRY too...

Things start getting more complicated now. The Romans in their wisdom thought repeating characters would become hard to read and count. So a rule with Roman Numerals is you can't have the same character repeated more than 3 times in a row.

Instead you take the next highest symbol and then "subtract" by putting a symbol to the left of it. Not all symbols can be used as subtractors; only I (1), X (10) and C (100).

For example 5 in Roman Numerals is v. To create 4 you do not do IIII, instead you do IV.

# Write the test first

```
{"4 gets converted to IV (can't repeat more than 3 times)", 4, "IV"},
```

# Try to run the test

```
===
RUN
TestRomanNumerals/4_gets_converted_to_IV_(cant_repeat_more_than
_3_times)
---
FAIL:
TestRomanNumerals/4_gets_converted_to_IV_(cant_repeat_more_than
_3_times) (0.00s)
    numeral_test.go:24: got 'IIII', want 'IV'
```

# Write enough code to make it pass

```
func ConvertToRoman(arabic int) string {
```