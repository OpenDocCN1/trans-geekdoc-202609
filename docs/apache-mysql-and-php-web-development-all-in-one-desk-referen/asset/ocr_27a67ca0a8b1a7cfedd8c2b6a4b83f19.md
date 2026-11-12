```
$longname = "Abraham Honest Abe Lincoln";
($fname, $mname1, $mname2, $lname) = split( ' ',$longname);
print "$fname\n";
print "$mname1\n";
print "$mname2\n";
print "$lname\n";
```

The split function returns a list. Instead of storing the list in an array, however, I store the individual elements in four separate scalar variables. If you want to extract only certain portions, put parentheses around the function and then put brackets after the function, specifying the elements. In the following example, I extract the first and last elements:

```
($firstname, $lastname) = (split( ' ',$longname))[0,-1];
```

If $longname still contains Abraham Honest Abe Lincoln, the split array returns a list of four strings. Then the [0,-1] indexes return a list consisting of the first element (the 0 index) and the last element (the -1 index). Thus, $firstname contains Abraham, and $lastname contains Lincoln.

# Associating Data with Hashes

If you want to store data in a list but want to be able to access the data via a name instead of an index, you can use a hash. A hash is the Perl name for what is commonly known as an associative array. An associative array is an array in which you store indexed information so that the index can be any data, not just a whole number or 0. (The reason for the strange name hash is that Perl uses a special way of organizing the data; this special way is called a hash by computer scientists. Why the computer scientists call it a hash, I have no idea.)

Here's an example to help you understand what a hash is. Suppose you have a list of names, and you want to be able to look up the first name, based on the last name. You can store this data like so:

```
%names = (
  "Lincoln" => "Abraham",
  "Washington" => "George",
  "Jefferson" => "Thomas"
);
```

This code creates a hash in which the element indexed by Lincoln contains the value Abraham; the element indexed by Washington contains the value George; and the value indexed by Jefferson contains the value Thomas. Here's a line of code that outputs the value indexed by Jefferson:

```
print $names{'Jefferson'};
```