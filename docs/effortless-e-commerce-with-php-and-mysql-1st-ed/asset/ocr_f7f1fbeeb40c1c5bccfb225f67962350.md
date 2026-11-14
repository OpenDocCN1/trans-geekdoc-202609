+   3. Create the while loop and check the $header value:

```
while ($row = mysqli_fetch_array($r, MYSQLI_ASSOC)) {
if (!$header) { ?>
```

The loop will be executed once for each returned row. If you look at the query results shown in Figure 8.5, you’ll see that the general category information is included in each returned row. This information will be used to create the header only for the first record fetched. To test for that situation, a condi- tional sees if $header is still false. In that case, a big block of HTML and PHP will be executed. Because that block is mostly HTML, it’s easier to just leave the PHP code as the result of this condition, which is perfectly valid.

+   4. Add the header box:

```
<!-- box begin -->
<div class="box alt"><div class="left-top-corner"><div class="
"right-top-corner"><div class="border-top"></div></div></div></div>
<div class="border-left"><div class="border-right">
<div class="inner">
<h2><?php echo $Category; ?><h2>
<div class="img-box">
<p><img alt=""<?php echo $Category; ?>" src="/products/< ?php
echo $row['g_image']; ?>" /></p>
</div>
</div></div><div class="left-bot-corner"><div class="
"right-bot-corner"><div class="border-bot"></div></div></div></div>
<!-- box end --><p> <br clear="all" /></p>
```

This box will be at the top of the page, displaying the category’s name,
image, and description. The $Category variable, used as a caption, is
defined in the browse.php page; the other two values come from the
returned row.

+   5. Begin the next box and complete the $header if:

```
<!-- box begin -->
<div class="box"><div class="left-top-corner"><div class="
"right-top-corner"><div class="border-top"></div></div></div></div>
<div class="border-left"><div class="border-right"><div class="
"inner">
<?php
    $header = true;
} // End of $header IF.
```

![](bbox=[0.715, 0.17, 0.805, 0.205])

Instead of fetching the general category information with each
specific product, you could run two queries: one for the general
category info and another for all the products in that category.