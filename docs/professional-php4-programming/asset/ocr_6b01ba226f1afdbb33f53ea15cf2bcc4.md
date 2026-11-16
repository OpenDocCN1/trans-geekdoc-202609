# # Multi-Byte Strings

There are quite a few languages where it isn't sufficient to use a single byte for each character. One byte has 8 bits and therefore can hold 256 (2^8) different values. Languages like Chinese or Japanese have many thousands of different characters. The Chinese script has more than 40,000. Japanese has all the Chinese characters and 2 more alphabets to boot. With these, each character might be two or more bytes long.

If we are using such strings in our scripts, we can't use the normal string functions, because they don't expect the characters to occupy more than one byte per character. Instead we have to use the string functions starting with mb.

So, to get the first three characters of a given string, use mb_substr() like this:

```
$start = mb_substr($string_with_chinese_characters, 0, 3);
```

Also take note of the different encoding the strings might have. To help with this, there is the function mb_detect_encoding(). With it, we can set the HTTP output encoding with mb_http_output(), so that the browser will understand. We can use this function together with mb_output_handler(), like this:

```
mb_http_output("UTF-8");
ob_start("mb_output_handler");
```

After using this function, all output will be converted to Unicode.

Note the "UTF-8" acronym. UTF-8 transforms all Unicode characters into a variable length encoding of bytes. The decisive advantage of this lies in its backward compatibility. For instance, it has the advantage that the Unicode characters corresponding to the familiar ASCII set have the same byte values as ASCII, namely 1 byte. Unicode characters transformed into UTF-8 can be used with existing software with few extensive software rewrites.

Finally, we send the correct MIME character set string using the function mb_preferred_mime_name():

```
header("Content-Type: text/html; charset=" . mb_preferred_mime_name($outputenc));
```

# ## PHP Multi-Byte String Module

There are quite a large number of multi-byte string functions collectively known as the PHP multi-byte string module. The emphasis is on Japanese character encoding, but the following characters sets are supported as of this moment:

UCS-4, UCS-4BE, UCS-4LE, UCS-2, UCS-2BE, UCS-2LE, UTF-32, UTF-32BE, UTF-32LE, UCS-2LE, UTF-16, UTF-16BE, UTF-16LE, UTF-8, UTF-7, ASCII, EUC-JP, SJIS, eucJP-win, SJIS-win, ISO-2022-JP(JIS), ISO-8859-1, ISO-8859-2, ISO-8859-3, ISO-8859-4, ISO-8859-5, ISO-8859-6, ISO-8859-7, ISO-8859-8, ISO-8859-9, ISO-8859-10, ISO-8859-13, ISO-8859-14, ISO-8859-15.