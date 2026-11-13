If you don't specify an index value, the value will be tacked onto the end of the array. The following line would assign “retriever” to $dogs[2].

```
$dogs[] = "retriever";
```

![](bbox=[0.08, 0.2, 0.75, 0.265])

Like many programming languages, PHP makes use of associative arrays. If you are new to the concept, elements in associative arrays have keys that reference individual elements. (In fact, all array values have keys. The difference with an associative array is that the keys are meaningful and can be strings as well as integers, whereas in a simple list array, they represent only the position of the value in the array.) Keys are particularly important when you're dealing with databases. When you fetch rows from your database query you will usually refer to the elements by their keys.

You can assign an associative array by using keys. Here, first_name, last_name, and email are the keys:

```
$person = array (
  "first_name" => "Jay".
  "last_name" => "Greenspan".
  "email" => "jgreen_1@yahoo.com"
);
```

If you wanted to add to this array, you could assign another value. Notice that the next line would add an integer to the array, so this array would then contain four values - three strings and one integer:

```
$person['age'] = 32;
```

Typically, if you wanted to access both the keys and the values in an associative array, you would use the list()=each() construct or the foreach() loop. Here are some examples:

```
while (list($key, $value) = each($person))
{
  echo "<b>key:</b> $key, <b>value:</b> = $value <br>\n";
}
```