# 8.1. Custom Data Files

```
var version int
if err := decoder.Decode(&version); err != nil {
    return nil, err
}
if version > fileVersion {
    return nil, fmt.Errorf("%d is too new to read", version)
}
var invoices []Invoice
err := decoder.Decode(&invoices)
return invoices, err
```

We have three items of data to read in: the magic number, the file version, and all the invoices. The gob.Decoder. Decode() method takes a pointer to the value it must populate with the gob data decodes, and returns an error or nil. We use the first two variables (magic and version) to check that we have a gob invoices file and that the file version is one we can handle. Then we read the invoices, in the process of which the gob.Decoder.Decode() method will increase the size of the invoices slice to accommodate the invoices it reads and populate the slice with pointers to Invoices (and their Items) that the function creates on the fly. At the end, the method returns the invoices and nil or an error if a problem occurred.

If the invoices data changed by the addition of extended fields, this will continue to work as is for Booleans, numbers, strings, time.Times, and structs containing these types. Of course, for data that contains other types, we must update the methods that satisfy the gob.GobEncoder and GobDecoder interfaces.

When dealing with struct types, the gob format is very flexible, coping seamlessly with some differences. For example, if a struct that has a value is written in gob format, the value can be read back into the same struct—or into many similar struct types, perhaps one has a pointer to the value, or where the type of the value is different but compatible (int vs. uint or similar). As the invo example shows, gob format has no problem handling nested data (although, at the time of this writing, it cannot handle recursive values). The gob documentation discusses what the format can cope with and explains the format's internals, none of which concern us providing we use the same types for writing and for reading—just as we have done in this example.

# 8.1.5. Handling Custom Binary Files

Although Go's encoding/gob package is very easy to use and requires very little code, we might still need to create our own custom binary formats. A custom binary format is likely to achieve the most compact data representation possible