# 4. LINTING AND FORMATTING YOUR CODE

How about saving us from remembering to order our imports?

```
$services->set(OrderedImportsFixer::class);
```

```
1. src/Model/Table\GamesTable.php
2.  ----------- begin diff -----------
3. --- Original
4. +++ New
5. @@ -6,8 +6,8 @@
6.  
7. use Cake\ORM\Association\BelongsTo;
8. use Cake\ORM\Locator\TableLocator;
9. +use Cake\ORM\Query;
10. use Cake\ORM\Table;
11. -use Cake\ORM\Query;
12.  
13. /**
14.  * Games Model
15. ----------- end diff -----------
```

+   18.  
19. Applied checkers:
20.  
21. * PhpCsFixer\Fixer\Import\OrderedImportsFixer

I want all my PHPUnit tests to use an annotation to indicate a method is a test case instead of prepending test:

```
$services->set(PhpUnitTestAnnotationFixer::class)
    ->call('configure', [[
        'style' => 'annotation'
    ]]);
```