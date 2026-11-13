object-oriented programming language, it does not use the concept of global variables.
However, by using the static or static final keywords, the variables can have all the
properties of global variables.

```
Python
text = "hello "
def hello():
    # text is a global variable
    global text
    # text is concatenated with a new text value
    text = text + "world"
# Driver code
hello()
print(text)
```

In this example, the text is a global variable, which means that, by calling the hello
procedure, the content of the variable text is changed and, once it is printed, even if it is
printed outside the procedure, it will display the updated content: hello world.

> **Top tip!**
> When writing code, aim to preponderantly use local variables rather than global variables. Local
> variables are confined to the function or block in which they are declared, promoting encapsulation
> and modularity. This makes functions self-contained and easier to understand, test and debug.
> Global variables can be modified by any part of the code, leading to unintended side effects that
> can make the program behaviour difficult to predict and debug. Local variables prevent such side
> effects by limiting the scope of variable modifications.

# REVIEW QUESTIONS

1 Trace the following program to determine its output.

```
Java
static String student = "Bob";
public static void changeOfName(String st) {
    st = "Jim";
    System.out.println("Student inside the method: "+st);
}
public static void main(String[] args) {
    changeOfName(student);
    System.out.println("Student outside the method: " + student);}
```