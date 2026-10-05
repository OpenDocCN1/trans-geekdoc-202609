# 364

# Chapter 8. File Handling

need the parallel data types or the conversions that the invoicedata program needs, so are likely to be faster and require less code than the invoicedata examples.

In addition to reading and writing speed, file size, and lines of code, there is one other issue that we should consider: format robustness. For example, if we add one field to the Invoice struct and one item to the Item struct, we will need to change our file formats. How easy is it to adapt our code to write and read the new format—and also to continue reading the old format? Providing we take care of version our file formats changes are pretty straightforward to cater to (one of the chapter's exercises will demonstrate)—with the exception of JSON format for adapting the code to be read both the old and new formats is slightly tricky.

In addition to the Invoice and Item structs, all the file formats share constants:

```
const (
    fileType      = "INVOICES" // Used by text formats
    magicNumber   = 0x125 // Used by binary formats
    fileVersion   = 100 // Used by all formats
    dateFormat    = "2006-01-02" // This date must always be used
)
```

The magicNumber is used to uniquely identify invoice files.* The FileVersion indicates the invoice file version—using this makes it easier to change the program later on to accommodate the data. The dateFormat shows how we want dates formatted in human-readable formats and is discussed later on (368).

We have also created a couple of interfaces.

```
type InvoicesMarshaler interface {
    MarshalInvoices(writer io.Writer, invoices []*Invoice) error
}
ntype InvoicesUnmarshaler interface {
    UnmarshalInvoices(reader io.Reader) ([]*Invoice, error)
}
```

The purpose of this is to make it easy to use a reader or writer for a specific format in a generic way. For example, here is the function the invoicedata program uses to read invoices from an open file.

> * There is no universal repository of magic numbers, so we cannot be certain that any particular magic number hasn't been used before.