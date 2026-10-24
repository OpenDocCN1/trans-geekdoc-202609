Table 2-1: Each of the USB's four transfer types is suited for different uses.

| Transfer Type | Control | Bulk | Interrupt | Isochronous |
|---|---|---|---|---|
| Typical Use | Identification and configuration | Printer, scanner, drive | Mouse, keyboard | Streaming audio, video |
| Required? | yes | no | no | no |
| Low speed allowed? | yes | no | yes | no |
| Data bytes/millisecond per transfer, maximum possible per pipe (high speed).* | 15,872 (thirty-one 64-byte transactions/microframe) | 53,248 (thirteen 512-byte transactions/microframe) | 24,576 (three 1024-byte transactions/microframe) | 24,576 (three 1024-byte transactions/microframe) |
| Data bytes/millisecond per transfer, maximum possible per pipe (full speed).* | 832 (thirteen 64-byte transactions/frame) | 1216 (nineteen 64-byte transactions/frame) | 64 (one 64-byte transaction/frame) | 1023 (one 1023-byte transaction/frame) |
| Data bytes/millisecond per transfer, maximum possible per pipe (low speed).* | 24 (three 8-byte transactions) | not allowed | 0.8 (8 bytes per 10 milliseconds) | not allowed |
| Direction of data flow | IN and OUT | IN or OUT | IN or OUT (USB 1.0 supports IN only) | IN or OUT |
| Reserved bandwidth for all transfers of the type (percent) | 10 at low/full speed, 20 at high speed (minimum) | none | 90 at low/full speed, 80 at high speed (isochronous & interrupt combined, maximum) |  |
| Error correction? | yes | yes | yes | no |
| Message or Stream data? | message | stream | stream | stream |
| Guaranteed delivery rate? | no | no | no | yes |
| Guaranteed latency (maximum time between transfers)? | no | no | yes | yes |
| *Assumes transfers use maximum packet size. |  |  |  |  |

Bulk transfers are intended for situations where the rate of transfer isn't critical, such as sending a file to a printer, receiving data from a scanner, or accessing files on a drive. For these applications, quick transfers are nice but the data can wait if necessary. If the bus is very busy, bulk transfers are delayed, but if the bus is otherwise idle, bulk transfers are very fast. Only