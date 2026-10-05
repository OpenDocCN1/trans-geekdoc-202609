# Chapter 8. File Handling

This chapter's first section shows how to read and write files using standard and custom format files. The second section covers Go's support for handling archive files and compression.

# 8.1. Custom Data Files

It is quite common for programs to maintain internal data structures and to provide import/export functionality to support data interchange, and also to facilitate the processing of their data by external tools. Since our concern here is with file handling, we will focus purely on how to write and read data to and from standard and custom formats from into a program's internal data structures.

For this section we use the same data for all the examples so that we can get a direct comparison between the various file formats. All the code is taken from the invoicedata program (in the invoicedata directory in the invoicedata. gob.go, inv.go, jsn.go, txt.go and xml.go). The program takes two filenames as command-line arguments, one to read and one to write (which must be different). The program reads the data from the first file (in whatever format its suffix indices) and writes the same data to the second file (again, using whatever format its suffix indicates).

The files created by invoicedata work cross-platform, that is, a file created on say, Windows, is readable on Mac OS X and Linux, and vice versa, no matter which format it is. Gzip-compressed files (e.g., invoices.gz) can be read and written seamlessly; compression is covered in the second section (§8.2 -> 397).

The data consists of []Invoice, that is, a slice of pointers to Invoice values. Each invoice is held in an Invoice value, and each invoice holds zero or more items in its Items field of type []Item(slice of pointers to Item).

```
type Invoice struct {
    Id int
    CustomerID int
    Raised time.Time
    Due time.Time
    Paid bool
    Note string
    Items []*Item
}

type Item struct {
    Id string
    Price float64
    Quantity int
    Note string
}
```

These structures are used to hold the data. Table 8.1 shows some informal comparisons of how long it takes to read and write the 50 000 random invoices, and the size of the file occupied by those invoices in each format. The timings are in seconds rounded up to the nearest tenth of a second—they should be taken as unitless unless they will undoubtedly vary on different hardware under