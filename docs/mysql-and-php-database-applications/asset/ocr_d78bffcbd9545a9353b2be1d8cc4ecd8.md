# Chapter 7: Writing Organized and Readable Code

# Function basics

We'll start writing a simple function that writes out the start of an HTML table.

```
function start_table() {
    echo "<table> border=1\n";
}
```

To call this function within our PHP page, we would access it just like a built-in PHP function:

```
start_table();
```

That's easy enough. But what if we want the border to vary in given situations? We could make the border a variable, and then in the function call specify the value for border.

```
function start_table($border) {
    echo "<table> border=$border\n";
}
```

```
start_table(1);
```

Now that most of the time we want the border to be 1, but would like to change the border within the function call. The following would do the trick:

```
function start_table($border) {
    echo "<table> border=$border\n";
}
```

Here $border has been given a default value of 1. But we can overwrite that value by specifying a different value when calling the function. For example, if we were to call the function with the following command, the table would have a border of 2:

```
start_table(2);
```

Once again, 1 is the default value, so if this function is called with the following code, the table border will be 1:

```
start_table();
```