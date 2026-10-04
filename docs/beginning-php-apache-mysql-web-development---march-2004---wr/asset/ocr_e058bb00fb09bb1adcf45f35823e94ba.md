# Creating PHP Pages

![](bbox=[0.151, 0.087, 0.927, 0.555])

Figure 2-14

# How It Works

This has been a rudimentary look at how to use functions, but you can see how they work. The moviel.php page gave users the option of looking at five or ten of our favorite movies. Whichever they choose sets the value for $movenium.

In addition, moviesite.php accomplishes several other tasks:

+   - It sets up the functions listmovies_1() and listmovies_2(), which prints a portion of the total top 10 list.
- We also added this line:

```
if (isset(\$_REQUEST['favmovie'])) {
```

71