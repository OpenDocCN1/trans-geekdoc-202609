```
}
}
// call the display_name function with a single argument ("Amandine")
display_name("Amandine");
echo "<br>";
// call the display_name function with two arguments ("Sarah" and "Smith")
display_name("Sarah", "Smith");
?>
```

This code defines a **display_name()** function that takes a mandatory parameter $firstname and an optional parameter $lastname with a default value of "Mercier". When the function is called, it checks whether the lastname is different from "Mercier". If so, it displays both the first and last names, otherwise it displays only the first name.

If you run this code, you will get the following result: