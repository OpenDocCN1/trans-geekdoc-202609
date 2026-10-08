# Core PHP Programming

```
print("/TH>");
}

//loop over each row
for($row=1; $row = filepro_rowcount(); $row++) {
    print("/TR\n");

    //output fields
    for($col=1;$col = filepro_fieldcount(); $col++) {
        print("/TD>");
        print(filepro_retrieve($row, $col));
        print("/TD>");
    }
    print("/TR\n");
}

print('/TABLE>');
?>
```

# integer filepro_fieldcount()

Use filepro_fieldcount to find the number of fields. See the filepro example above.

# string filepro_fieldname(integer field_number)

The filepro_fieldname function returns the name of the field for the given field number. See the filepro example above.

# string filepro_fieldtype(integer field_number)

The filepro_fieldtype function returns the edit type for the given field number. See the filepro example above.

# string filepro_retrieve(integer row, integer field)

The filepro_retrieve function returns the value for the specified field on the specified row. See the filepro example above.

# integer filepro_rowcount()

Use filepro_rowcount to find the number of rows. See the filepro example above.