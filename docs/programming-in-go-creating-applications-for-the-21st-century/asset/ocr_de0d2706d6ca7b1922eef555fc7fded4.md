# 8.1. Custom Data Files

# Table 8.1 Format Speed and Size Comparisons

| Suffix | Read | Write | Size (KiB) | Read/Write LOC | Format |
|---|---|---|---|---||}{
| .gob | 0.3 | 0.2 | 7948 | 21 + 1 = 32 | Go Binary |
| .gob.gz | 0.5 | 1.5 | 2589 | | |
| .jsn | 4.5 | 2.2 | 16283 | 32 + 17 = 49 | JSON |
| .jsn.gz | 4.5 | 3.4 | 2678 | | |
| .xml | 6.7 | 1.2 | 18917 | 45 + 30 = 75 | XML |
| .xml.gz | 6.9 | 2.7 | 2730 | | |
| .txt | 1.9 | 1.0 | 12375 | 86 + 53 = 139 | Plain text (UTF-8) |
| .txt.gz | 2.2 | 2.2 | 2514 | | |
| .inv | 1.7 | 3.5 | 7250 | 128 + 87 = 215 | Custom binary |
| .inv.gz | 1.6 | 2.6 | 2400 | | |

loads. The size column shows the sizes in kibytes—these should be very consistent across machines. For this data set, the compressed sizes are surprisingly similar, even when the uncompressed sizes vary considerably. The lines of code exclude that that is common to all formats (e.g., for decompression and compressing the structs).

The timings and file sizes are what we reasonably expect—apart from the extremely fast reading and writing of the plain text format. This is thanks to the fmt package's excellent print and scan functions in conjunction with a custom text format that we designed to be easy to parse. For the JSON and XML formats, instead of using the default storage for time, Time values (ISO-8601 date/time string), we have simply stored the date part—which has slightly reduced the file size at the expense of some processing speed and some additional code. For example, the JSON code could run faster, and about the same number of lines as the Binary code, if we allowed it to handle time values.

For binary data, the Binary format is the most convenient to use—it is fast, extremely compact, requires very little code, and is relatively easy to adapt to data changes. However, if we use custom types that are not initially gob-encodable and have to make them satisfy the gob.Encoder and Decoder interfaces, this can considerably slow down writing and reading in gob format, and also bloat out the file size.

For human-readable data, XML is the probable format to use—particularly since it is so useful as a data exchange format. More lines are required to handle XML format than JSON format. This is because Go lacks an interface that is expected to be made good in a later Go 1.x release, and also because we have used parallel data types (XMLInvoice and XMLItem) to help map between the XML data and the invoice data (Invoice and Item). Applications that use XML as their external format would not