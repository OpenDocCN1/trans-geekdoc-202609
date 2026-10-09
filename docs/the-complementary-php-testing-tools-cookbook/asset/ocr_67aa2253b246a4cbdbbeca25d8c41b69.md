# **2. STATIC CODE ANALYSIS TOOLING**

Then, according to the instructions, I add a reference to this file in my phpslan.neon configuration file.

```
```
1. includes:
2.      - phpslan-baseline.neon
3.
4. parameters:
5.     bootstrapFiles:
6.      - vendor/autoload.php
7.      level: 7
8.      paths:
9.      - .
10.     excludePaths:
11.        analyse:
12.      - vendor
```
```

Having done this, I should not see any errors the next time I ask PHPStan to analyze my code:

```
```
Note: Using configuration file /Users/chartjes/ibl.dev/webreg/phpstan.neon.
64/64 [████████████████████████████] 100%

[OK] No errors
```
```

Now I can start refactoring or adding code to the project, and PHPStan will only report on errors it hasn’t already seen. This is a very handy tool for large legacy projects.