
As you may recall, in this chapter we’re aiming to make it easier for non-HTML-savvy users to add formatting to the jokes on our website. For example, if a user puts asterisks around a word in the text of a joke—such as `'Knock *knock*…'`—we’d like to display the joke with HTML emphasis tags around that word: `Knock <em>knock</em>…'`.

We can detect the presence of plain-text formatting such as this in a joke’s text using `preg_match` with the regular expression syntax we’ve just learned. However, what we *need* to do is pinpoint that formatting and *replace* it with appropriate HTML tags. To achieve this, we need to look at another regular expression function offered by PHP: `preg_replace`.

`preg_replace`, like `preg_match`, accepts a regular expression and a string of text, and attempts to match the regular expression in the string. In addition, `preg_replace` takes another string of text and replaces every match of the regular expression with that string.

The syntax for `preg_replace` is as follows:

```
$newString = preg_replace($regExp, $replaceWith, $oldString);
```

Here, `$regExp` is the regular expression, and `replaceWith` is the string that will replace matches in `$oldString`. The function returns the new string with all the replacements made. In that code, this newly generated string is stored in `$newString`.

We’re now ready to build our joke formatting function.

## Emphasized Text

We could use a relevant `preg_replace` method everywhere it’s required in our templates. However, since this is going to be useful in multiple places, and any website we build, we’ll create a class for it and place it in our `Ninja` namespace:

```
namespace Ninja;

class Markdown {
  public function __construct(private string $string) {
  }

  public function toHtml() {
    // convert $this->string to HTML

    return $html;
  }
}
```

The plain-text formatting syntax we’ll support is a simplified form of Markdown, a markup language created by John Gruber. Markdown is described like this [on its home page](http://daringfireball.net/projects/markdown/):

> Markdown is a text-to-HTML conversion tool for web writers. Markdown allows you to write using an easy-to-read, easy-to-write plain-text format, then convert it to structurally valid XHTML (or HTML).

Since this class will convert Markdown to HTML, it’s named `Markdown`.

This first action is to use the `htmlentities` function to convert any HTML code present in the text into text, by removing any characters that are understood by browsers (`<`, `>`, `&`, `"`). We want to avoid any HTML code appearing in the output, except that which is generated from plain-text formatting.

### Not Quite Markdown

Technically, what we’re doing here breaks one of the features of Markdown: support for inline HTML. “Real” Markdown can contain HTML code, which will be passed through to the browser untouched. The idea is that you can use HTML to produce any formatting that’s too complex to create using Markdown’s plain-text formatting syntax. Since we don’t want to allow this, it might be more accurate to say we’ll support Markdown-*style* formatting.

Let’s start with formatting that will create **bold** and *italic* text.

In Markdown, you can emphasize text by surrounding it with a pair of asterisks (`*`), or a pair of underscores (`_`). (For example, *emphasized text* is achieved with `*emphasized text*` or `_emphasized text_`.) We’ll replace any such pair with `<em>` and `</em>` tags.

### `<em>` and `<strong>` vs `<i>` and `<b>`

You may be more accustomed to using `<i>` and `<b>` tags for bold and italic text. However, I’ve chosen to respect the most recent HTML standards, which recommend using the more meaningful `<em>` and `<strong>` tags respectively. If bold text doesn’t necessarily indicate strong emphasis in your content, and italic text isn’t representative of emphasis, you might want to use `<i>` and `<b>` instead.

To achieve this, we’ll use two regular expressions: one that handles a pair of asterisks, and one that handles a pair of underscores.

Let’s start with the underscores:

`` `/_[^_]+_/` ``

Breaking this down:

*   `/`: we choose our usual slash character to begin (and therefore delimit) our regular expression.
*   `_`: there’s nothing special about underscores in regular expressions, so this will simply match an underscore character in the text.
*   `[^_]`: square brackets are used to match a sequence of one or more characters that are placed between the opening bracket `[` and closing bracket `]`. The caret (`^`), when placed inside square brackets, acts as a logical *not*. The expression `[^_]` will match any character that is not an underscore.
*   `+`: the plus character indicates one or more characters that match the preceding expression. `[^_]+` can be read as *one or more characters that are not an underscore*.
*   `_`: the second underscore, which marks the end of the italicized text.
*   `/`: the end of the regular expression.

In English, the expression `/_[^_]+_/` could be translated as: “Find an underscore, followed by one or more characters that aren’t an underscore, and stop at the following underscore.”

Now, it’s easy enough to feed this regular expression to `preg_replace`, but we have a problem:

```
$text = preg_replace('/_[^_]+_/', '<em>emphasized text</em>', $text);
```

The second argument we pass to `preg_replace` needs to be the text that we want to replace each match with. The problem is, we have no idea what the text that goes between the `<em>` and `</em>` tags will be. It’s part of the text that’s being matched by our regular expression!

Thankfully, another feature of `preg_replace` comes to our rescue. If you surround a portion of the regular expression with parentheses, you can capture the corresponding portion of the matched text and use it in the replacement string. To do this, you’ll use the code `$n`, where `n` is `1` for the first parenthesized portion of the regular expression, `2` for the second, and so on, up to `99` for the 99th. Consider this example:

```
$text = 'banana';
$text = preg_replace('/(.*)(nana)/', '$2$1', $text);
echo $text; // outputs 'nanaba'
```

So `$1` is replaced with the text matched by the first grouped portion of the regular expression (`(.*)`—zero or more non-newline characters), which is `ba` in this case. `$2` is replaced by `nana`, which is the text matched by the second grouped portion of the regular expression (`(nana)`). The replacement string `'$2$1'`, therefore, produces `'nanaba'`.

### Double Quotes and Dollar Signs in Regular Expressions

If you think all the way back to Chapter 2, you’ll remember that PHP supports both double quotes (`"`) and single quotes (`'`) for strings. One difference between double and single quotes is that variables in double quotes are automatically expanded. For example, take this code:

```
$name = 'Tom';

echo "Welcome back $name";
```

This will print “Welcome back Tom”. This presents a problem when using regular expressions, as the dollar sign has a special meaning.

Let’s swap out the single quotes for double quotes in the second argument from above:

```
$text = preg_replace('/(.*)(nana)/', "$2$1", $text);
```

Now, PHP will try to expand the variables `$1` and `$2` when the string is created, rather than using them as part of the regular expression replacement. To overcome this, you can escape the `$` in the same way as you would a quote inside the string, by prefixing it with a backslash:

```
$text = preg_replace('/(.*)(nana)/', "\$2\$1", $text);
```

We can use the same principle to create our emphasized text, adding parentheses to our regular expression:

`` `/_([^_]+)_/` ``
