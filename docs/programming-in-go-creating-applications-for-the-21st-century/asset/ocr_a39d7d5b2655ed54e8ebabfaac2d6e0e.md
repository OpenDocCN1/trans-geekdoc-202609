# 8.1. Custom Data Files

no invoices), but with the exact capacity that we need. Then we read in each invoice in turn and append it to the invoices slice.

An alternative approach would have been to replace the make() call with make([]invoice, count) and the append() with lines[i] = invoice. However, we prefer to create slices with the capacity they need, since this is potentially faster than growing a slice on the fly. After all, if we append to a slice whose length is equal to its capacity, a new slice will be created under the hood and the original slice's data will be copied into it—whereas if the capacity is sufficient in the first place, no copying is required.

```
func checkInVersion(reader io.Reader) error {
	var magic uint32	if err := binary.Read(reader, byteOrder, &magic); err != nil {
	return err
	}
	if magic != magicNumber {
	return errors.New("cannot read non-invoices inv file")
	}
	var version int16	if err := binary.Read(reader, byteOrder, &version); err != nil {
	return err
	}
	if version > fileSize {
	return fmt.Errorf("version %d is too new to read", version)
	}
	return nil
}
```

This function tries to read in the file's magic number and version. It returns nil if the file is acceptable and an error otherwise.

The binary.Read() function is the complement of the binary.Write() function—it takes an io.Reader to read from, the byteOrder to use, and a pointer to an item of the exact type for it to populate.

```
func readIntFromInt32(reader io.Reader) (int, error) {
	var in int32
	err := binary.Read(reader, byteOrder, &in)
	return int(in), err
}
```

This custom helper function is used to read an int32 from a binary file and return it as a plain int.