# Part II: Learning the Language

Finally, you reach the end of the main...while loop. As you'd expect, the loop ends once the pigeon coordinates match the home coordinates:

```
} while ($pigeonX != $homeX // $pigeonY != $homeY)
```

In addition, the script used various CSS styles (embedded within the head element of the page) to improve the appearance of the maps.

# Mixing Decisions and Looping with HTML

In Chapter 2, you learned that you can embed PHP within HTML Web pages and, indeed, most of the examples in this book use this technique to wrap an XHTML page header and footer around the PHP code.

You also learned that you can switch between displaying HTML markup and exporting PHP code by using the <php ... ?> tags. This feature really comes into its owns with decisions and looping, because you can use PHP to control which sections of a Web page are displayed (and how they're displayed).

Here's a simple example:

```
<!DOCTYPE html ////W3//DTD XHTML 1.0 Strict//EN"
n"http://www.w3.org/TR/html/DTD/xhtml-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<Head>
  <title>Fibonacci sequence</title>
  <link rel="stylesheet" type="text/css" href="common.css" />
  <style type="text/css">
    th { text-align: left; background-color: #999; }
    td { padding: 0.4em; }
    tr.alt td { background: #ddd; }
  </style>
</Head>
<body>
  <h2>Fibonacci sequence</h2>
  <table cellspacing="0" style="width: 20em; border: 1px #666;">
    <tr>
      <th>Sequence #</th>
      <th>Value</th>
    </tr>
    <tr>
      <td>F<sub>0</sub>/</td>
      <td>0/</td>
    </tr>
    <tr class="alt">
      <td>F<sub>1</sub>/</td>
      <td>1/</td>
    </tr>
  </table>
</body></html>
```