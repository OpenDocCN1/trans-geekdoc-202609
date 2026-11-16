# ## Associative Arrays in Smarty

You can approach associative arrays (hashes) in a very similar manner to how you approach linear arrays. Consider the following control code to supply the Smarty template:

```
```php
$arHash["Name"] = "Ed";
$arHash["Age"] = 27;
$arHash["Location"] = "London";
$objSmarty->assign("Writer", $arHash);
```
```

Again, the approach for assignment appears to be very similar. The following shows how you can now render the output in your template:

```
```
The author of this chapter is ({$Writer.Name}), ({$Writer.Age}) years of age,
currently residing in ({$Writer.Location}).
```
```

Notice the simple syntax of ({$X.Y}), where X is the name of the Smarty variable, and Y is the key from the hash that has been assigned to it. This yields the following output:

```
```
The author of this chapter is Ed, 27 years of age, currently residing in London.
```
```

# ## Conditionals in Smarty

What if you want to display content only if a certain condition is met? This would be of particular interest to you in displaying error messages. You would want to display the error only if an error has definitely occurred.

You assign variables in your controller as follows:

```
```php
$objSmarty->assign("isError", 1);
$objSmarty->assign("ErrorText", "You did not specify a search term.");
```
```

The following template logic can support this:

```
```
{if $isError == 1}
The following error occurred: {$ErrorText}
{/if}
```
```

As you can see, a conditional expression is very similar to what you would use in PHP to perform the test. This will render only the introductory text, and the error itself, if isError is set to 1:

```
```
The following error occurred: You did not specify a search term.
```
```

To prove this to yourself, change the assignment to isError in your controller to 0. The output is not rendered at all.

This is somewhat laborious, though. In native PHP templating, you would probably just check whether an error message has been defined. You can also do that in Smarty:

```
```
{if $ErrorText}
The following error occurred: {$ErrorText}
{/if}
```
```