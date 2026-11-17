```
all:
.settings:
i18n: true
```

# Using the Translation Helper

Let's say that you want to create a website in English and French, with English being the default language. Before even. So the user interface translation relies on a dictionary file.

The dictionary files are written in the XML Localization Interchange File Format (XLIFF), named according to the pattern messages.[language code].xml, and stored in the application i18n/ directory.

XLIFF is a standard format based on XML. As it is well known, you can use third-party translation tools to reference all text in your website and translate it. Translation firms know how to handle such files and to translate an entire site just by adding a new XLIFF translation.

> In addition to the XLIFF standard, symfony also supports several other translation back-ends for dictionaries: gettext, MySQL, and SQLite. Refer to the API documentation for more information about configuring these back-ends.

Listing 13-14 shows an example of the XLIFF syntax with the messages.fr.xml file necessary to translate Listing 13-13 into French.

Listing 13-14 - An XLIFF Dictionary, in frontend/i18n/messages.fr.xml