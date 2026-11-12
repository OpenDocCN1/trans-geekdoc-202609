```
<a href="?php echo $baseUrl; ?>/products/">Products</a><br />
<a href="?php echo $baseUrl; ?>/products/books/fiction/">Fiction</a><br />
</body>
</html>
```

Simplifying that a little, the actual work of menu construction happens here:

```
while ($item = $crumbs->fetch()) {
    if ($item->isRoot()) {
        echo "<a href="" . $baseUrl . $item->location() . "">" .
            $item->name() . "</a>";
    } else {
        echo " > <a href="" . $baseUrl . $item->location() . "">" .
            $item->name() . "</a>";
    }
}
```

The iterator method fetch is used to read through the list of menu items, returning FALSE when it reaches the end (see Volume II, Chapter 7 for more information about iterators). Each $item returned is an instance of the MenuItem class, which we'll look at shortly. In brief, these are the methods used above to build the links for the menu:

+   isRoot If this is a root of a menu tree, returns TRUE.
+   location Returns the location field from the menu table.
+   name Returns the name field from the menu table.

There's also the method description, which we could use for a popup description (e.g. with the link's title attribute).

Figure 9.8 shows how the resulting links appear in a browser.