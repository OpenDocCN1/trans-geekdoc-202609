# Using a Serial Number rather than the RecordID will make your life very difficult.

| Auto-Enter | Validation | Storage | Furigana |
|---|---|---|---|
| Automatically enter the following data into this field: | | | |
| Creation Date | | | |
| Modification Date | | | |
| Serial number | | On creation | On commit |
| next value | 1 | increment by 1 | |
| Value from last visited record | | | |
| Data: | | |

| Calculated value | Specify... |
|---|---|
| Do not replace existing value of field (if any) | |
| Looked-up value | Specify... |

Prohibit modification of value during data entry

# Figure 5-9: Auto Enter Serial Number for the Primary Key

Evaluate this calculation from the context of php_demo

| Current Table (php_demo) | Operators | View: all functions by name |
|---|---|---|
| FirstName | & | Abs (number) |
| LastName | + | Asc (number) |
| Number | | Count (number) |
| Date | 1 | Atn (number) |
| Timestamp | | Average (field result...) |
| Image | 0 | Case (text) result(text2 resu... |
| Calculation | | Ceiling (number) |
| RecordID | | Char (number) |
| Email | | Choose (text; res0) result1 r... |
| Serial - | | Cast (text; res0) result1 |
| Get(RecordID) | | |

Calculation result must be Text

Do not evaluate all referenced fields are empty

# Figure 5-10: Auto Enter Get(RecordID) Rather than the Auto Entered Serial Number

# Layouts, Not Table Access

For those of you who have experience with ASP or JSP you are well accustomed to using SQL to retrieve data
from tables and joining tables. I hate to run on your parade, the FileMaker API for PHP does not give you that
kind of access to the database. You have to create a specific layout for your web page that includes all the
bells and whistles that you might need, such as value lists attached to the fields and portals. The real problem
with this scenario is that a single layout may force you to expose extra fields and records, which will