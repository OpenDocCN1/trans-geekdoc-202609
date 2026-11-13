```
```java
private static Scanner read;
public static void main(String[] args) {
  read = new Scanner(System.in);
  double purchaseValue, discount;
  discount=0;
  System.out.println("enter value of goods purchased: ");
  purchaseValue = read.nextDouble();
  if (purchaseValue>=100)
    discount = purchaseValue * 0.2;
  System.out.println("Your discount is: " + discount);
}
```
```

In this example, the purchaseValue and discount variables have been declared as double because they are meant to store an amount of money, which could be a decimal value.
As the discount is only calculated if the condition is met, we had to initialize it to 0 in the beginning, so there is a value to display if no calculation occurs. The indentation inside the IF statement in the Python below shows what instruction is going to be executed when the condition is met. In Java, the indentation is replaced by curly brackets and, if those are missing, then the next line will be interpreted as belonging to the selection statement. Therefore, the output statement will be run independently of the given condition, as it is not included in the IF statement.

```
```python
discount = 0
purchaseValue= float(input("Enter the value of your goods:"))
if purchaseValue>=100:
    discount = purchaseValue * 0.2
print("Your discount is ", discount)
```
```

In Python, there is no need to declare the variables, so only the discount variable is initialized to 0. However, the input value is converted to float, to ensure the user will enter a decimal number (integers are included into the range of decimal values). If the float conversion did not happen, the user's input would be a text, and this would throw an error when attempting to use it in calculations.

You can further expand this code and include a variable to store and display the due amount:

```
```java
double purchaseValue,toPay, discount;
toPay=0;
System.out.println("enter the value of your goods: ");
purchaseValue = read.nextDouble();
if (purchaseValue>=100) {
    discount = purchaseValue * 0.2;
    toPay = purchaseValue - discount;
}
System.out.println("You need to pay: " + toPay);
```
```