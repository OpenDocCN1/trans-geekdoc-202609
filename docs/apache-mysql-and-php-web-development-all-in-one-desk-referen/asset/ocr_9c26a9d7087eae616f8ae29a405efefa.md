In the first iteration, the item variable gets the value 5. In the next iteration, the item variable gets the value 10, then 25, and then 500. Here's the output:

```
5
10
25
500
```

If you want to count a range of numbers — such as 0, 1, 2, 3, up to, for example, 100 — use a regular for loop. But if you want to count a particular set of numbers — such as 5, 10, 25, and 500 — the foreach loop is better, as demonstrated in the preceding example.

Tcl also has an interesting feature that enables you to move through a list but store the list in pairs. Take a look at this example:

```
foreach {item1 item2} {5 10 25 500} {
    puts "item1=$item1 item2=$item2"
}
```

The first line is just like the previous example, but this time, I added two counter variables, item1 and item2. (Don't use a comma between any of these variables, or you'll get strange errors that are almost impossible to figure out. I speak — ahem — from experience.)

In the first iteration of this loop, item1 gets 5, and item2 gets 10; these are the first two items in the loop. In the next iteration, item1 gets 25, and item2 gets 500; these are the next two items in the list. In other words, you move through the list in groups of two rather than one. Here's the output:

```
item1=5 item2=10
item1=25 item2=500
```

But notice I have an even number of items in the list, and that works out nice and neat. What if you try to fake out the loop and put an odd number of items in the list? What will happen? Here's an example:

```
foreach {item1 item2} {5 10 25 500 600} {
    puts "item1=$item1 item2=$item2"
}
```

In the first iteration, you have 5 and 10 in item1 and item2, respectively. Then you get 25 and 500. But what about the third iteration? The loop has only one number left, 600. Here's the output so you can see what happens:

```
item1=5 item2=10
item1=25 item2=500
item1=600 item2=
```