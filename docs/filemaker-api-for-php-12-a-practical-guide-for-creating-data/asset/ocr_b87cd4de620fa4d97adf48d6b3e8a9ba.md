```
</head>
<body>
<?php
foreach($records as $record) {

    $id = $record->getRecordID();
    echo '<strong>' . $record->getField('Name') . '</strong><br>';
    echo '<button type="button" onclick="showDetail(\'.$id.\')">Show Detail</button>';
    echo '<div id="' . $id . '"></div>';
    echo '<hr>';
}
?>
</body>
</html>
```

Now we've displayed the data on the web page and dynamically named each of the DIV tags we can talk about the showDetail JavaScript function that updates the page. As with all JavaScript code, it goes in the HEAD section of the web page, defined in the tag <script type="text/javascript">. I named the custom function showDetail and defined one variable "id" that receives the RecordId from the button. The id can be used anywhere in the function. I created the XMLHttpRequest variable and left it empty to define it based on which browser the client is using. In general, all modern browsers support the XMLHttpRequest request. The exception is IE5 and IE6, which use an ActiveXObject. This code never changes.

```
<script type="text/javascript">
function showDetail(id) {
    var xmlhttp;
    if (window.IE7 {
        // code for Firefox, Chrome, Opera, Safari
        xmlhttp=new XMLHttpRequest();
    } else {
        // code for IE5, IE6
        xmlhttp=new ActiveXObject("Microsoft.XMLHTTP\n    }
}
```

The next section of code essentially waits for a response from the server with the data from the show_detail.php page. While this is running the onchange event triggered every time the readyState changes. The readyState property holds the status of the XMLHttpRequest. In this case, we are trapping for readyState=4 (finished and response is ready) and the page status=200 (OK). The readyState has 5 possible outcomes:

+   0: not initialized
1: server connection established
2: request received
3: processing request
4: request finished and response is ready

Obviously, we're only interested in 4. The page status has two possible responses: 200 OK, and 404 Not Found. We're only interested in 200.

```
xmlhttp.onchange=function() {
    if (xmlhttp.readyState==4 && xmlhttp.status==200) {
}
```

Once we get a positive response back from the server we can utilize the callback function to place the RecordID value (id) to the xmlhttp.responseText text function. This is the actual function that will replace the content of the DIV