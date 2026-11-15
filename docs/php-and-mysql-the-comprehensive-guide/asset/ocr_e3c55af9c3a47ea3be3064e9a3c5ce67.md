Everything else is then taken care of by the writeHTML(HTML) method. It takes a string with HTML code as the central parameter. This can even contain CSS and complex elements such as tables.

Listing 31.5 and Figure 31.5 show an overview of some possibilities.

```
$html2pdf = new HTML2Pdf();
$html2pdf->writeHTML('<
<style type="text/css">
table {
    border-collapse: collapse;
}
th, td {
    width: 200px;
    border: 1px solid gray;
    padding: 5px;
}
</style>
<h1>Heading</h1>
<p>An output in a paragraph with a little text and even more text. A
output in a paragraph with a little text and <strong>even</strong> more text. A
output in a paragraph with a little text and even more text. An
output in a paragraph with a little text and even more text. </p>
<hr/>
<h2 style="color: red">Heading 2</h2>
<p>An output in a paragraph with a little text and even more text. One
output in a paragraph with a little text and <strong>even</strong> more text.
more text. An output in a paragraph with a little text and even more text. An
output in a paragraph with a little text and even more text. </p>
<table>
<tr>
<th>cell heading1</th>
<th>cell heading2</th>
</tr>
<tr>
<td>Cell 1</td>
<td>Cell 2</td>
</tr>
</table>');
$html2pdf->output();
```

# **Listing 31.5 HTML Output with HTML2PDF ("html2pdf.php")**