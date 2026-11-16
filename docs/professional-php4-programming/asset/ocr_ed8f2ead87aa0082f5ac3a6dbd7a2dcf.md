# Internationalization

Internationalization is the process of preparing a program to be translated into another language. As internationalization is an awfully long word to type, it's normally shortened to **i18n** (there are 18 characters between the first "i" and the last "n").

Programmers take care of internationalization by adapting the code in their scripts. The programmers don't do the translation, but instead make it easy for others to do so. There are sets of standards that make programming easier:

+   - Character sets and encoding
+   - User interface parameters, like date and currency format
+   - Character input for characters not available on the keyboard
+   - Message display standards, for example, error messages. We will not deal with them here

Before beginning to code an internationalized PHP application, we should be familiar with i18n. It is extremely difficult to allow for other cultures and languages in an application after the basic design and coding is finished, so it should definitely be a consideration at the design stage.

# Localization

Localization is shortened to **l10n**. The process of translating a script to a different language, often done by individual translators, is known as localization. As cultural domain experts they apply linguistic and visual conventions associated with the use of software in their target region. Also, they need to be experts in the source language, its idioms, and the conventions associated with it.

There is a special case of localization that enables the support of a pre-determined set of languages, called **multi-lingualization**. In this case, we are not dealing with a single language, but with a set of possibly related languages supported by the operating system, the web browser, or the web server.

We need a **locale** to localize the script. A locale holds the set of values determining language, region, character set, encoding, date, and currency format. For example, a locale might represent dates as DD/MM-YYYY instead of MM/DD/YYYY. The idea is that when you switch to another locale, all the parts of the program that deal with output should change to the new language. Think of a locale as a special kind of database that contains the information we need to display and format messages in a foreign language. We will have one such "database" for each language our application supports, and by using the correct one, the program can present itself in different languages.

# Native Language Support

Native language support (NLS) is achieved by writing internationalization routines and enabling localization support. NLS is the end goal, which is achieved through internationalization and localization and refers to a script's ability to support a user's native languages.

An application that runs in an international environment must not have built-in assumptions about:

+   - Locale-specific and culture-specific conventions