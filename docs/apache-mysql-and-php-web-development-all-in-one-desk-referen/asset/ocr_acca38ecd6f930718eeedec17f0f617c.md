# # Looping for a reason: for loops

The `for` statement is another way to create a loop. With the `for` statement, you specify three things upfront:

+   - The initial setup
+   - The conditions under which the loop will continue to run
+   - What to do at the end of each iteration

Before I explain each of these bullet items, take a look at the following example:

```
for ($i=0; $i<10; $i++) {
    print "$i\n";
}
```

This `for` loop counts from 0 to 9, inclusively, and prints each number. Here's the output:

```
0
1
2
3
4
5
6
7
8
9
```

The key to the `for` loop is the junk — er, I mean `expressions` — inside parentheses in the first line. The three items inside those parentheses are each separated by commas; these correspond to the bullet items I mentioned earlier. The first item in this parentheses is this:

```
$i=0
```

This creates a counter variable called `$i` that you can use inside the loop — much like the default variable in a `foreach` loop — and initializes it to 0. The next item is this:

```
$i<10
```