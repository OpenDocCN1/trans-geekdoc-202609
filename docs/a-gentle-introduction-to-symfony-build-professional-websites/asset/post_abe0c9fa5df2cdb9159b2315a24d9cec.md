
Another way to organize translation dictionaries is to split them by module. Instead of writing a single messages.XX.xml file for the whole application, you can write one in each modules/[module_name]/i18n/ directory. It makes modules more independent from the application, which is necessary if you want to reuse them, such as in plug-ins (see Chapter 17).

As updating the i18n dictionaries by hand is quite error prone, symfony provides a task to automate the process. The i18n:extract task parses a symfony application to extract all the strings that need to be translated. It takes an application and a culture as its arguments:

```
$ php symfony i18n:extract frontend en
```

By default, the task does not modify your dictionaries, it just outputs the number of new and old i18n strings. To append the new strings to your dictionary, you can pass the --auto-save option:

```
$ php symfony i18n:extract --auto-save frontend en
```

You can also delete old strings automatically by passing the --auto-delete option:

```
$ php symfony i18n:extract --auto-save --auto-delete frontend en
```

> The current task has some known limitations. It can only work with the default messages dictionary, and for file based backends (XLIFF or gettext), it only saves and deletes strings in the main apps/frontend/i18n/messages.XX.xml file.

## Handling Other Elements Requiring Translation

The following are other elements that may require translation:

- Images, text documents, or any other type of assets can also vary according to the user culture. The best example is a piece of text with a special typography that is actually an image. For these, you can create subdirectories named after the user culture:

```
<?php echo image_tag($sf_user->getCulture().'/myText.gif') ?>
```

- Error messages from validation files are automatically output by a __(), so you just need to add their translation to a dictionary to have them translated.

- The default symfony pages (page not found, internal server error, restricted access, and so on) are in English and must be rewritten in an i18n application. You should probably create your own default module in your application and use __() in its templates. Refer to Chapter 19 to see how to customize these pages.

## Handling Complex Translation Needs

Translation only makes sense if the __() argument is a full sentence. However, as you sometimes have formatting or variables mixed with words, you could be tempted to cut sentences into several chunks, thus calling the helper on senseless phrases. Fortunately, the __() helper offers a replacement feature based on tokens, which will help you to have a meaningful dictionary that is easier to handle by translators. As with HTML formatting, you can leave it in the helper call as well. Listing 13-16 shows an example.

### Listing 13-16 - Translating Sentences That Contain Code

```
// Base example
Welcome to all the <b>new</b> users.<br />
There are <?php echo count_logged() ?> persons logged.
```

```
// Bad way to enable text translation
<?php echo __('Welcome to all the') ?>
<b><?php echo __('new') ?></b><?php echo __('users') ?>.<br />
<?php echo __('There are') ?>
<?php echo count_logged() ?>
<?php echo __('persons logged') ?>
```

```
// Good way to enable text translation
<?php echo __('<b>Welcome to all the <b>new</b> users</b>') ?> <br />
<?php echo __('There are %1% persons logged', array('%1%' =>
count_logged())) ?>
```

In this example, the token is %1%, but it can be anything, since the replacement function used
by the translation helper is strtr().

One of the common problems with translation is the use of the plural form. According to the
number of results, the text changes but not in the same way according to the language. For
instance, the last sentence in Listing 13-16 is not correct if count_logged() returns 0 or 1.
You could do a test on the return value of this function and choose which sentence to use
accordingly, but that would represent a lot of code. Additionally, different languages have
different grammar rules, and the declension rules of plural can be quite complex. As this
problem is very common, symfony provides a helper to deal with it, called
format_number_choice(). Listing 13-17 demonstrates how to use this helper.

### Listing 13-17 - Translating Sentences Depending on the Value of Parameters

```
<?php echo format_number_choice(
 '[0]Nobody is logged|[1]There is 1 person logged|[1,+Inf]There are %1%
persons logged', array('%1%' => count_logged()), count_logged()) ?>
```

The first argument is the multiple possibilities of text. The second argument is the
replacement pattern (as with the __() helper) and is optional. The third argument is the
number on which the test is made to determine which text is taken.

The message/string choices are separated by the pipe (|) character followed by an array of
acceptable values, using the following syntax:

- [1,2]: Accepts values between 1 and 2, inclusive
- (1,2): Accepts values between 1 and 2, excluding 1 and 2
- {1,2,3,4}: Only values defined in the set are accepted
- [-Inf,0): Accepts values greater or equal to negative infinity and strictly less than
  0
- {n: n % 10 > 1 && n % 10 < 5} pliki: Matches numbers like 2, 3, 4, 22, 23,
  24 (useful for languages like Polish or Russian)

Any nonempty combinations of the delimiters of square brackets and parentheses are
acceptable.

The message will need to appear explicitly in the XLIFF file for the translation to work
properly. Listing 13-18 shows an example.

### Listing 13-18 - XLIFF Dictionary for a format_number_choice() Argument

```
...
<trans-unit id="3">
<source>[0]Nobody is logged|[1]There is 1 person logged|(1,+Inf]There are %1% persons logged</source>
<target>[0]Personne n'est connecté|[1]Une personne est connectée|(1,+Inf]Il y a %1% personnes en ligne</target>
</trans-unit>
...
```

## A few words about charsets

Dealing with internationalized content in templates often leads to problems with charsets. If you use a localized charset, you will need to change it each time the user changes culture. In addition, the templates written in a given charset will not display the characters of another charset properly.

This is why, as soon as you deal with more than one culture, all your templates must be saved in UTF-8, and the layout must declare the content with this charset. You won't have any unpleasant surprises if you always work with UTF-8, and you will save yourself from a big headache.

Symfony applications rely on one central setting for the charset, in the settings.yml file. Changing this parameter will change the content-type header of all responses.

```
all:
.settings:
charset: utf-8
```

## Calling the Translation Helper Outside a Template

Not all the text that is displayed in a page comes from templates. That’s why you often need to call the __() helper in other parts of your application: actions, filters, model classes, and so on. Listing 13-19 shows how to call the helper in an action by retrieving the current instance of the I18N object through the context singleton.

### Listing 13-19 - Calling __() in an Action

```
$this->getContext()->getI18N()->__($text, $args, 'messages');
```

## Summary

Handling internationalization and localization in web applications is painless if you know how to deal with the user culture. The helpers automatically take it into account to output correctly formatted data, and the localized content from the database is seen as if it were part of a simple table. As for the interface translation, the __() helper and XLIFF dictionary ensure that you will have maximum versatility with minimum work.

## Chapter 14

## Admin Generator

Many applications are based on data stored in a database and offer an interface to access it. Symfony automates the repetitive task of creating a module providing data manipulation capabilities based on a Propel or Doctrine object. If your object model is properly defined, symfony can even generate an entire site administration automatically. This chapter describes the use of the administration generator, which is bundled with the Propel and Doctrine plugin. It relies on a special configuration file with a complete syntax, so most of this chapter describes the various possibilities of the administration generator.

## Code Generation Based on the Model

In a web application, data access operations can be categorized as one of the following:

- Creation of a record
- Retrieval of records
- Update of a record (and modification of its columns)
- Deletion of a record

These operations are so common that they have a dedicated acronym: CRUD. Many pages can be reduced to one of them. For instance, in a forum application, the list of latest posts is a retrieve operation, and the reply to a post corresponds to a create operation.

The basic actions and templates that implement the CRUD operations for a given table are repeatedly created in web applications. In symfony, the model layer contains enough information to allow generating the CRUD operations code, so as to speed up the early part of the back-end interfaces.

## Example Data Model

Throughout this chapter, the listings will demonstrate the capabilities of the symfony admin generator based on a simple example, which will remind you of Chapter 8. This is the well-known example of the weblog application, containing two BlogArticle and BlogComment classes. Listing 14-1 shows its schema, illustrated in Figure 14-1.

### Listing 14-1 - Propel schema of the Example Weblog Application

```
propel:
  blog_category:
    id:     ~
    name:   varchar(255)
  blog_author:
    id:     ~
    name:   varchar(255)
```
