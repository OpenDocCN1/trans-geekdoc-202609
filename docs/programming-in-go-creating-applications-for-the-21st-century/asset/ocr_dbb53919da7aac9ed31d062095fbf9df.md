# Chapter 8. File Handling

check the version, and if it is one we can convert all the XML structs back to the structs used internally in our program. Naturally, this conversion would be unnecessary if we used XML-tagged structs.

```
func (xmlInvoices *XMLInvoices) Invoices() ([]*Invoice,
	err error) {
	invovoices := make([]*Invoice, len(xmlInvoices.Invoices))
	for _, xmlInvoices := range xmlInvoices.Invoices {
	vinvoice, err := xmlInvoices.Invoice()
		if err != nil {
		return nil, err
	}
		invoices = append(invoices, invoice)
	}
	return invoices, nil
}
```

The XMLInvoices.Invoices() method converts an *XMLInvoices into an []*Invoice. It is the inverse of the XMLInvoicesForInvoices() function (374 ◄), and passes all the conversion work to the XMLInvoice.Invoice() method.

```
func (xmlInvoice *XMLInvoice) Invoice() (invoice *Invoice, err error) {
	invoice := &Invoice{
		Id:
			xmlInvoice.Id,
		CustomerId:xmlInvoice.CustomerId,
			Paid:xmlInvoice.Paid,
			Note:strings.TrimSpace(xmlInvoice.Note),
		Items:make([]*Item, 0, len(xmlInvoice.Item)),
	}
	if invoice.Raised, err = time.Parse(dateFormat, xmlInvoice.Raised) {
		err != nil {
		return nil, err
	}
tif invoice.Due, err = time.Parse(dateFormat, xmlInvoice.Due) {
		err != nil {
		return nil, err
	}
	for _, xmlItem := range xmlInvoice.Item {
	item := &Item{
			Id:xmlItem.Id,
			Price:xmlItem.Price,
			Quantity:xmlItem.Quantity,
			Note:strings.TrimSpace(xmlItem.Note),
	}
	\vinvoice.Items = append(invoice.Items, item)
}
```