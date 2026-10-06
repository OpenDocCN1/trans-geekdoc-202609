# Part II: Learning Language

# Padding the Output

You can add characters to the left (by default) or the right of the formatted argument in order to pad it out to a fixed width. This is useful if you want to add zeros to a number, or horizontally align as many strings by padding with spaces.

To add padding you insert a padding specifier into your conversion specification, before the type specifier. The padding specifier consists of either a zero (to pad with zeros) or a space character (to pad with spaces), by the number of characters to pad the result out to. printf() then adds as many zeros or spaces as required to make the result correct.

For example, the following code displays various numbers, using leading zeros to ensure the result aligns with six digits:

```
printf("%06d\", 123);      // Displays "000123"
printf("%06d\", 4567);     // Displays "004567"
printf("%06d\", 123456);   // Displays "123456"
```

The padding specifier can add characters where required, but it never truncates the output. So printf ("%06d", 1234567) displays "1234567", not "1234567".

This example pads strings using leading spaces to ensure they're right-aligned:

```
printf("%pre\">\nprintf("% 15s\n", "Hi" );
printf("% 15s\n", "Hello" );
printf("% 15s\n", "Hello, world!" );
printf("</pre\>\");"
```

Here's the result:

Hi
Hello
Hello, world!

You can also leave out the zero or space and just specify a number, in which case printf() pads with spaces.

You are not limited to zeros and spaces. To use your padding character, insert an apostrophe ( ' ) followed by the character instead of the zero or space:

```
printf("*#-8s", "Hi" ); // Displays "Hi######"
```

If you want to add padding to the right rather than the left — so that the result is left-aligned rather than right-aligned — add a minus (-) symbol between the padding character and the width specifier:

```
printf("*#-8s", "Hi" ); // Displays "Hi######"
```

Padding behaves differently when using f or F to display a float. For more details, see "Specifying Number Precision."