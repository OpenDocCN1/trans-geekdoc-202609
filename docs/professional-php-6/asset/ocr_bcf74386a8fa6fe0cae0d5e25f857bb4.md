# Using the Decorator

After you’ve done the work developing the Decorator classes, you’ll find that it is a very flexible and powerful pattern. Not only is it easy to use, but different Decorators can be combined to give multiple effects to the same widget. Decorators can even be applied in different order. Another Decorator class follows. Save the file as closebox_decorator.php:

```
<?php require_once("abstract_widget.php");

class CloseBoxDecorator extends Widget {

    private $widget;

    function __construct(Widget $widget) {
        $this->widget = $widget;
    }

    public function draw() {
        print '<table border=0 cellspacing=1 bgcolor="#666666">';
        print '<tr bgcolor=#666666>';
        print '<td align=right>';
        print '<table width=10 height=10 bgcolor="cccccc">';
        print '<tr><td><b>x</b></td></tr>';
        print '</table>';
        print '</td>';
        print '<tr>';
        print '<tr bgcolor=#ffffff>';
        print '<td>';

        $this->widget->draw();

        print '</td>';
        print '</tr>';
        print '</table>';
    }

    public function update(Observable $subject) {
        $this->widget->update($subject);
    }
}
```

The preceding Decorator applies a simple menu bar with a closed box on it. Combining the two Widgets with the two Decorators is easy. Save the following file as decorator.php:

```
<?php
require_once("abstract_widget.php");
require_once("closebox_decorator.php");
require_once("border_decorator.php");
require_once("observable.php");

$dat = new DataSource();
$widgetA = new BasicWidget();
$widgetB = new FancyWidget();
```