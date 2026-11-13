| Function | Return Value | Action |
| :--- | :--- | :--- |
| base_convert(string number, int frombase, int tobase) | string | Converts a number in a string from any base smaller than or equal to 36 to any base smaller than or equal to 36 |
| _format(float number [, int num_decimal_places [, string dec_seperator, string thousands_separator]]) | string | Formats a number with grouped thousands |
| fmod(float x, float y) | float | Returns the remainder of dividing x by y as a float |

| Function | Return Value | Action |
| :--- | :--- | :--- |
| srand([int seed]) | void | Seeds the random-number generator |
| mt_srand([int seed]) | void | Seeds the Mersenne Twister random-number generator |
| rand([int min, int max]) | int | Returns a random number |
| mt_rand([int min, int max]) | int | Returns a random number from the Mersenne Twister |
| getrandmax(void) | int | Returns the maximum value a random number can have |
| mt_getrandmax(void) | int | Returns the maximum value a random number from the Mersenne Twister can have |