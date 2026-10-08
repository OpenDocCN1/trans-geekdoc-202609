# Chapter 9 Creating Your Web Database

Table 9.9 shows the possible different display types for TIMESTAMP.

| Table 9.9 TIMESTAMP Display Types |
| Type Specified | Display |
| --- | --- |
| TIMESTAMP | YYYYMDDDHMMSS |
| TIMESTAMP (14) | YYYYMDDDHMMSS |
| TIMESTAMP (12) | YYYYMDDDHMM |
| TIMESTAMP (10) | YYYYMDDDHH |
| TIMESTAMP (8) | YYYYMMDD |
| TIMESTAMP (6) | YYYYMM |
| TIMESTAMP (4) | YY |

String types fall into four groups. First, there are plain strings—that is, short pieces of text. These are the CHAR (fixed-length character) and VARCHAR (variable-length character) types. You can specify the width of each. Columns of type are padded to the maximum width regardless of the size of the data, VARCHAR columns vary in width with the data (Note that MySQL strips the spaces from CHARs when they are retrieved and from VARCHARs when they are *stored*.) There is a space versus speed trade-off with these two types, which we discuss in more detail in Chapter 12.

Second, there are BINARY and BINARY BLOB types. These are strings of bytes rather than characters.

Third, there are CHAR and BLOB types. These types, which come in various sizes, are for longer text or binary data, BLOBs, or *binary large objects*, can hold anything you like—for example, or sound data.

Because these column types can hold large amounts of data, they may require some special considerations. We discuss this in Chapter 12.

The fourth group has two types: SET and ENUM. The SET type specifies that values in this column must come from a particular set of specified values. Column values can contain more than one value from the set. You can have a maximum of 64 things in the specified set.

ENUM is an enumeration. It is similar to SET, except that columns this can have only one of the specified values or NULL, and you can have a maximum of 65,535 things in the enumeration.

We summarized the string data types in Tables 9.10–9.13. Table 9.10 shows the plain string types.