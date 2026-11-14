```
<li><a href="recommendations.php" title="View Your Recommendations">Recommendations</a></li>
<li><a href="logout.php" title="Logout">Logout</a></li>
</ul>
<div class="title">
<h4>Content</h4>
</div>
<ul>
<li><a href="category.php?id=3" title="Common Attacks">Common Attacks</a></li>
<li><a href="category.php?id=5" title="Database Security">Database Security</a></li>
<li><a href="category.php?id=1" title="General Web Security">General Web Security</a></li>
<li><a href="category.php?id=4" title="JavaScript Security">JavaScript Security</a></li>
<li><a href="category.php?id=2" title="PHP Security">PHP Security</a></li>
<li><a href="pdfs.php" title="PDF Guides">PDF Guides</a></li>
</ul>
<!-- END SIDEBAR -->
</div>
<div class="footer">
<p><a href="site_map.php" title="Site Map">Site Map</a> | <a href="policies.php" title="Site Policies">Policies</a> &
bsp;&nbsp; &copy; Knowledge is Power | Design by <a href="http://www.spyka.net">spyka webmaster</a></p>
</div>
<!-- END PAGE -->
</div>
</body>
</html>
```

That's the footer code for a logged-in, non-administrative user. In the next series of steps, the code for the other two possible situations (a visitor who is not logged in and an administrator who is logged in) are changed.

+   3. Create a new file to be named footer.html and stored in the includes directory.