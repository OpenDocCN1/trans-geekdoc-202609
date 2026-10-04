```
/* Create a QueryResult object that will query the database by calling the
query() method from the database object and specifying the selector string to
be used. */
QueryResult<Object> studentname = db.query(selector1, Object.class);
```

```
/* Extract the name field from the list1 object */
String studentname = String.valueOf(list1.get(0));
```

```
/* Normally the name will be between the == and } components in the cloud
dabase, hence to obtain only the name, some processing is required using
the split method. */
String[] part1 = studentname.split("=");
String[] name1 = part1[1].split("}");
String name = name1[0];
```

```
// Display the evaluated value of the name in the appropriate textField.
jTextField5.setText(name);
```

```
/* Repeat the operation description for the Name field to extract the
Course field. */
QueryResult<Object> coursename = db.query(selector2, Object.class);
List list2 = coursename.getDocs();
String course = String.valueOf(list2.get(0));
String[] part2 = course.split("=");
String[] course1 = part2[1].split("}");
String courses = course1[0];
jTextField6.setText(courses);
```

```
}
/* This method defines the action to be performed when the 'RETRIEVE ALL
FIELDS' button is pressed. */
```