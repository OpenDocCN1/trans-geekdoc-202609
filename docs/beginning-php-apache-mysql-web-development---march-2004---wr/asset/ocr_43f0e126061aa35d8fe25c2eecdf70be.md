+   Allow for registering, login, and order tracking. Some customers like to check the status of their orders.

A: We discussed login and user authentication in Chapter 11. You apply these principles here, and it is a matter of issuing a SELECT statement based on customer number and displaying the results in a simple table. The only change you could make is to add the ordermain table that shows order status such as “Shipped,” “Received,” and so for customers can tell where in the order fulfillment process their order lies.

# Chapter 15

+   Add code to admin.php to prevent unauthorized users from loading the page. Redirect back to index.php.

A: This block of code should be at the top of admin.php:

```
<?php
include "http.php";
session_start();
if ($_SESSION['access_lvl'] < 3) redirect('index.php');
?>
```

+   Create a regular expression that recognizes an e-mail address in a post and turns it into a link.

A: This is not the only answer but it gets the job done:
/[\w-]+\.[\w-]+\)*@@[\w-]+\.[\w-]+\+/

+   Add a bit of code to the pagination function to go to the first or last page. For example, if there are 14 pages, and the user is on page 8, and the range is 7, it should look like this:

```
<PREV] 1 [5] [6] [7] 8 [9] [10] [11] ... [14] NEXT >
```

A: Replace the appropriate lines of code with the following snippets:

```
if ($range > 1) {
  $pagelinks .= "<a class='pagenumlink' href='<?php echo $currpage-1; ?>'>$1</a>...";
} else {
  $pagelinks .= "&nbsp;&nbsp;";
}

if ($range < $numpages) {
  $pagelinks .= "..<a class='pagenumlink' href='<?php echo $currpage+1; ?>'>" . $page . "." . $numpages . "</a>...";
} else {
  $pagelinks .= "&nbsp;&nbsp;";
}
```