```
```php
echo "</ul>";

foreach ( $files as $file ) {
    if ( substr( $file, -1 ) == "/" ) traverseDir( "$dir/" . substr( $file,
0, -1 ) );
}

closedir( $Handle );
}

traverseDir( $dirPath );

?>
</body>
</html>
```
```

![](bbox=[0.195, 0.365, 0.895, 0.79])

# Figure 11-3