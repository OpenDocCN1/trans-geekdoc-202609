# Seeing the need for references

Suppose you have a set of classes and each class has an associated list of students. How can you store this in Perl? In versions of Perl prior to 5.0, you really couldn't store it at all, at least not without a lot of data acrobatics. The reason that hashes could contain only scalars. The various Perl manuals talk about ways you may work around this, and I won't go into them here, because you no longer need to work around the former shortcoming. Let me just say it was messy. Today, with version 5.0 and later, you still store only scalars inside lists and arrays; however, the difference is that a scalar now can refer to a list or hash. And so by adding a special type of scalar called a reference, the Perl designers quickly solved the problem of not being able to put lists and hashes inside other lists and hashes.

Now think about this: First, I will create an array that holds a list. Next, I will create a variable that refers to the array. The variable that refers to the array is called a reference, and I can access the members of the list by using the array or the reference.

Here's some sample code that does this:

```
@tunes = ('Yankee Doodle', 'Rhapsody in Blue',
              'Bohemian Rhapsody');

$myref = \@tunes;

print $myref->[0];
print "\n";
print $myref->[1];
print "\n";
print $myref->[2];
print "\n";
```

This code first creates an array called @tunes and stores a list in the array. This list contains the titles of three songs. Next, the code creates a reference to the @tunes array (by putting a backslash before the name @tunes). The code stores this reference inside the scalar variable called $myref. Now $myref contains a reference to the array. However, $myref is not itself an array; $myref is still a scalar in that it contains a single item, a reference.