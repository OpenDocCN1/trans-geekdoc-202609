# Chapter 4

```
function calculate_differences($takings,$cost) {
$difference = $takings - $cost;
if($difference < 0) {
  $difference = substr($difference,1);
  $font_color = 'red';
  $profit_or_loss = "$.$difference.*m";
}elseif($difference > 0) {
  $font_color = 'green';
  $profit_or_loss = "$.$difference.*m";
}else{
  $font_color = 'blue';
  $profit_or_loss = "Broke even";
}
  return "<font color=$font_color">$profit_or_loss</font>";
}
```

This function will make easier for you. This will become clearer as we proceed through the rest of the example.

+   Save this file as movie_details.php.

# How It Works

The line that contains the subst is placed before the $profit_or_loss line because a loss will return a negative number, and no one says, "The movie made a loss of 10 million dollars." Instead we say, what happens when the movie timings are the same as the movie production costs? That's where the "else" comes into play. We covered it effortlessly.

The important thing to remember is that in PHP you can easily create new variables by performing actions on existing ones. Just because you don't hold the information in the database means you can't create it.

# Try It Out Displaying the New Information

Now you are going to alter the original master table to include the new data, and this will serve as your new "child" table.

+   Add the following code to movie_details.php:

```
/* Function to get the director's name from the people table */
function get_director() {
  global $movie_director;
  global $director;

  $query_d = SELECT people_fullname
  FROM people
  WHERE people_id=$movie_director;
  $results_d = mysql_query($query_d) or die($mysql_error());
  $row_d = mysql_fetch_array($results_d);
  extract($row_d);
n
```