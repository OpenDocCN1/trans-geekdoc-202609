```
fmt.Println(string(inv))
}
```

The output displays a file with each value in JSON format. While the JSON formatted data was written to a file to demonstrate the capability, it is also common to write JSON formatted data to a REST API, as shown later in Chapter 4.2.

```
{
"total": 3,
"devices": [
"SW1",
"SW2",
"SW3"
]
}
```