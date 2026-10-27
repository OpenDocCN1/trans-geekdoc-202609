projects, this can create a hodgepodge of varying code that confuses other developers and makes code difficult to maintain.

Many developers are still resistant to implementing a coding standard, even given this potential for conflict. Their reasons are many: good code does not result from a coding standard, or the fact that a coding standard means they have to spend precious time reformatting their code instead of making it work properly.

However, coding standards have two important applications that make them necessary in large teams: first, they make code maintenance considerably easier by codifying and unifying the way code is written and developed. Second, they can help prevent inadvertent bugs by their implementation.

Most developers will agree that it is easier to write code than it is to read it. Given the difficulty in reading code, developing without a coding standard makes this even more difficult, because in addition to reading code that is unfamiliar the developer must also adapt to a coding style that is unfamiliar.

A standardized coding style, regardless of whether it is each developer’s personal preference, establishes a familiar baseline that ensures that developers will be able to more easily read and understand source code not written by them. This further ensures that maintainability is made easier.

Style guides, when well written, can also help prevent the introduction of bugs into your code. For example, requiring brackets around if-else statements, even if they are a single line, helps prevent the introduction of bugs when a developer goes to add a second behavior in that if-else loop. Without such a coding standard, it is possible that the developer might forget and introduce something that causes the original item to be executed regardless; this condition would obviously introduce a significant bug.

Joel Spolsky once wrote an article called “Making Wrong Code Look Wrong” in which he argues that developers can designate between unsafe and safe (unclean and clean) variables in code. This helps prevent security problems, and might also help prevent bugs in code.

Another strategy suggested by some is the reversal of the order in which items are compared in if-else statements, generating a fatal error in the event that a developer uses the wrong symbol. For example:

```
```php
if($var = count($array)) { ... }
```
```