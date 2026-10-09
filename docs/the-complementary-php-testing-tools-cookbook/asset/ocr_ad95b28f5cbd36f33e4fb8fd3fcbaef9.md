The first step is to create a PHPStan configuration file:

```
1. parameters:
2. bootstrapFiles:
3. - vendor/autoload.php
4. level: 7
5. paths:
6. - .
7. excludePaths:
8. analyse:
9. - vendor
```

How bad could it be?

```
[ERROR] Found 312 errors
```

Maybe that’s pretty bad. Now, chances are that if this was some kind of paid project instead of a hobbyist one I might not want to spend all that developer time fixing older problems. Instead, I want to make sure all new code I write can be analyzed by PHPStan but accept the current state of the codebase.

For this, PHPStan has the concept of “setting a baseline” Using the `--generate-baseline` switch from the command line, PHPStan generates a file that contains all the errors it finds.

Here’s what I saw when I ran that command:

```
./vendor/bin/phpstan --generate-baseline
```

```
Note: Using configuration file /Users/chartjes/ibl.dev/webreg/phpstan.neon.
64/64 [#################] 100%
```

```
[OK] Baseline generated with 312 errors
```