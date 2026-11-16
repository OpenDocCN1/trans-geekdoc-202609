Starting from the top, the JavaScript function subtotal() takes a form, which is a place to put the answer and an array of numbers to add.

Although JavaScript supports decimals, it doesn't support arbitrary precision. Therefore, because you'd like dollars down to the penny (as in $9.99), you must multiply everything by 100. Do the math, round the result, and then divide by 100.

Therefore, by adding 0.01 to 9.98, multiply everything by 100: 1.0 and 998.0. Do the addition: 999.0. Round the result, 999, and divide by 100: 9.99. Yes, it looks as though it'll be a pain.

The next few functions deal with totaling up columns in each section (Lodging, Meals, Transportation, and so on), vertically totaling each amount per day. Finally, daycalc() is called by each of the “cells”:

```
function subday (thisForm, totalcell, prefix, maxindex) {
    var cellArray = new Array (maxindex);
    for (var i=0; i < maxindex; i++) {
        cellArray[i] = thisForm[prefix+i].name;
    }
    return subtotal(thisForm, totalcell, cellArray);
}
```

```
function subweek (thisForm, totalcell, prefix, postfix) {
    return subtotal (thisForm, totalcell,
        new Array (prefix+'sun'+postfix, prefix+'mon'+postfix,
            prefix+'tue'+postfix, prefix+'wed'+postfix,
            prefix+'thr'+postfix, prefix+'fri'+postfix,
            prefix+'sat'+postfix));
}
```

```
function daycalc (thisForm, day, code, thisindex, maxindex) {
    subday (thisForm, code+"_"+day+"_sub", code+"_"+day+"_", maxindex);
    subweek (thisForm, code+"_week_sub"+thisindex, code+"_", '_'+thisindex);
    subday (thisForm, code+"_week_sub", code+"_week_sub", maxindex);
    totalcalc (thisForm);
    return true;
}
```

The function daycalc() is called from each cell that accepts user input in the HTML form in such a manner:

```
onkeyup="return daycalc(this.form, 'sun', 'lodging', '0', 3)"
```

Remember that the screen is generated from your expense meta-array:

```
array('meals_breakfast', 'meals_lunch', 'meals_dinner', 'meals_tips',
    'meals_entertainment')
```

However, JavaScript has no knowledge of PHP, or Smarty, or whatever else you’re using in the back end, so you must be explicit and tell JavaScript which cell you are working with, as well as how many cells need to be subtotaled. These, respectively, are the last two arguments in the daycalc() function call: '0' is the current row and '3' signifies the maximum number of rows that need to be vertically subtotaled in the subday function.