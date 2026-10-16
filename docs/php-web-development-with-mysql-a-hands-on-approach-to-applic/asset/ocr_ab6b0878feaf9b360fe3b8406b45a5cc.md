In this example, we would probably want to name this file Radio.php.

Class names follow the same rules as variable names. However, unlike variable names, class names are not case-sensitive. In practice, the coding standard for naming classes is to start the first word with an upper-case letter and to start every word in the class name with an upper-case letter (i.e., CustomerAccount). This convention is known as “StudlyCaps.”

One thing to keep in mind about classes is that they are like blueprints or recipes for PHP objects. We explore this later when discussing the difference between an instance of a class—known as an object—and the class definition itself.

# Properties

Of course, we need to add data to our classes. In some programming languages, these are called instance or class member variables. In PHP, we call them “properties.”

Using our Radio example, here are a few properties:

```
<?php
class Radio
{
    private $powered;  // true or false
    private $volume;   // 0 - 10
    private $channel;  // 535kHz - 1700kHz, 87.5MHz - 108MHz
}
```

> On Class Design
> 
> *As I mentioned previously, at the most basic level, a class should define what a program knows (its data) and what a program does (its functionality). Ideally, in object design, you want to think of your class as a single thing. In this case, we are modeling the concept of a radio in software. Before writing any code, think about how one would interact with our radio. Since this is a simple example, we need our radio to know (i.e., hold data for) whether it is on or off, its volume, and what channel or frequency it is set to. Likewise, we also need functionality to turn on and off the radio, set its volume, and change its channel or frequency. The properties and methods your class needs should be informed by your software requirements. We will fill this in when we talk about methods.*