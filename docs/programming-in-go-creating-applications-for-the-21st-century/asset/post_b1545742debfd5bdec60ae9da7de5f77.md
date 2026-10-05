
## 8.1. Custom Data Files

its strings.Fields() and strings.Split() functions, and the fmt package's scan functions.

## 8.1.4. Handling Gob Binary Files

The binary ("gob") format is a self-describing sequence of binary values. Internally, the Go binary format consists of a sequence of zero or more chunks, each of which has a byte count, a sequence of zero or more typeid–typeSpecification pairs, and a typeid–value pair. The typeid–Specification pairs may be omitted if the value's typeid is predefined (e.g., bool, int, etc.); otherwise each the type is needed to describe a custom type (a custom struct). Type pair typeIds are negated to distinguish between type pairs and value pairs. As we will see, we don't need to know any of the internals to make use gob format, the encoding/gob package takes care of all the low-level details for us, behind the scenes.*

The encoding/gob package provides encoder and decoder functionality in the same way as the encoding/json package, and is just easy to use. In general, gob format is the most convenient Gob to use for data files or for transmitting data over network connections, providing that human readability is not a requirement.

### 8.1.4.1. Writing Gob Binary Files

Here is a method for writing an entire data set of []Invoice items to an open file (or anything that fulfills the io.interface) in gob format.

```go
type GobMarshaler struct{
func (GobMarshaler) MarshalInvoices(writer io.Writer,
	invoices []Invoice) error {
		encoder := gob.NewEncoder(writer)
	if err := encoder.Encode(magicNumber); err != nil {
			return err
	}
	if err := encoder.Encode(fileVersion); err != nil {
			return err
	}
	return encoder.Encode(invoices)
}
```

We begin by creating a gob encoder that wraps the io.Writer and provides a writer to which we can write our data.

> * A detailed description of the format is given in the documentation, golang.org/pkg/encoding/gob/. And Rob Pike has written an interesting blog post on gob format, blog.golang.org/2011/03/gobs-of-data.html.

# Chapter 8. File Handling

We write the data using our slice of gob.Encoder.Encode() method. This method copies perfectly with our slice of invoices each of which contains its own slice of items. The method returns an error or nil; if we get an error we immediately return it to the caller.

Writing a magic number and a file version isn't necessary, of course, but as one of the exercises we will show, doing this makes it easier to change the file format later.

Notice that the method isn't concerned with the types of the data it encodes, it is so trivial to create similar functions for writing gob data. Furthermore, the GobMarshaler.MarshalInvoices() method will not require any changes to write in a new format.

Since our Invoice struct's fields are all Booleans, numbers, strings, time.Times, or structs (i.e., Items) which themselves contain only Booleans, numbers, strings, time.Times, or structs, the code works here as is.

If our structs contained fields that aren't gob-encoded we would have to make our structs satisfy the gob.Encoder and gob.Decoder interfaces. The gob encoder is smart enough to check whether a value it is asked to encode is a gob.GobEncoder, and if it is, the encoder uses the value's own GobEncode() method rather than using its own built-in encoding code. The same thing applies to decoding with the check being made for a Decode() method that satisfies the gob.Decoder interface. The invoiced example's source code's gob file includes the—unnecessary, and commented out—code to make an Invoice encoder and decoder, just to show an easy way to do it). Making a struct satisfy these interfaces can significantly slow down gob writing and reading, as well as producing larger files.

### 8.1.4.2. Reading Go Binary Files

Reading gob data is just as easy as writing it—providing we read back into top-level variables of the same types as the ones written. The GobMarshaler.UnmarshalInvoices() method takes an io.Reader(e.g., a file opened for reading) from which we read the data.

```go
func (GobMarshaler) UnmarshalInvoices(reader io.Reader) ([]*Invoice,
	error,
	decoder := gob.NewDecoder(reader)
	var magicNumber int
tif err := decoder.Decode(&magicNumber); err != nil {
		return nil, err
}
tif magicNumber != magicNumber {
		return nil, errors.New("cannot read non-invoices gob make file")
}
```

```go
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

When dealing with struct types, the gob format is very flexible, coping seamlessly with some differences. For example, if a struct that has a value is written in gob format, the value can be read back into the same struct—or into many similar struct types, perhaps one has a pointer to the value, or where the type of the value is different but compatible (int vs. uint or similar). As the invo example shows, gob format has no problem handling nested data (although, at the time of this writing, it cannot handle recursive values). The gob documentation discusses what the format can cope with and explains the format's internals, none of which concern us providing we use the same types for writing and reading.

## 8.1.5. Handling Custom Binary Files

Although Go's encoding/gob package is very easy to use and requires very little code, we might still need to create our own custom binary formats. A custom binary format is likely to achieve the most compact data representation possible and be very fast to write and read. In practice, we have found that writingand reading in Go format is dramatically faster than using a custom binary format—and creates files that are not much bigger. However, some of the advantage is lost if we have mostly data that isn't gob-encable by satisfying the gob.Encoder and Decoder interfaces. Of course, in some situations we may need to interoperate with other software that uses its own custom binary format that we must be able to write and, so knowing how to work with binary files can be very useful.

### 8.5.1. Writing Custom Binary Files

Writing data in binary format is straightforward thanks to the encoding/binary package's binary.Write() function.

```go
type InvMarshaler struct{
    var byteOrder = binary.LittleEndian
    func (InvMarshaler) MarshalInvoices(writer io.Writer,
        invoices []*Invoice) error {
```
