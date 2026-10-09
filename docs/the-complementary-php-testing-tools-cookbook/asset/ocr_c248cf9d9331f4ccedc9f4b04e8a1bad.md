# 3. MUTATION TESTING

The framework I am using provided the bootstrap.php file for me. Check the documen-
tation for your framework for more details, or if you are using a custom solution, you'll have
to figure out what should belong in that file.

With those two configuration files in place, I used Infection's `--filter=path/to/
code/to/test` CLI option to tell it what code we are looking at. So what were the results of
running it?

```
```
1. php infection.phar --filter=src/Controller/Component/StandingsComponent.php
2.
3. Running initial test suite...
4.
5. PHPUnit version: 8.5.15
6.
7.      23 [============================] 8 secs
8.
9. Generate mutants...
10.
11. Processing source code files: 1/1
12. .: killed, M: escaped, U: uncovered, E: fatal error, T: timed out, S:
   skipped
13.
14. UUUUUUUT................M................................MMM   (  50 / 302)
15. MMMMMMMMMMMMM.............MMM..............M.............   ( 100 / 302)
16. M......MM........................TTTTTTTTTTTT..........   ( 150 / 302)
17. MMMMMMMMMMMM..M...MMMMMMMMMMMMMM.MMM..MMMMMM..   ( 200 / 302)
18. MMMMMMM...MMMMMM...MMMMMMM...MMM.............   ( 250 / 302)
19. MMMMMM.MMMMMMM.....MMM.........MMMMMMMMMM......   ( 300 / 302)
20. ..M                                        ( 302 / 302)
21.
22. 302 mutations were generated:
23.      39 mutants were killed
24.       6 mutants were not covered by tests
25.      255 covered mutants were not detected
26.       0 errors were encountered
27.       2 time outs were encountered
28.       0 mutants required more time than configured
29.
30. Metrics:
31.        Mutation Score Indicator (MSI): 13%
32.        Mutation Code Coverage: 98%
33.        Covered Code MSI: 13%
34.
35. Please note that some mutants will inevitably be harmless (i.e. false
   positives).
36.
37. Time: 4m 33s. Memory: 0.03GB
```
```