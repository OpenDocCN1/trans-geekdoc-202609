```
```solidity
pragma solidity ^0.5.0;

contract Test {
    struct Car {
        string make;
        string model;
        uint value;
    }
    Car car;

    function setCar() public {
        car = Car('Audi', 'A6', 5000000);
    }
    function getCarValue() public view returns (uint) {
        return car.value; // Accessing value from Struct Car using (.) operator
    }
}
```
```

**FIGURE 8.8**  Structs in Solidity.

application, then you would prefer to restrict the size selection to small, medium, and large. Therefore, eliminating the chances of erroneous input.

The code in Figure 8.9 illustrates the concept of enum in Solidity.

# 8.6.4.1  Enum Gotchas

+   a. Numbers are not accepted as a constant in an enum. And for booleans, the first letter must be capital (True or False).
+   
+   b. Enum identifies its End of Declaration by the closing curly bracket. A semicolon (;) is used to indicate the end of single-line instructions, and curly brackets ({}) are used to indicate the start or end of a set of instructions like functions, struct, modifiers, enums, and the contract itself. Therefore, we need not specify the End of Declaration with a semicolon.

# 8.6.5  STRINGS

The string data type is similar to an array of characters. Solidity sustains both single (’) and double quote (“) string literals. The “string” keyword can be used to declare a string variable type. Although it is recommended using byte-type literals compared to

```
```solidity
pragma solidity ^0.5.0;

contract Direction {
    enum DirectionChoices { GoLeft, GoRight, GoStraight, StandStill };
    function Direction()
    {
        choices = DirectionChoices.GoStraight;
    }
    function getChoice() returns (uint ch)
    {
        ch = uint256(choices);
    }
    DirectionChoices choices;
}
```
```

**FIGURE 8.9**  Enum in Solidity.