# Chapter 15

Next, we grab the page variable, if it is set. If not, we set $page to 1.

Our next step is to determine whether the <PREV link be activated or not. Obviously, if we are on page 1, there is no previous page. Otherwise, the previous page is the current page number minus 1:

```
if($page == 1) {
  $pagelinks .= '<span class="pageprev&lt; PREV</span>&gt; ';
} else {
  $page = $page - 1;
  $pagelinks .= '<a class="pageprevlink" href="$currpage&lt;..."&gt;$page&gt;</a>';
}
```

The next bit of code does a bit of math. We are defining a few things in this code block. The number of pages is determined by dividing the total number of rows returned by our SELECT FOUND_ROWS() query($numrows) by the number of pages per page ($limit) and rounding up.

Next, the range is grabbed from the global $admin['pagerange']$ and stored in $range. If it's not available, $range defaults to 7. This value determines how many pages are accessible via a link at the bottom of the page. For example, if the range is 5, there are 13 pages, and we are currently viewing page 6, we will have access to pages 4, 5, 6, 7, and 8:

< PREV [4] [5] [6] [7] [8] .. NEXT

"... tells you which pages are in direction (before or after).

```
$numpages = ceil($numrows / $limit);
$range = $admin['pagerange']['value'];
if ($range == "" or $range == 0) $range = 7;
```

The next few lines determine range of pages to show you. In the example, if the $range is 5, you are viewing page 2 of 13 pages, the code should be smart enough to allow access to pages 1 through5:

< PREV [1] [2] [3] [4] [5] .. NEXT

As you can see, if you are viewing page 2, you can get to pages 1 through 7, and there are more pages past 5. The logic of determines which pages are accessible is the following:

```
$range = max(1, $page-$($range-1)/2);
$rrange = min($numpages, $page+($range-1)/2);
if (($rrange - $range) < ($page - 1)) {
  if ($range == 1) {
    $rrange = min($range + ($range-1), $numpages);
  } else {
    $range = max($range - ($range-1), 0);
  }
}
```

Next, the part of code renders the space between pages PREV and NEXT. If the lower range is higher than 1, put "..." to show that by clicking <PREV. Then, use the $range and

564