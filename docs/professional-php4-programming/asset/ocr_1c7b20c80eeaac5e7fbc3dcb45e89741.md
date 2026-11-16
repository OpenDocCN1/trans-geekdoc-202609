# GNU Gettext

When the GNU project grew beyond the boundaries of Canada and the US, programmers from countries outside the English-speaking world wanted to translate their GUIs, message catalogues, and web pages into other languages. There arose the need for a clever way of synchronizing translations. They wanted to avoid working multilingual programmers too hard, but at the same time, make it easy for translators to do their job.

They came up with the Gettext library, and it has since become the standard solution for internationalizing open source programs. It has plenty of tools that help in writing the .po files which hold the strings. We will talk more about this later in the chapter.

# The Basics

gettext() is the method used by the Gettext library for internationalization. The idea behind gettext() is that if we have a string that needs to be translated, Gettext will search for a translation for that string in a database (the .po file). If gettext() finds the translation, it uses this, else, it uses the original string. When gettext() looks for a translation, it uses the original string as the lookup key. This means that the string does not have to be translated multiple times.

This means that nothing breaks when the programmer adds new strings to the script. Since the text the programmer adds is usually in English, translations will just revert.

> SuSE Linux distribution used to default to German whenever system messages had been left un-translated. This used to infuriate English-speaking users, but was nothing but the effect of gettext() default.

To use gettext() in the code, pass the string to be translated as an argument to the gettext() function, like this:

```
print("Hello World!"); // Before
print(gettext("Hello World!"); // After
```

Since gettext() takes a long time to write, the function call can be shortened by using the underscore "_" character. It can be used like this:

```
print(_("Hello World!"));
```

When using arrays to hold the translation, we get an empty string if the string isn't present, and perhaps a warning about a missing index in the array. The result is that the Gettext-way of doing things is more robust.

# xgettext and Helpers

Once the strings in the program are marked with the _() function or gettext() code, they have to be extracted so that they can be translated. This can be done with xgettext, which is part of the Gettext package.