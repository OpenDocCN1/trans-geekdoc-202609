# Cost

Over the useful life of a piece of software, significantly more time will be spent maintaining, modifying, testing, and documenting it than was originally spent writing it. If you are writing commercial code, you should attempt to limit the number of lines in use within the organization. One of the most practical ways to achieve this is to reuse code already in use of writing a slightly different version of the code for a new task. Less code means lower costs. If existing software meets the requirements of the new project, the cost of using existing software is almost always less than the cost of developing an equivalent product. This applies whether you are buying a product or using an open-source project. Tread carefully, though if existing software almost meets your requirements.

Modifying existing code can be more difficult than writing new code. If you are working with an open-source project, look for one that has a plugin architecture, where you can easily access its functionality. Otherwise, if you must change the way it works, you will need to either work on updating your changes to the main project (preferably), or maintain your own fork (not recommended).

# Reliability

If a module of code is in use somewhere in your organization, it has presumably already been tested. If this module contains only a few lines, there is a possibility that, if you rewrite it, you will overlook either something that the original author incorporated or something was added to the original code after a defect was found during testing. Existing, mature code is usually more reliable than fresh, "green" code.

The exception to this is if the code module is old enough to be considered legacy code. Sometimes older libraries develop a certain amount of craft through growth over time. In this case, you may consider developing a replacement that can be used throughout your organization.

# Consistency

The external interfaces to your system, including both user interfaces and interfaces to outside systems, should be consistent. Writing new code consistent with the way other parts of the system function takes will care and deliberate effort. If you are reusing code that runs another part of the system, your functionality will automatically be consistent.

On top of these advantages, reusing code is less work for you, as long as the original code is modular and well written. While you work, try to recognize sections of your code that you might be able to call on in the future.

# Using require() and include()

PHP provides two very simple, yet useful statements, to allow you to reuse code. Using a require() or include() statement, you can load a file into your PHP script. The file can contain anything you would normally have in a script including PHP statements, text, HTML tags, PHP functions, or PHP classes.