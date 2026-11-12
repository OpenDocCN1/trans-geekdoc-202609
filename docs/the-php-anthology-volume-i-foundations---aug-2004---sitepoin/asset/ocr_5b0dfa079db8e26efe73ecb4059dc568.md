```
// Set the style for each cell of the row
$cellStyle = 'style="font-family: verdana; font-size: 11;"';

// Apply the style
$table->setAllAttributes($cellStyle);

// Define the style for the column headings
$headerStyle = 'style="background-color: #ffffff;
font-family: verdana;
font-weight: bold;
font-size: 12;"';

// Set the row attributes for the header row
$table->setRowAttributes(0, $headerStyle);

// Set alternating row colors
$table->altRowAttributes(
    1,
    'style="background-color: #d3d3d3"',
    'style="background-color: #ffffff"',
    TRUE
);

// Display the table
echo $table->toHTML();
```

The end result is a neat looking table that we can order by column, as shown in Figure 9.1.