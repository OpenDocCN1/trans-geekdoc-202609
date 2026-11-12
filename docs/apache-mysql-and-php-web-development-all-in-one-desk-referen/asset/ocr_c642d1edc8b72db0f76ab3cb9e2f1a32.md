Make sure that you understand why it works. The code @food[0,3,4] returns a list of three elements. The left half of the equal sign is also a list of three elements, and Perl copies the elements one by one from the right side to the left side.

Now look at this code:

```
@pres = ("Washington", "Adams", "Jefferson");
($first, $second, $third) = @pres;
```

The first line creates a list and puts it in the @pres array; no big deal. The second line copies the individual elements from the list stored in @pres to the list on the left. Thus, the first element, Washington, ends up in the $first variable; the second, Adams, ends up in the $second variable; and the third, Jefferson, ends up in the $third variable.

If the list on the right has more elements than the list on the left, only as many elements as necessary are copied. Take a look at this slightly modified code:

```
@pres = ("Washington", "Adams", "Jefferson");
($tallguy, $funguy) = @pres;
```

The list on the right side of the equal sign has more elements than the list on the left, but that's okay. After the second line of code is run, $tallguy contains the string Washington, and $funguy contains the string Adams. The third string, Jefferson, isn't used.

When working with arrays and copying the elements elsewhere, remember that you're just copying the elements. For example, when you do something like this, the original array, @pres, remains unchanged:

```
($tallguy, $funguy) = @pres;
```

Thus, if @pres contains Washington, Adams, and Jefferson, respectively, then after this code runs, $tallguy will contain Washington, and $pres[0] will still contain Washington as well.

If you explore functions later on (or if you already have), you'll be interested in knowing that when you call a function that returns a list, the list hangs around in limbo until you store it in a variable. However, you can also yank out only certain elements of the list and store them in individual variables using the technique I'm describing in the present section. The following code shows how to do this: