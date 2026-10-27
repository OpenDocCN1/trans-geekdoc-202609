Finally, unit testing can save money by reducing the number of critical bugs that emerge. By having developers write tests, especially beforehand, they can build in security tests, meaning that their code must comply with the security requirements before the product ships. If new security bugs are introduced, the code will fail the unit tests, alerting you to potentially seriously dangerous bugs before they are discovered by accident or in the wild.

By employing the strategies in the last section, you can also point out that unit testing does not necessarily require a significant outlay of time or capital to accomplish. Instead, by writing unit tests incrementally against the code base you already have, and writing them against new functionality that you are incorporating, you can show that unit testing can start right away, and incorporate future products and releases, without needing to write tests for your existing application's code.

# Unit Testing Improves the Quality of Software

While we briefly touched on this in the section on saving money, unit testing improves software quality. Managers typically care about quality almost as much as they care about saving money; the end result is that you should be able to make a solid case for the quality of software being improved through the use of unit testing.

Software quality is essentially a function of two things: first, how well the software meets the needs of the user, and secondly, how many bugs that user reports to the developer. There are some bugs that a user reports that will never be caught by unit tests. For example, user interface bugs or usability bugs will always be filed. However, bugs like "submitting the form doesn't change the values" are things that you can test and resolve before the software ships.

It is well known that users hate buggy software products; they refuse to use them, or mock them mercilessly. Microsoft learned this with the release of Microsoft Word; the release was terrible, full of bugs, and users hated it.

When your product is full of bugs, your users will hate that product. The end result is that they will replace it, if they are able. Do not let that happen to you. By writing unit tests as bug reports come in and ahead of the bug reports, you will have the best opportunity to prevent bugs from being built into your system. You will be able to