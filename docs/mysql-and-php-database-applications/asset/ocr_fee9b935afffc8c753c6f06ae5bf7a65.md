```
// code for editing database
} elseif ($submit == "update") 
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

"else' is not as same as 'else'. If you have space between the words, you will not get an error, but you may get some weird behavior.

# Alternative if... structures

There are a couple of different ways to write statements. The first simply substitutes a colon for the opening curly brace and the word endif with a semicolon for the closing curly brace.

This syntax is depreciated. You're better off not using it.

```
if ($a==1):
    echo "I knew a was equal to one.";
elif ($a>1):
    echo "a is a bigger than I thought.";
else:
    echo "a is a little number."
endif;
```

The other alternative if structure we have is what known as a ternary operator. It's essentially a shortened form of an if ... else statement and we'll use it in this