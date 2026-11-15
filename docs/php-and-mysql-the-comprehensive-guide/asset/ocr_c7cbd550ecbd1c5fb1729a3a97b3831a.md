If you want the date to be a little more colorful, create the countdown with images. You only need the numbers from 0 to 9 as images. It is best to name these intelligently—for example, _0.gif_ to _9.gif_—and then insert the corresponding image depending on the number. The following example shows the necessary changes in the countdown file.

```
if ($result > 0) {
    $days = str_split(floor($result / (60 * 60 * 24)));
    echo "Still ";
    for ($i = 0; $i < count($days); $i++) { echo
    "<img src="" . $days[$i] . ".gif" />";
    }
    echo "until " . date('m/d/Y', $date1);
} else {
    echo "Your date is not in the future!";
}
```

# Listing 9.23 The Countdown with Graphics (Excerpt from "countdown_images.php")

The calculation result is split into an array. A `for` loop then runs through the array and outputs the image with the corresponding number for each position (see Figure 9.17). The number comes from the array with the individual digits.

![](bbox=[0.14, 0.48, 0.69, 0.62])

# Figure 9.17 The Display with Graphics

> **Tip**
> 
> A countdown with continuous animation is a task for client-side technologies, like JavaScript. Why? With a server-side language such as PHP, each update of the countdown would require data to be transferred again. On the client side, however, the countdown can tick every second.

Another method to realize the countdown is again to use the `DateTime` object, with the `diff(DateTime, Absolute)` method. First you have to convert both date values into `DateTime` objects, then you can use the first one as a parameter of `diff()` in the second object.