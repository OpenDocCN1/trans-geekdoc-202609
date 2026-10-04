# Table 12-2 Omitting Leading 0s and All 0 Segments

| Type | Format |
|---|---|
| Preferred | 2001:0db8:0000:1111:0000:0000:0000:0200 |
| Compressed with spaces | 2001: db8: 0:1111: : 200 |
| Compressed | 2001:db8:0:1111::200 |
| Preferred | 2001:0db8:0000:0000:ab00:0000:0000:0000 |
| Compressed with spaces | 2001: db8: 0: 0:ab00:: |
| Compressed | 2001:db8:0:0:ab00:: |
| Preferred | 2001:0db8:aaaa:0001:0000:0000:0000:0000 |
| Compressed with spaces | 2001: db8:aaaa: 1:: |
| Compressed | 2001:db8:aaaa:1:: |
| Preferred | fe80:0000:0000:0000:0123:4567:89ab:cdef |
| Compressed with spaces | fe80: : 123 :4567 :89ab :cdef |
| Compressed | fe80::123:4567:89ab:cdef |
| Preferred | fe80:0000:0000:0000:0000:0000:0000:0001 |
| Compressed with spaces | fe80: : : 1 |
| Compressed | fe80::0 |
| Preferred | 0000:0000:0000:0000:0000:0000:0000:0001 |
| Compressed with spaces | : : 1 |
| Compressed | ::1 |
| Preferred | 0000:0000:0000:0000:0000:0000:0000:0000 |
| Compressed with spaces | :: |
| Compressed | :: |