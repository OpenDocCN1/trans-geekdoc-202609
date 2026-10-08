When AverageTemperature is first used, PHP marks it internally as a string because it is assigned the value of a string literal. Setting the type to double causes the value to be reevaluated. If you check the output, youwill notice that some information is lost as a result. The text following the number is dropped off because it has no meaning in the context of a floating-point number. Likewise, when the script sets the type to integer, the fractional part of the number is dropped. When we change the type back to string, the previous information is gone.

In contrast to, the use of type conversion commands preserves the value of the variable because it does the conversion on the fly. The inside variable are not changed.

The settype function is described in full in Chapter 9, "Data Functions," as are the conversion functions intval, strval, and doubleval . Casts, identical in operation to type conversion functions, take the form of an expression with a datatype in parentheses. Valid casts are (boolean), (integer), (string), (double), (array) , and (object). Arrays and objects are discussed in Chapters 5 and 6.

Another type of data sometimes discussed in this text is the bitfield. Rather than a type exactly, it is a way of viewing an integer. Instead of a single value, it is viewed as a sequence of ones and zeroes. Bitfields are discussed later in this chapter in relation to bitwise operators.

# Variable Creation and Scope

Although you've seen variables in the previous pages, you may wonder what they are exactly. Part of a computer is called RAM, or random access memory. This is a volatile medium for storing information. That is, it all disappears when you shut off the machine. The computer sees this memory as a long string of single characters, or bytes, each numbered. In PHP, however, you cannot actually get to memory at this level. You must use a variable. You provide a name, and PHP takes care of matching the name to physical memory.

+   Listing 2.2 Experimenting with Scope