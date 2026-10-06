# Part II: Learning the Language

```
function fibonacci($ n ) {
  if ( $n == 0 ) || ( $n == 1 ) return $n;
  return fibonacci($n-2) + fibonacci($n-1);
}

for ($i=0; $i <= $iterations; $i++) {
  <tr<?php if ($i % 2 != 0 ) echo ' class="alt"' ?>>
    <td><?php echo $i; ?></td>
    <td><?php echo fibonacci( $i );?></td>
  </tr>
}
<?php
?>
</table>
</body>
</html>
```

Save the script as fibonacci_recursion.php in your document root folder and run it via your Web browser. You should see a page much like Figure 7-6. Notice that the sequence is identical to that produced by the script in Chapter 4.

![](bbox=[0.132, 0.458, 0.785, 0.875])

Figure 7-6

162