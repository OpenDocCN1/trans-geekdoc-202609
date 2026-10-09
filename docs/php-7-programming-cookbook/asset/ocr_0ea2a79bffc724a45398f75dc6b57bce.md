# How it works...

It is considered best practice to place all logically related functions into a separate PHP file. Create a file called chap_03_developing_functions_library.php and place these functions (described previously) inside:

+   - someName()
- someOtherName()
- someInfinite()
- someDirScan()
- someTypeHint()

This file is then included in the code that uses these functions.

```
include (__DIR__ . DIRECTORY_SEPARATOR . 'chap_03_developing_functions_library.php');
```

To call the someName() function, use the name and supply the parameter.

```
echo someName('TEST');    // returns "INIT" and also TEST"
```

You can call the someOtherName() function using one or two parameters, as shown here:

```
echo someOtherName(1);     // returns  1
echo someOtherName(1, 1);  //  returns 2
```

The someInfinite() function accepts an infinite (or variable) number of parameters. Here are a couple of examples calling this function:

```
echo someInfinite(1, 2, 3);
echo PHP_EOL;
echo someInfinite(22.22, 'A', ['a' => 1, 'b' => 2]);
```