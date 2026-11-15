The default value is then used each time the function is called without the respective value (see Figure 6.3). A default value can be a value or a constant. You can also set the default value to NULL—that is, no value. This means that an error does not occur if the parameter value is not set when the function is called, but the parameter itself is not set either.1 You can use this construct to simulate a type of *overloading*—that is, passing different numbers of parameters. However, this is really only an auxiliary construct.

![](bbox=[0.145, 0.22, 0.735, 0.325])

Figure 6.3 The Default Value Appears at the Top, the Transferred Value at the Bottom

> **Note**
> If you use more than one parameter, you must write the parameter(s) with default values at the end:
> 
> ```php
> function output($par1, $par2 = "Default2") {
>   echo "Parameter value 1: $par1<br />";
>   echo "Parameter value 2: $par2";
> }
> 
> output("Exclusive1");
> 
> This is logical if you remember that PHP needs to know which variable the passed parameter is to be used for.

# Flexible Number of Parameters

The default value is the only way to pass too few parameters to a function. You can pass too many parameters with the ... operator (*splat operator*). It is placed before the last parameter and takes all transferred parameters as an array.

The ... operator can only be used with the last parameter of a function. However, it is easily possible to insert one or more other parameters before it. These can also have default values.

> **Note**
> Passing too many parameters is often referred to as *overloading*. However, overloading in the object-oriented sense implies that different functions are available for different numbers of parameters. This is not the case.

1 Not set here means that a test with isset() fails. More on this follows in Section 6.19.