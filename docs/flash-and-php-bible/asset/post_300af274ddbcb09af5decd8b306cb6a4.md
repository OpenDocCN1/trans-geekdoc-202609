
## Acknowledgments

I would like to thank Laura Sinise for helping me to get started. This book would not have been possible without the following people: Senior Acquisitions Editor, Stephanie McComb; Project Editor, Beth Taylor; Copy Editor, Kim Heusel; Technical Editor, Navid Mitchell; and Mary Keefe. I would also like to thank my friends Colin, Philip, Brooke, Frank, Jimmy and Daz and my cousin Teisha for their huge amount of support. And lastly, I would like to thank my family for their understanding and patience while I was locked away in my office during all hours of the night.

## Contents at a Glance

- About the Author . . . . . . . . . . . . . . . . . . . . . . . . . . . . . v
- Foreword . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . vii
- Acknowledgments . . . . . . . . . . . . . . . . . . . . . . . . . . . . . ix
- Introduction . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . xix

## Part I: Understanding the Basics . . . . . . . . . . . . . . . . 1

- Chapter 1: Getting Started with Flash and PHP . . . . . . . . . . . . . . 3
- Chapter 2: Exploring Flash and PHP . . . . . . . . . . . . . . . . . . . . 37
- Chapter 3: Getting Connected . . . . . . . . . . . . . . . . . . . . . . . 63
- Chapter 4: Working with Data . . . . . . . . . . . . . . . . . . . . . . . . 85
- Chapter 5: Interacting with the User . . . . . . . . . . . . . . . . . . . . 99
- Chapter 6: Working with Cookies . . . . . . . . . . . . . . . . . . . . . 113

## Part II: Developing Interactive Content . . . . . . . . . . . . . . 125

- Chapter 7: Maintaining Security while Working with User Input . . . . . . 127
- Chapter 8: Using Sockets . . . . . . . . . . . . . . . . . . . . . . . . . . 153

## Part III: Extending Flash and PHP . . . . . . . . . . . . . . . . 189

- Chapter 9: Working with Third-Party Libraries . . . . . . . . . . . . . . . 191
- Chapter 10: Using Object-Oriented Programming . . . . . . . . . . . . . . 219

## Part IV: Developing Applications . . . . . . . . . . . . . . . . 237

- Chapter 11: Developing Basic Applications . . . . . . . . . . . . . . . . . 239
- Chapter 12: Developing Real-World Applications . . . . . . . . . . . . . . 289
- Chapter 13: Using Advanced Real-World Applications . . . . . . . . . . . . 335
- Chapter 14: Debugging Applications . . . . . . . . . . . . . . . . . . . . . 381

## Part V: Server, Application, and Database Maintenance . . . . . . 393

- Chapter 15: Maintaining an Application . . . . . . . . . . . . . . . . . . . 395
- Chapter 16: Maintaining a Scalable and More Efficient Server . . . . . . . 405
- Chapter 17: Building Complete Advanced Applications . . . . . . . . . . . 429

- Index . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 487

![](img/d9d48cd53eee0fbc1ebc363c322fac2c_12_0.png)

- About the Author . . . . . . . . . . . . . . . . v
- Foreword . . . . . . . . . . . . . . . . vii
- Acknowledgments . . . . . . . . . . . . . . . . ix
- Introduction . . . . . . . . . . . . . . . . xix

## Part I: Understanding the Basics . . 1

### Chapter 1: Getting Started with Flash and PHP . . . . . . . . . . . . . . . . 3

- Adding Apache to a Web Server . . . . . . . . . . . . . . . . . 3
- Installing Apache for Windows . . . . . . . . . . . . . . . . . . . . . . . 4
- Installing Apache for UNIX . . . . . . . . . . . . . . . . . . . . . . . . 9
- Modifying Apache for Windows and UNIX . . . . . . . . . . . . . . . . 13
- Installing MySQL . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 14
- Installing MySQL for Windows . . . . . . . . . . . . . . . . . . . . . 14
- Installing MySQL for UNIX . . . . . . . . . . . . . . . . . . . . . . . . . 25
- Protecting MySQL . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 26
- Setting up PHP on the Web Server . . . . . . . . . . . . . . . . . . . . . . 27
- Installing PHP for Windows . . . . . . . . . . . . . . . . . . . . . . . 27
- Installing PHP for UNIX . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 33
- Summary . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 35

### Chapter 2: Exploring Flash and PHP . . . . . . . . . . . . . . . . 37

- Introduction to the Web Server . . . . . . . . . . . . . . . . . . . . . . . 37
- Working with .htaccess files . . . . . . . . . . . . . . . . . . . . . . . . 37
- Protecting your content . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 38
- Gathering information about Apache . . . . . . . . . . . . . . . . . . . . . 40
- Using custom error documents . . . . . . . . . . . . . . . . . . . . . . . . . 42
- Exploring the Basics of PHP . . . . . . . . . . . . . . . . . . . . . . . . . . 47
- Understanding variables . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 47
- Working with functions . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 49
- Understanding control structures . . . . . . . . . . . . . . . . . . . . . . 51
- Using type checking in PHP . . . . . . . . . . . . . . . . . . . . . . . . . . . . 56

## Contents

- Exploring the Basics of MySQL .................................................... 57
- Using statements .................................................................... 57
- Conditions ............................................................................ 58
- Exploring Flash ...................................................................... 59
- Flash IDE .............................................................................. 59
- Alternative editors ................................................................ 61
- Flash-enabled devices ............................................................ 62
- Moving forward ...................................................................... 62
- Summary ............................................................................... 62

### Chapter 3: Getting Connected

- Understanding Communications in Flash .................................... 63
- Determining the status of PHP ................................................ 64
- Working with various connection types .................................... 65
- Connecting Flash to PHP ........................................................ 69
- Connecting PHP to MySQL ...................................................... 73
- Determining the status of MySQL ............................................ 73
- Connecting to MySQL ............................................................ 74
- Bringing it all together ........................................................ 77
- Summary .............................................................................. 84

### Chapter 4: Working with Data

- Loading Data in Flash ............................................................ 85
- Understanding the classes used to load data ............................ 86
- Putting it all together .......................................................... 87
- Handling Loaded Data ............................................................ 88
- One-way loading .................................................................... 88
- Two-way loading .................................................................... 88
- Loading XML in Flash ............................................................. 89
- Working with XML in PHP ........................................................ 92
- Loading XML .......................................................................... 92
- Sending XML .......................................................................... 93
- Loading Images Using PHP ....................................................... 95
- Setting up the image loader .................................................... 96
- Summary .............................................................................. 98

### Chapter 5: Interacting with the User

- Form Development Using Flash .................................................. 99
- Creating a Contact Form ........................................................ 101
- Calling the PHP ...................................................................... 103
- Contact form event handlers .................................................... 103
- Mailing in PHP ....................................................................... 105
- Login Module in Flash ............................................................ 106
- Code skeleton ........................................................................ 106
- Login event handlers ............................................................... 107
- Server integration for login module .......................................... 110
- Summary .............................................................................. 111
