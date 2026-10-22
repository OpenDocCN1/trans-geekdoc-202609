# Refactoring The Tests

Wait! What happened? Aha, I forgot to add in code to handle these values correctly. Let me do that now.

```
1. case $currentValue % 100 === 0:
2. $result .= 'C';
3. $currentValue -= 100;
4. break;
5. case $currentValue % 50 === 0:
6. $result .= 'L';
7. $currentValue -= 50;
8. break;
9. case $currentValue % 10 === 0:
10. $result .= 'X';
11. $currentValue -= 10;
12. break;
```

Now the tests pass.

```
OK (9 tests, 9 assertions)
```

Now, I go to the Wikipedia page for Roman numerals and add some values in the data set, refactoring them to have them in numeric order:

```
1. return [
2. [1, 'I'],
3. [2, 'II'],
4. [3, 'III'],
5. [4, 'IV'],
6. [5, 'V'],
7. [9, 'IX'],
8. [10, 'X'],
9. [14, 'XIV'],
10. [15, 'XV'],
11. [29, 'XXIV'],
12. [40, 'XL'],
13. [44, 'XLIV'],
14. [49, 'XXXIX'],
15. [50, 'L'],
16. [57, 'LVII'],
17. [63, 'LXIII'],
18. [78, 'LXXVIII'],
19. [82, 'LXXXII'],
20. [91, 'XCI'],
21. [100, 'C']
22. ];
```