
Finally, polyinstantiation means “many instances,” two instances (specific objects) with the same names that contain different data. This may be used in multilevel secure environments to keep top secret and secret data separate, for example. See [Chapter 4](#Ch004_107-223_B9780443187346000076_1.xhtml), Domain 3: Security Architecture and Engineering for more information about polyinstantiation. [Fig. 9.11](#Ch009_459-508_B9780443187346000088.xhtml#f0060) shows polyinstantiated Addy objects: two objects with the same name but different data. Note that these are two separate objects. Also, to a secret-cleared subject, the Addy object with secret data is the only known Addy object.

![Fig. 9.11 Polyinstantiation.](images/B9780443187346000088/f09-11-9780443187346.jpg)

[Fig. 9.11](#Ch009_459-508_B9780443187346000088.xhtml#B-f0060) Polyinstantiation.

Here is a summary of Object-Oriented Programming concepts illustrated by Addy:

*   **Object**: `Addy`
*   **Class**: `Mathematical operators`
*   **Method**: `Addition`
*   **Inheritance**: `Addy` inherits an understanding of numbers and math from his parent class `Mathematical operators`. The programmer simply needs to program `Addy` to support the method of addition
*   **Example input message**: `1 + 2`
*   **Example output message**: `3`
*   **Polymorphism**: `Addy` can change behavior based on the context of the input, overloading the `+` to perform addition, or concatenation, depending on the context
*   **Polyinstantiation**: Two `Addy` objects (secret and top secret), with different data

#### Coupling and Cohesion

Coupling and cohesion are two concepts used to describe objects. A highly coupled object (such as `Addy`) requires lots of other objects to perform basic jobs, like math. An object with high cohesion is far more independent: it can perform most functions independently. Objects with high coupling have low cohesion, and the reverse is also true: objects with low coupling have high cohesion.

`Addy` is highly coupled and has low cohesion: he must delegate any message that does not contain a `+`. Imagine another object called `Calculator`, which can add, subtract, multiply, divide, perform square roots, exponentiation, etc. `Calculator` would have high cohesion and low coupling.

#### Learn by Example: Managing Risk Though Objects

Objects are designed to be reused: this lowers development costs. Objects can also lower risk. Much like strong encryption such as `AES`, the longer an object remains in secure use, the more assurance we have that the object is truly secure. Like encryption algorithms, as time passes, and countless attacks prove unsuccessful, the object demonstrates its real-world strength.

Let us assume your company has been selling information security books online for the past 5 years. Your website allows users to choose a book, such as *TCP/IP Illustrated* by W. Richard Stevens, and enter their name, address, and credit card billing information. Credit card transactions are risky: risks include disclosure of customer’s PII, as well as risk of credit card fraud; stolen cards used to fraudulently purchase books.

The website is programmed in an object-oriented language. It includes a credit card processing object called `CCValidate`, first written 5 years ago. The input message is the credit card number and expiration date entered by the customer. The output message is binary: “approved” or “denied.”

The `CCValidate` object hides the complexity of what is happening in the background after the input message of credit card number and expiration date are entered. It performs the following methods:

1.  The object has variable buffers for the credit card number that perform bounds checking.
2.  The object ensures that the input message is the proper length and contains the proper types of characters in each field.
    a.  In the case of a `MasterCard®`, 16 numbers (the credit card number), followed by the date (two-digit month followed by a four-digit year).
    b.  Any input message that does not meet these criteria is immediately rejected.
3.  The object ensures the expiration date is in the future.
    a.  Any input message that does not meet this criterion is immediately rejected.
4.  The object then evaluates the format and self-checking digits within the entered credit card number.
    a.  Valid `MasterCard®` numbers start with 51–55, and have 16 digits.
    b.  They must also contain proper self-checking digits.
        i.  See [http://web.eecs.umich.edu/~bartlett/credit_card_number.xhtml](http://web.eecs.umich.edu/~bartlett/credit_card_number.xhtml) for more information
    c.  Any input message that does not meet these criteria is immediately rejected.
5.  The object then sends a message to the proper credit card company server, checking to see if the card is valid and contains enough balance to make a purchase.
    a.  The credit card company sends a return message of “accept” or “denied,” which the credit card object sends to the Web server as a message.

As `CCValidate` is used, bugs may be discovered and fixed. Improvements may be identified and coded. Over time, the object matures and simply does its job. It is attacked on the Internet; attackers launch buffer overflow attacks and insert garbage numbers, and the object performs admirably.

If a new site comes online, the programmers should not create a new credit card validating object from scratch: reinventing the wheel is too risky. They should manage their risk by locating and using a mature object that has stood the test of time: `CCValidate`.

### Object Request Brokers

As we have seen previously, mature objects are designed to be reused: they lower risk and development costs. *Object Request Brokers* (ORBs) can be used to locate objects: they act as object search engines. ORBs are *middleware*: they connect programs to programs. Common object brokers included `COM`, `DCOM`, and `CORBA`.

#### COM and DCOM

Two object broker technologies by Microsoft are *COM* (*Component Object Model*) and *DCOM* (*Distributed Component Object Model*). `COM` locates objects on a local system; `DCOM` can also locate objects over a network.

`COM` allows objects written with different OOP languages to communicate, where objects written in `C++` send messages to objects written in `Java`, for example. It is designed to hide the details of any individual object and focuses on the object’s capabilities. `COM+` is an extension to `COM`, introduced in Microsoft Windows 2000. `ActiveX` is discussed in [Chapter 4](#Ch004_107-223_B9780443187346000076_1.xhtml), Domain 3: Security Architecture and Engineering.

`DCOM` is a networked sequel to `COM`. `DCOM` includes *Object Linking and Embedding* (OLE), a way to link documents to other documents.

Both `COM` and `DCOM` are being supplanted by `Microsoft.NET`, which can interoperate with `DCOM`, but offers advanced functionality to both `COM` and `DCOM`.

#### CORBA

*Common Object Request Broker Architecture* (CORBA) is an open vendor-neutral networked object broker framework by the Object Management Group (OMG). `CORBA` competes with Microsoft’s proprietary `DCOM`. `CORBA` objects communicate via a message interface, described by the *Interface Definition Language* (IDL). See [http://www.corba.org](http://www.corba.org) for more information about `CORBA`.
