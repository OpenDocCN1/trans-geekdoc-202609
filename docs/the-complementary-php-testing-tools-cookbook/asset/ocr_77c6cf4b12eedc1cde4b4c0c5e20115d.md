# How

See, now the tool does all the things I either did not know were part of the PSR-12 standard, or things I keep forgetting to do myself.

Hrm. I notice my files don't all have a `declare(strict_types=1);` statement. Could we add that as a rule?

Looking in the documentation I see that there is a rule for it:

```
$services->set(DeclareStrictTypesFixer::class);
```

I add this to my `ecs.php` file, and away it goes.

```
1.
2. All sorts of output snipped...
3.
4. 31) tests/bootstrap.php
5.
6.  ----------- begin diff -----------
7. --- Original
8. +++ New
9. @@ -1,4 +1,6 @@
10.  \<?php
11. +
12. +declare(strict_types=1);
13.  /**
14.  * Test runner bootstrap.
15.  *
16.  ----------- end diff -----------
17.
18.
19. Applied checkers:
20.
21.  \* PhpCsFixer\Fixer\PhpTag\BlankLineAfterOpeningTagFixer
22.  \* PhpCsFixer\Fixer\Strict\DeclareStrictTypesFixer
23.
24.
25.
26. [WARNING] 31 errors are fixable! Just add "--fix" to console command and rerun to apply.
```

Great; it's a quick fix, and I don't have to worry about that any more.

Now I check to make sure I haven't broken anything... and my tests show some errors! Both in one file that did not have strict typing in it. Two changes later (casting variables to expected values), and my test suite is passing again! What else can it do?