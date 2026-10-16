```
new LinkData('http://php.net/', 'PHP')
);

echo json_encode($data);
?>
```

The JSON Server Endpoint (json.php)

On the client side, JavaScript code can then call the PHP script and process the data. When using a JavaScript library like the popular jQuery (http://jquery.com/), working with the JSON data can be quite easy (see Figure 11.6). The following code displays the information contained in the JSON string in the form of a bulleted list:

```
<script type="text/javascript" src="http://code.jquery.com/jquery-latest.js"></script>
<script type="text/javascript">
$(function() {
    $.getJSON("json.php", function(data) {
        $.each(data, function(key, value) {
            $("<a>").attr("href", value.url)
                .html(value.text)
                .wrap("<li>")
                .parent()
                .appendTo("ul");
        });
    });
});
</script>
...
<body>
    <ul></ul>
</body>
```

The JSON Client, Using jQuery (json.html)