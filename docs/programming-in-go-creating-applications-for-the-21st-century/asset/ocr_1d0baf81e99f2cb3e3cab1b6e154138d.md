# 406 Chapter 8. File Handling

tiny test files: utf16-to-utf8/utf16-to-utf8.txt and utf16-to-utf8/utf16-le.txt.
The binary package's Read() function can read uint16 values (which is what
UTF-16 characters are) using a specified endianness. And the unicode/utf16
package's Decode() function can convert a slice of uint16 values to a slice of
code points (i.e., to []rune); so wrapping the result of a utf16.Decode() call
in string() is to produce a UTF-8-encoded string. A solution is
the the file utf16-to-utf8/utf16-to-utf8.go, and is around 50 lines excluding
imports.

+   3. Copy the invoicedata directory to, say, my invoicedata, and modify the
invoicedata program in a few distinct ways. First, change the Invoice and
Items to those shown below.

```
type Invoice struct { // fileVersion type Item struct { // fileVersion
  Id int // 100 string // 100
  CustomerID int // 100 Price float64 // 100
  DepartmentID string // 101 Quantity int // 100
  Raised time.Time // 100 TaxBand int // 101
  Due time.Time // 100 Note string // 100
  Paid bool // 100
  Note string // 100
  Items []*Item // 100
}
```

Now modify the program so it always writes invoices in the new format
(i.e., one that handles the new structs), and can read in invoices in the
original format or in the new format.

When the program reads data in the original format, the zero values
for the extra fields are not acceptable, populate these fields with values
according to these rules: Set an invoice's department ID to "GEN" if the
invoice ID is less than 3000, to "MKT" if the ID is less than 4000, to "COM" if
the ID is less than 5000, to "ERP" if the ID is less than 6000, to "INP" if the ID
is less than 7000, to "TZ" if the ID is less than 8000, to "V20" if the ID is
than 9000, and to "X15" otherwise. Set each item's band to the integer
value of the invoice's third character. For example, if the ID is "JU4661", the
tax band should be 4.

A solution is provided in the invoicedata directory. The solution adds
three functions to invoicedata.go: one to update all the invoices in []*In-
voice (i.e., to provide acceptable values for the new fields), one to update
an individual invoice, and one to update individual item. The solution
needed changes to all the .go files, with the jsn.go, xml.go, and txt go
most affected. In all, the changes amount to around 150 lines of addition-
al code.