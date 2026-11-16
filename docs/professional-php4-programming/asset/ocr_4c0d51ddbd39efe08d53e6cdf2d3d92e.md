The final widget we create for our window is a GtkButton with the text Log in on it. We connect the clicked signal for this button to the doLogin() function. The user will click this button when they have filled in the username and password. This causes the clicked signal to be emitted, and the doLogin() function is called:

```
$widgets['main']['login_btn'] = &new GtkButton('Log in');
$widgets['main']['login_btn']->connect('clicked', 'doLogin');
```

The next few function calls place the widgets we just created into the instance of GtkTable we created at the beginning of the function. This is all done by calling the attach() method of GtkTable. This method accepts between five and nine arguments. The first parameter is the widget we want to place into the table. The next four parameters specify where in the table the widget will be placed:

```
$widgets['main']['table']->attach($widgets['main']['label_name'],
0, 1,
0, 1);

$widgets['main']['table']->attach($widgets['main']['label_pass'],
0, 1,
2, 3);

$widgets['main']['table']->attach($widgets['main']['login_name'],
1, 2,
0, 1);

$widgets['main']['table']->attach($widgets['main']['login_pass'],
1, 2,
2, 3);

$widgets['main']['table']->attach($widgets['main']['login_btn'],
0, 2,
3, 4);
```

The position of the child widget within a table is specified in relation to column and row lines that make up the bounding box for that widget. So for the table we created at the beginning of the function we have 4 rows and 2 columns. This means we have five row lines (numbered 0-4) and two column lines (numbered 0-2). So in our first call to attach we are placing our widget between grid lines 0 and 1 horizontally, and between grid lines 0 and 1 vertically as shown in the diagram below:

![](bbox=[0.29, 0.7, 0.71, 0.92])