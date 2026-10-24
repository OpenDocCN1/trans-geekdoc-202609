The item size (bits 1 and 0) indicates how many data bytes the item contains. Note that an item size of 3 (11 in binary) corresponds to 4 data bytes:

| Item Size (binary) | Number of Data Bytes |
|---|---|
| 00 | 0 |
| 01 | 1 |
| 10 | 2 |
| 11 | 4 |

The item type (bits 3 and 2) describes the scope of the item: Main (00), Global (01), or Local (10). Main items define or group data fields in the descriptor. Global items describe data. Local items define characteristics of individual controls or data. (This chapter has more information about these item types.)

The item tag (bits 4-7) indicates the item's function.

# Long Items

A Long item uses multiple bytes to store the same information as the Short item's 1-byte prefix stores. A Long item's 1-byte prefix (FEh) identifies the item as a Long item. In addition, the item has a byte that specifies the number of data bytes, a byte containing the item tag, and up to 255 bytes of data.

# The Main Item Type

A Main item defines or groups data items within a report descriptor. There are five Main item types. Input, Output, and Feature items each define fields in a type of report. Collection and End Collection items group related items within a report. The default value for all Main items is zero.