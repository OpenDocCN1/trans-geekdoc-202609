Note the print statement in the loadSingers() method. Having this here is just for demonstration purposes. Run the following code (you can add it to the bottom of the previous code, if you wish), and you'll see that the print statement does not appear on the screen:

```
```php
<?php
$objNightClub = new NightClub('The Sands');
print "Welcome to " . $objNightClub->name . ".<br>\n";
?>
```
```

Now try it again, this time doing something with the $singers collection:

```
```php
<?php
$objNightClub = new NightClub('The Sands');
print "Welcome to " . $objNightClub->name . ".<br>\n";
print "We have " . $objNightClub->singers->length() . " singers " .
       "for your listening pleasure this evening.";
?>
```
```

Running this should result in the following output:

```
Welcome to The Sands.
(We're loading the singers!)
We have 3 singers for your listening pleasure this evening.
```

As you can see, this makes using the singers collection extremely easy. If you were to create the NightClub class, you could hand that class off to a more junior member of your software development team, who could then use that class to display the screen output shown in the example without any knowledge of how or when that collection was loaded. In addition, you ensure that the application isn't taking up any more system resources than are absolutely necessary.

The next section returns to the registrar's office example and shows how to put all this to good use in a real-world application.

# # Using the Collection Class

As already mentioned previously in this chapter, the registrar's office application involves a class called Student that contains a collection of Course objects. Both classes are fairly simple. The UML class diagram is shown in Figure 5-3.

![](bbox=[0.41, 0.74, 0.66, 0.82])

Figure 5-3: UML class diagram