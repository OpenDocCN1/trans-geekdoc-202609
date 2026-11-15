The third parameter allows conversion with a specified character set. The default value for this is ISO-8859-1. The other values can be found in Table 7.1.

| Character Set | Alternative Designations | Description |
|---|---|---|
| ISO-8859-1 | ISO8859-1 | Western Europe, Latin-1 |
| ISO-8859-15 | ISO8859-15 | Western Europe, Latin-9; new compared to ISO-8859-1: Euro characters, French accents, Scandinavian letters |
| UTF-8 | | Eight-bit Unicode |
| cp866 | ibm866, 866 | Cyrillic character set |
| cp1251 | Windows-1251, win-1251, 1251 | Cyrillic character set for Windows |
| cp1252 | Windows-1252, 1252 | Windows character set Western Europe |
| KOI8-R | koi8-ru, koi8r | Russian character set |
| BIG5 | 950 | Traditional Chinese (Taiwan) |
| BIG5-HKSCS | | Traditional Chinese with Hong Kong extension |
| GB2312 | 936 | Simple Chinese |
| Shift_JIS | SJIS, 932 | Japanese |
| EUC-JP | EUCJP | Japanese |

# Table 7.1 Character Sets

htmlspecialchars(String, quotation marks, character set) works in principle exactly like htmlentities() but does not convert all HTML special characters. The following are converted:

```
< > ' " &
```

German umlauts, for example, are not included. Why is there a slimmed-down version? Especially in English-speaking countries, the complete conversion of all special characters is often not necessary or not desired. The entities converted by htmlspecialchars() are also the decisive characters of HTML syntax.

# Convert Special Characters Back

Now for the other way round: converting HTML special characters back into a normal string. For this, PHP provides the html_entity_decode(String, quotation marks, character set) function. It uses the same parameters as htmlentities().