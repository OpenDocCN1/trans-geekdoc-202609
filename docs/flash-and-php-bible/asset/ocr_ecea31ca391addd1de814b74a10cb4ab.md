That is all the PHP code that is needed to develop this video application. Here is the completed PHP:

```
<?php

$action = (isset($_GET['a'])) ? $_GET['a'] : "";

$videos = array(
    array("Sample Video 1", "color.flv", 0),
    array("Sample Video 2", "color.flv", 0),
    array("Sample Video 3", "color.flv", 0),
    array("Sample Video 4", "color.flv", 0),
    array("Sample Video 5", "color.flv", 0),
    array("Sample Video 6", "color.flv", 0)
);

if($action == "getvideos")
{
    $xml = "<videos>";
    for($i=0; $i < count($videos); $i++)
    {
        $xml .= "\t<video>";
        $xml .= " <name="" . $videos[$i][0] . "">";
        $xml .= " <src="" . $videos[$i][1] . "">";
        $xml .= " <playCount="" . $videos[$i][2] . "">";
        $xml .= " </\n>";
    }
    $xml .= "</videos>";

    header("Content-type: text/xml");
    print $xml;
}

?>
```

# Developing a Poll Application

A poll is a very common feature of any Web site, but a person will often use a service that manages the poll instead of creating his or her own. The main problem with that approach is your data is on someone else's server. A less common issue is the lack of freedom with the design of the poll application.

# Building the PHP and MySQL

This application consists of the design, PHP development, and ActionScript to develop a full functional polling application, such as the one shown in Figure 13.6. The initial focus is on the SQL code that stores the poll data.