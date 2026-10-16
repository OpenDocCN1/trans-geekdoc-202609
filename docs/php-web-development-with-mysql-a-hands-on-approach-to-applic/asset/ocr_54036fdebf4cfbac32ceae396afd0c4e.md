# 2. WRITING YOUR FIRST PHP SCRIPT

# Comments

When we write code, we do it for a reason. Frequently we need to share why something works the way it does. Like many modern programming languages, PHP allows you to create single and multi-line comments, as shown in Listing 2.2.

# Listing 2.2.

```
```php
<?php
//Single line comment

# Also a single line comment

phpinfo(); //comment after code

/*
Multi line block, you can add as many
lines as you want, but don't write a book
*/
```
```

When we comment our code, our comments should reflect why our code exists instead of how our code works. The how is most often explained by the actual code.

Here are a few examples of bad and good commenting.

# *Bad Commenting Example*

In Listing 2.3, the comment repeats how the code works instead of explaining why it's done that way. If our regular expression changes, we must remember to update the comment—a step that's often overlooked. If comments don't match the code, future developers may get confused.

# Listing 2.3.

```
```php
<?php
/*
We are formatting phone numbers by stripping all characters
then putting parens around the first 3 numbers adding a
space then grouping the next 3 numbers adding a dash
then the last 4 numbers
*/
function formatPhoneNumber($phone_string)
{
```
```