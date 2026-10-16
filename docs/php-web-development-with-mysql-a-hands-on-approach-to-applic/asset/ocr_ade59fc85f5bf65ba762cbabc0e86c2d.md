# 8. VERIFYING VARIABLES AND TYPE CHECKING

Listing 8.4.

```
1. <?php
2.
3. class Car {}
4.
5. $boolean = true;
6. $integer = 123;
7. $integer_negative = -13;
8. $float_double = 12.35;
9. $string = "Hello World";
10. $array = array('one', 'fish', 'two', 'fish', 'red', 'fish');
11. $object = new Car();
12. $null = NULL;
13. ?>
14.
15. <table border='1px solid;'>
16.     <tr>
17.         <th>Type</th>
18.         <th>Value</th>
19.         <th>gettype() response</th>
20.     </tr>
21.     <tr>
22.         <td>Boolean</td>
23.         <td><?= $boolean ?></td>
24.         <td><?= gettype($boolean); ?></td>
25.     </tr>
26.     <tr>
27.         <td>Integer</td>
28.         <td><?= $integer ?></td>
29.         <td><?= gettype($integer); ?></td>
30.     </tr>
31.     <tr>
32.         <td>Integer Negative</td>
33.         <td><?= $integer_negative ?></td>
34.         <td><?= gettype($integer_negative); ?></td>
35.     </tr>
36.     <tr>
37.         <td>Float</td>
38.         <td><?= $float_double ?></td>
39.         <td><?= gettype($float_double); ?></td>
40.     </tr>
41.     <tr>
42.         <td>String</td>
43.         <td><?= $string ?></td>
44.         <td><?= gettype($string); ?></td>
45.     </tr>
46.     <tr>
47.         <td>Array</td>
48.         <td><?= implode(',', $array); ?></td>
49.         <td><?= gettype($array); ?></td>
50.     </tr>
```