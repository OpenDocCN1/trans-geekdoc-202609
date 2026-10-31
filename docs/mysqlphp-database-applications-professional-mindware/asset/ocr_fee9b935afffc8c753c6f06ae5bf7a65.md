```
{
    // code for editing database
} elseif ($submit =="update")
{
    //code for updating records
}elseif ($submit == "delete")
{
    //code for deleting records
} else
{
    echo "I have no idea what I should be doing.";
}
```

![](bbox=[0.18, 0.36, 0.26, 0.44])

“elseif” is not that same as “else if”. If you have that space between the words, you will not get an error, but you may get some weird behavior.

# Alternative if... structures

There are a couple of different ways to write if statements. The first simply substitutes a colon for the opening curly brace and the word endif with a semicolon for the closing curly brace.

![](bbox=[0.18, 0.58, 0.26, 0.66])

This syntax is deprecated. You're better off not using it.

```
if ($a==1):
    echo "I knew a was equal to one.";
elseif ($a>1):
    echo "a is bigger than I thought.";
else:
    echo "a is a little number.";
endif;
```

The other alternative if structure we have is what's known as a trinary operator. It's essentially a shortened form of an if ... else statement and we'll use it in this