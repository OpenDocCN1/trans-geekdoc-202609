```
```php
if (isset($_GET["id"]) && is_numeric($_GET["id"])) {
    if (isset($_GET["ok"])) {
        if ($db = oci_connect("user", "password", "orcl")) {
            $sql = "DELETE FROM guestbook WHERE id=:id";
            $command = oci_parse($db, $sql);
            oci_bind_by_name($command, ":id", intval($_GET["id"]));
            if (oci_execute($command)) {
                echo "<p>Entry deleted.</p>
                <p><a href=\"gb-admin.php\">Back to overview
                </a></p>";
            } else {
                echo "Error!";
            }
            oci_close($db);
        } else {
            echo "Error!";
        }
    } else {
        printf("<a href=\"gb-admin.php?id=%s&ok=1\">Really delete?
        </a>", urlencode($_GET["id"]));
    }
} else {
    if ($db = oci_connect("user", "password", "orcl")) {
        $sql = "SELECT * FROM guestbook ORDER BY date DESC";
        $command = oci_parse($db, $sql);
        if (oci_execute($command)) {
            while ($row = oci_fetch_object($command)) {
                printf("<p><b><a href=\"gb-admin.php?id=%s\">Delete this entry</a>
                - <a href=\"gb-edit.php?id=%s\">Edit this entry</a></b></p>
                <p><a href=\"mailto:%s\">%s</a> wrote on at %s:</p>
                <h3>%s</h3><p>%s</p><hr noshade=\"noshade\" />",
                urlencode($row->id),
                urlencode($row->id),
                htmlspecialchars($row->email),
                htmlspecialchars($row->author),
                htmlspecialchars(date("Y-m-d, H:i", intval($row->date))),
                htmlspecialchars($row->heading),
                nl2br(htmlspecialchars($row->entry))
                );
            }
        }
        oci_close($db);
    } else {
        echo "Error!";
    }
}
```
```