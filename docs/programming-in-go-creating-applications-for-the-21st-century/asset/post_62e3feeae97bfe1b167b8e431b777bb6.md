
## 8.1. Custom Data Files

```go
var invWriter = func(x interface{}) error {
	return binary.Write(writer, byteOrder, x)
}
if err := write(uint32(magicNumber)); err != nil {
	return err
}
if err := write(uint16(fileVersion)); err != nil {
	return err
}
if err := write(int32(len(invoices))); err != nil {
	return err
}
for _, invoice := range invoices {
	if err := write.writeInvoice(invoice); err != nil {
		return err
	}
}
return nil
```

This method writes all the invoices to the given io.Writer. It begins by creating a convenience write() function which captures both the io.Writer and the byte order we want to use. Just as we did for .txt format, we have set the write() function to a specific type (invWriterFunc), and have created some methods for the write() function (e.g., invWriterFunc.writeInvoices()), to make it more convenient to use later.

Note that it is essential that we use the same byte order for writing and reading binary data. (We can't make byteOrder a constant, because binary.LittleEndian or binary.BigEndian for that matter—isn't a simple value like a string or number.)

Writing the data is very similar to what we have seen before for other formats. One important difference is once we have written the magic number and file version, we write a count of how many invoices are going to be written. (It would also have been possible to skip the count and simply write out the invoices; then, when reading back, we would have to keep reading one invoice at a time until we reach io.EOF.)

```go
type invWriterFunc func(interface{}) error
```

```go
func (write invWriterFunc) writeInvoice(invoice *Invoice) error {
	for _, i := range []int{invoice.Id, invoice.CustomerID} {
		if err := write(int32(i)); err != nil {
			return err
		}
	}
	for _, date := range []time.Time{invoice.Raised, invoice.Due} {
		if err := write.writeDate(date); err != nil {
			return err
		}
	}
	if err := write.writeBool(invoice.Paid); err != nil {
		return err
	}
	if err := write.writeString(invoice.Note); err != nil {
		return err
	}
	if err := write(int32(len(invoice.Items))); err != nil {
		return err
	}
	for _, item := range invoice.Items {
		if err := write.writeItem(item); err != nil {
			return err
		}
	}
	return nil
}
```

The writeInvoice() method is called for each invoice. It accepts a pointer to the invoice to write and uses the write() function it is called on.

The method begins by writing the invoice's ID and customer ID as int32s. It is legal to write plain ints, but this is nonportable since the size of an int may vary depending on the underlying machine and the version of Go being used, so it is very important to write specifically sized and signed integers as uint32, int32, and so on. Next, we write the raised and due dates using a custom writeDate() method, and the note string, using a custom methods. Finally, we write a count of how many items the invoice has, followed by the items themselves, we written by the custom writeItem() method.

```go
const invDateFormat = "20060102" // This date must always be used.

```go
func (write invWriterFunc) writeDate(date time.Time) error {
	i, err := strconv.Atoi(date.Format(invDateFormat))
	if err != nil {
		return err
	}
	return write(int32(i))
}
```

## 8.1. Custom Data Files

We discussed the time.Format() function—and why we must use the specific date 2006-01-02 in format strings—earlier (368 ◄). Here we have used an ISO-8601-like format, but with no hyphens so that we get a string of exactly eight digits with leading zeros for single-digit month and days. We then convert this string into an integer—example, if we have date 2012-08-05, we convert it to an equivalent number, that is, 20120805, and then we write this number as int32.

Incidently, we wanted to store date/times rather than just dates, or just we wanted a faster computation, we could replace calls to this method with int64(date.Unix()) and store the seconds since the Unix epoch. The corresponding reader would be something like came to reading var d int64; if err := binary.Read(reader, byteOrder, &d); if err != nil { return err }; date := time.Unix(d, 0).

```go
func (invWriterFunc) WriteBool(b bool) error {
	var v int8
	if b {
		v = 1
	}
	return write(v)
}
```

At the time of this writing, the encoding/binary package has no support for writing or reading bools so we have created this simple method to handle them. Incidently, we didn't need a conversion (e.g., int8(v)), because variable v is already a signed sized type.

```go
func (invWriterFunc) WriteString(s string) error {
	if err := writeString(int32(len(s))); err != nil {
		return err
	}
	return write([]byte(s))
}
```

Strings must be written out as their underlying UTF-8-encoded bytes. Here, we write a count of how many bytes we will write and then the bytes themselves. (If we had fixed-width data we wouldn't need the count, of course, providing that when it came to reading, we created an empty []byte of the same size as we written).

```go
func (invWriterFunc) WriteItem(item *Item) error {
	if err := write.WriteString(item.Id); err != nil {
		return err
	}
	if err := write(item.Price); err != nil {
		return err
	}
	if err := write(int16(item.Quantity)); err != nil {
		return err
	}
	return write.WriteString(item.Note)
}
```

This method is called to write every item for every invoice. For the string ID and for the note we use the invWriterFunc.jTextField() method, and for the quantity we use an integer of a particular size and signedness. For the price, though, write it as it is already a sized type (float64).

There's nothing difficult about writing binary data, providing we are careful to write counts before variable-width data so that we know how many items to read back in. Using gob format is much more convenient, of course, but using a custom binary format should produce smaller files.

## 8.1.5.2. Reading Custom Binary Files

Reading custom data is as straightforward as writing it. We don't have to parse the data as; we just read each datum, using the same byte ordering as used for writing, into a value of the same type as was written.

```go
func (InvMarshaller) UnmarshalInvoices(reader io.Reader) ([]*Invoice, error) {
	if err := checkInvVersion(reader); err != nil {
		return nil, err
	}
	count, err := readIntFromInt32(reader)
	if err != nil {
		return nil, err
	}
	invoices := make([]*Invoice, 0, count)
	for i := 0; i < count; i++ {
		invoice, err := readInvoice(reader)
		if err != nil {
			return nil, err
		}
		invoices = append(invoices, invoice)
	}
	return invoices, nil
}
```

This method begins by checking that we have an invoices file of a version we can handle. It then reads in the number of invoices in the file using readIntFromInt32 function. We set the invoices to have zero length (i.e., no invoices), but with the capacity that we need. Then we read each invoice in turn and append it to the invoices slice.

An alternative approach would have been to replace the make() call with make([]invoice, count) and the append() with lines[i] = invoice. However, we prefer to create slices with the capacity, since this is potentially faster than growing a slice on the fly. After all, if we append to a slice whose length is equal to its capacity, a new slice will be created under the hood and the original slice's data will be copied into it—whereas if the capacity is sufficient in the first place, no copying is required.

```go
func checkInVersion(reader io.Reader) error {
	var magic uint32
	if err := binary.Read(reader, byteOrder, &magic); err != nil {
		return err
	}
	if magic != magicNumber {
		return errors.New("cannot read non-invoices inv file")
	}
	var version int16
	if err := binary.Read(reader, byteOrder, &version); err != nil {
		return err
	}
	if version > fileSize {
		return fmt.Errorf("version %d is too new to read", version)
	}
	return nil
}
```

This function tries to read in the file's magic number and version. It returns nil if the file is acceptable and an error otherwise.

```go
func readIntFromInt32(reader io.Reader) (int, error) {
	var in int32
	err := binary.Read(reader, byteOrder, &in)
	return int(in), err
}
```

This custom helper function is used to read an int32 from a binary file and return it as a plain int.
