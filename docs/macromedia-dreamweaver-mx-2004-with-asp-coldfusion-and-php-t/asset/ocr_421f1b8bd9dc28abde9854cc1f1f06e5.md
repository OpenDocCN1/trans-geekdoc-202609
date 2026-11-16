Now that you understand how the code works, you probably can already see what the problem is: each time the code loops, it prints a block of text wrapped by an `<p></p>` tag pairing. And `<p>` tags are block-level HTML elements that output with extra space. In other words, you need to replace the `<p>` tags with a `<br />` tag. You'll add it momentarily.

Thus all three server models (ASP, ColdFusion, and PHP) are not quite looping what we want, and that is why the display on the page is not right. In all cases, all we need to do is modify the code being looped over, so that there are no paragraph tags inside the loop, and so that there is a line break after each link. This obviously is an easy solution—but it is only easy if you look at the code and take a moment to understand what's going on.

The solution varies somewhat by server model.

# 10) All server models: Find the closing `</a>` tag inside the loop, and immediately after it, insert a `<br />` tag.

This line break fixes the display problem from before for ASP and PHP. ColdFusion users need to complete one more step.

![](bbox=[0.27, 0.445, 0.94, 0.51])

# 11) PHP users only: Move the opening `<p>` tag so that it is before the opening `<?php do` line; likewise, move the closing `</p>` tag so that it is outside the closing `<?php } while` line (but before the closing `</td>`.

This takes care of the nesting problem. Now, effectively all elements output by the loop are in a single paragraph, separated with line breaks (`<br />`).

The final PHP block should look as follows:

```
<p><?php do { ?>
<a href="profiles_detail.php?countryID=<?php echo $row_rs_tourNames['countryID']; ?>"
><?php echo $row_rs_tourNames['countryName']; ?></a><br />
<?php } while ($row_rs_tourNames = mysql_fetch_assoc($rs_tourNames));
?></p></td>
```

![](bbox=[0.27, 0.795, 0.94, 0.86])