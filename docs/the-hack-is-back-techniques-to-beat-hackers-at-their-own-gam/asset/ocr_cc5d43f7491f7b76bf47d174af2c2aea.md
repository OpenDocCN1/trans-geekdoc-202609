uncovering hidden or forgotten files is an easy way to gain access to a system for an organization. Some additional fantastic resources on using ffuf are below:

+   - [http://ffuf.me/](http://ffuf.me/)
+   - [https://danielmiessler.com/study/ffuf/](https://danielmiessler.com/study/ffuf/)
+   - [https://coding.io/tools/ffuf/bounty/2020/09/17/everything-you-need-to-know-about-ffuf.html](https://coding.io/tools/ffuf/bounty/2020/09/17/everything-you-need-to-know-about-ffuf.html)

# ## Python Libraries

There are certain times when we need to create a tool for our specific situation. There will be scenarios where the implementation of a web application is in such a way that an existing tool does not exist for us to use. In these instances, we will need to create our own tool out of Python or some other programming language to attack the item effectively.

One of the great things about modern programming is how many open-source libraries are available. If you’re looking to complete some type of task, such as making an HTTP request or performing a specific type of hashing, chances are that someone else has already created a library that can complete these functions. These already written functions are easily integrated open-source libraries that can be accessed, saving countless amounts of time on your end. Using programs such as **pip**, we can install a library that has already written code to help perform a specific action and utilize it within our program. For example, the **requests** library helps simplify HTTP requests and create a much more manageable way to programmatically integrate with our needs.

The **pip** program uses the Python Package Index (PyPI) at [pypi.org](https://pypi.org). This is a location where many exceptional libraries are hosted along with links to their documentation. Updates are pushed to PyPI as well, where the **pip** program can be used to update the library as needed.

![](bbox=[0.107, 0.543, 0.894, 0.781])

**FIGURE 3.44**  [Pypi.org](https://pypi.org) website which hosts many useful Python libraries.

To download and install a library, the command **pip install requests** would be used to install the requests library. Pay attention to the requests page on Pypi as well, because this shows how to install the library via pip as well as high-level information about the library and links to the official documentation.