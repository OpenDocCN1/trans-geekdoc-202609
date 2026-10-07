Code, but in the abstract sense.

```
// This makes perfect sense
$array = array('James', 'Mary', 'John');
print $array[0];
```

// Output: 'James'

This makes sense precisely because we know that's arrays work. We know that getting access to an element of the array requires us to put a number inside the square brackets. Since we also know that PHP arrays are zero-indexed, to access the first element of that array, we need to use an index value of Ø.

How do we know? There's nothing in that last code block that explicitly tells you how to get a handle on the 'James' element I'd wager if I give you that array and asked you to print 'Mary' to the screen, there's very likelihood that the line of code that you would use read very much like, if not exactly the same as print $array[1]; even though Mary is clearly the second name listed in the array.

The reason that you would do so is the very reason before us. It is exactly both you and I already know how numerically indexed arrays work in PHP. Given the fact that it's one of the first things we both learnt before the language, both understand the attributes and characteristics, the essential behaviours of simple arrays like this.

Given an infinite number of parallel universes, at least one of planes of existence will include a version of PHP that has, built into the core language itself, the perfect definition of a Person data type. In that universe, no developer ever needs to write their own Person class because the language already provides the ideal solution to use in every application that they create. In another of those parallel universes, Reece's Pieces are all free. I'd like to think that there was a third universe in which the perfect Person data type existed and everyone was with a free Reese's Pieces.

In our universe, no such data type currently exists and we generally still have to pay for chocolatey goodness. Now you could, brush off your K skills (or use Zephyr) and create a Person class as a PHP extension, presumably for a particular and very specific project. That would generally be madness though – think of the maintenance overhead!

The thing that normal, sane developers do is to create a Person class in regular PHP code and subsequently instantiate Person objects from that blueprint. By setting