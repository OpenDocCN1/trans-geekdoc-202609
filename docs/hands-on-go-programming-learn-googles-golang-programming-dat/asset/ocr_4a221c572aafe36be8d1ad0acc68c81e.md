```
i.m1()
i.m2()
fmt.Println("Assigning Address of St")
i = &St{}
i.m1()
i.m2()
}
```

The following will be the output for the above program:

**Assigning value of St**
**In m1 of St**
**In m2 of St**
**Assigning Address of St**
**In m1 of St**

**In m2 of St**

In the above code, we have implemented the ltr interface by defining the m1 and m2 methods with values receiver. In the main function, we have tried to assign both the value and address of St to an interface variable and it worked fine. We will not get a compilation error in this code.