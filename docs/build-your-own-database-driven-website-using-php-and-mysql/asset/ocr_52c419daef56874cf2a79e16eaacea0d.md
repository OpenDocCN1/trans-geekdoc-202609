The fact that these checkboxes submit into an array actually adds quite a measure of convenience to our code. In essence, what we’ll receive from the submitted form is either 1) an array of category IDs to add the joke to, or 2) nothing at all (if none of the checkboxes were checked). First let’s handle the latter, special case, by creating an empty array when we find that the `$cats` variable is empty:

```
if ($cats == "") $cats = array();
```

The array function that appears here is used to create a new array in PHP. The parameters that are passed to it become the elements of the array. Because we’re passing no parameters to it here, it’ll simply create an empty array.

Now that we’ve guaranteed that the `$cats` variable contains an array, we can use a loop to consider each category ID in the array in turn, and to insert the appropriate entry into the database. Since this array isn’t based on a database row, you might wonder how we can access the values in the array. After all, we previously retrieved an array value using its database column name (e.g. `$cat["Name"]`). In this case, our array was created simply by feeding a series of values into the same variable name. When this happens, PHP automatically assigns numerical labels or **indices** to the values in the array. For instance, the value of the first checkbox that was checked will be submitted first into the array and will be accessible as `$cat[0]`. That is, PHP assigns it an array index of 0. The second checkbox that is checked will have its value stored with an index of 1, accessible as `$cat[1]`. So if there are `n` checkboxes checked, then the value of the last checkbox will be in `$cat[n-1]`. By counting up through the array indexes as we proceed through a loop in our code, we can process the elements of this array one at a time.

But wait... what is `n`? We have no way of knowing in advance how many checkboxes will be checked, so how do we know when to stop counting? Well, there are two ways. The first is to use a PHP function called `count` that takes an array as a parameter and counts the number of elements in it. Here’s what our while loop would look like if we use this method:

```
$i = 0; // First index
while ($i < count($cats)) { // while we're not at the end
    // process $cats[$i]
    $i = $i + 1;
}
```

As you can see, this loop uses a **counter variable** (`$i`), that is, a variable that counts the number of times the loop has executed. The first time through the loop, it will have a value of 0, then at the end of the loop we’ll add 1 to it. Therefore, the second time through the loop it will have a value of 1, and so on. Within the loop, we can use this variable as the array index to pull a category ID out of the `$cats` array. The loop stops looping when `$i` reaches