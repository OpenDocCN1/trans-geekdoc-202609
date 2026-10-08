```
<h1><?php getgettext("WELCOME_TEXT"); ?></h1>
<h2><?php getgettext("CHOOSE_LANGUAGE"); ?></h2>
<ul>
<li><a href="<?php echo \$_SERVER['PHP_SELF'];?&amp;lang=en_US&quot;">en_US</a></li>
<li><a href="<?php echo \$_SERVER['PHP_SELF'];?&amp;lang=ja_JP&quot;">ja_JP</a></li>
</ul>
<body>
</html>
```

Once you have a handle on the basics of application internationalization and localization, if you are developing an application used by speakers of many different languages, I recommend looking into a GNU-based localization framework and crowdsourced translation services to handle the creation of your PO files (unless you have a plethora of native language speakers at your disposal or a lot of money to spend on translation services).

# Further Reading

Internationalization and localization is a huge topic, and we only covered the most basic of the concepts in this brief chapter. For example, we didn't talk about localizing numbers, dates, and currency using PHP, but all of these are possible using built-in functionality such as the `strtotime()` function for locale-aware time display, or by extending functionality to create helper classes and functions to suit your needs. You can also take a look at PHP frameworks that handle all of this to evaluate their usefulness to your project or to see how those developers build the underlying functionality. Rich examples can be found in Zend Framework (http://framework.zend.com/manual/current/en/modules/zend.i18n.translating.html) and Symfony (http://symfony.com/doc/current/book/translation.html).

# Next

One of the many useful things you can do with PHP is to create images on the fly. Chapter 21, "Generating Images," discusses how to use the image library functions to achieve some interesting and useful effects.