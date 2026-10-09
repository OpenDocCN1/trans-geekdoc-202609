```
_ = writer.Write(row)
}

writer.Flush()

file.Close()
}
```

The resulting file viewed in spreadsheet form below.

HOST IP ADDR LOCATION
RTR1 1.1.1.1 Seattle, WA
RTR2 2.2.2.2 Nevada, NV

The same file viewed in plain text from a text editor below.

```
HOST,IP ADDR,LOCATION
RTR1,1.1.1.1,"Seattle, WA"
RTR2,2.2.2.2,"Nevada, NV"
```