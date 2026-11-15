an overview of all the important new features: https://www.php.net/releases/8.0, this was adopted for later versions p.e. https://www.php.net/releases/8.4.

![](bbox=[0.142, 0.148, 0.857, 0.489])

Figure 1.4 New Features in PHP 8.4

> **Tip**
> 
> If you want to delve deeper into the considerations and decisions of the PHP core developers behind the innovations in PHP 8 and earlier versions, you can find the function proposal RFCs, including the voting results, in the PHP wiki. For PHP 8, see https://wiki.php.net/rfc#php_80; for PHP 8.4, see https://wiki.php.net/rfc#php_84.

The following list provides an overview of the most important new features of PHP 8:

+   - PHP now includes a just-in-time (JIT) compiler. PHP is actually an interpreted programming language; that is, it is executed when called and is not converted into machine code before execution like a compiled programming language. The JIT compiler is a kind of middle ground. It is used to precompile code where appropriate and works closely with the code-caching system in PHP 8. In many applications, the reward for the effort is increased performance without functional disadvantages.
+   - The completely new match language construct is introduced as an often-simpler alternative to the switch case distinction. More on this in Chapter 5.
+   - Named parameters allow access to function and method parameters, regardless of the order. You can read more about this in Chapter 6.