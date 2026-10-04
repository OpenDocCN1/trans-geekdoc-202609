# 328 Part IV: No So Simple Applications

```
if ($author == "") { $author = "[no name]"; }

if ($root_id != $topic_id && $root_id != $parent_id) {
    if ($root_name == "") { $root_name = "[no topic name]"; }
    print paragraph("<b>$root:</b>
        anchor_tag("index.php?topic_id=$root_id")
        $root_name
    );
}
```

If there is a parent topic, the name of the topic is printed, along with a link to it.

```
if (!empty($parent_name)) {
    print paragraph("<b>$parent:</b>
        anchor_tag("index.php?topic_id=$parent_id")
        $parent_name
    );
}
```

```
// print out the current topic
print paragraph("<b>$name</b> by <b>$author</b> ($author_host) on <b>$create_dt</b>");
print paragraph($description);

if ($show_kids) {
    // print out a link to where the user can reply to
    // the current topic
    print paragraph("write_topic.php?topic_id=$topic_id
        <b>Reply to this</b>");
    );
}
```

```
// now display any children of the current topic
print paragraph(display_kids($topic_id, $level));
```