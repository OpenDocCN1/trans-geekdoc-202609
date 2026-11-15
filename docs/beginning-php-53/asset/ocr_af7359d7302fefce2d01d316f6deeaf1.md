# Padding the Output

You can add characters to the left (by default) or the right of the formatted argument in order to pad it out to a fixed width. This is useful if you want to add leading zeros to a number, or horizontally align many strings by padding with spaces.

To add padding you insert a _padding specifier_ into your conversion specification, before the type specifier. The padding specifier consists of either a zero (to pad with zeros) or a space character (to pad with spaces), followed by the number of characters to pad the result out to. `printf()` then adds as many zeros or spaces as required to make the result the correct width.

For example, the following code displays various numbers, using leading zeros where necessary to ensure the result is always six digits long:

```
printf( "%06d<br/>", 123 ); // Displays "000123"
printf( "%06d<br/>", 4567 ); // Displays "004567"
printf( "%06d<br/>", 123456 ); // Displays "123456"
```

The padding specifier can add characters where required, but it never truncates the output. So `printf( "%06d", 12345678 )` displays "12345678", not "345678".

This example pads various strings using leading spaces to ensure that they're right-aligned:

```
print "<pre>";
printf( "% 15s\n", "Hi" );
printf( "% 15s\n", "Hello" );
printf( "% 15s\n", "Hello, world!" );
print "</pre>";
```

Here's the result:

```
Hi
Hello
Hello, world!
```

You can also leave out the zero or space and just specify a number, in which case `printf()` pads with spaces.

You're not limited to zeros and spaces. To use your own padding character, insert an apostrophe ( ' ) followed by the character instead of the zero or space:

```
printf( "%'#8s", "Hi" ); // Displays "######Hi"
```

If you want to add padding to the right rather than the left — so that the result is left-aligned rather than right-aligned — add a minus (-) symbol between the padding character and the width specifier:

```
printf( "%'-#8s", "Hi" ); // Displays "Hi######"
```

Padding behaves differently when using `f` or `F` to display a float. For more details, see “Specifying Number Precision.”