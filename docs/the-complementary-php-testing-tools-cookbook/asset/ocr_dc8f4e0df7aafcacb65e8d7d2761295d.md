```
1. 3) tests/TestCase/Model/Table/GamesTableTest.php
2.
3. ```diff begin diff```
4. --- Original
5. +++ New
6. @@ -15,7 +15,10 @@
7. ```
8. ```class GamesTableTest extends TestCase
9. ```{
10. - ```public function testGetWeeklyResult(): void
11. + ```/**
12. + ```* @test
13. + ```*/
14. + ```public function getWeeklyResult(): void
15. + ```{
16. ```/** @var GamesTable $table */
17. ```$table = (new TableLocator())->get('Games');
18. ```
19. ```diff end diff```
20.
21. Applied checkers:
22.
23. * PhpCsFixer\Fixer\PhpUnit\PhpUnitTestAnnotationFixer
```

# When

In my experience, there are three places to use code linters and formatters:

# During Development

The most common practice if it is not mandatory for a particular project is to have the developers use the linting and formatting tools during their work and hopefully before committing and pushing their code for review or merging.

I have done this on projects where these tools were not mandatory.

# Before Version Control Usage

If you are using a version control system that has the concept of a “pre-commit hook” I highly recommend reading the documentation for your VCS on how to use them and set one up.

This way, if you have forgotten to run the linter it will be done before your VCS tooling pushes your code to the repository.