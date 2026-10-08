![](bbox=[0.231, 0.096, 0.529, 0.269])

<??

```
class classroom {
    var $name;
    function room($name="unnamed") {
        $this->name = $name;
    }
}

class house {
    //array of rooms
    var $room;
}

//create empty house
$home = new house();

//add some rooms
$home->room[] = new room("bedroom");
$home->room[] = new room("kitchen");
$home->room[] = new room("bathroom");

//show the first room of the house
print($home->room[0]->name);
?>
```