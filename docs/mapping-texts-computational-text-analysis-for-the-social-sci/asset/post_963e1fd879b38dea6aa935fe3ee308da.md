
quote ” (which is U+201D in UTF-8) is rendered as â€œ if we tried to use Windows-1252 encoding (see Table 7.1).

## Table 7.1: Common “Mojibake” Encoding Errors

| Expected | Mojibake | Unicode | Expected | Mojibake | Unicode |
| :--- | :--- | :--- | :--- | :--- | :--- |
| " | â€œ | U+201C | ' | â€™ | U+2019 |
| " | â€� | U+201D | — | â€” | U+2014 |
| , | â€~ | U+2018 | ... | â€| | U+2026 |

The above examples offer enough reason to become familiar with encodings, understand the encoding of our locale, and be consistent throughout our pipeline (as best we can). Doing so will mitigate unintended encoding errors in our corpus, making it less likely that we end up analyzing gibberish.

## THIS SECTION NEEDS:

- stringi
- quanteda
- tidytext
- tidyverse
- textclean
- tokenizers
- gutenbergr
- hunspell

## MARKUP CHARACTERS

When reading in a browser (like Mozilla Firefox or Apple Safari) or a word processor (like Microsoft Word or OpenOffice Writer), the text is “what you see is what you get” or WYSIWYG. We see different fonts and sizes, some words bold or italicized, words grouped into paragraphs or columns, etc. Behind the scenes is a range of characters that are not printed. Rather, the browser or word processor is interpreting those characters as formatting or style. These non-content characters are often called markup.

6 For example, Microsoft Notepad, gedit on Linux, or the editors built into IDEs like RStudio or VS Code.

Unlike word processors or browsers, plain-text editors6 do not interpret markup language. Rather, they operate as “what you see is what you mean” or WYSIWM. If we open a webpage HTML (Hypertext Markup Language) file in a plain-text editor, we see both content and markup characters. Aside from HTML, the most common markup languages include XML,7 LATEX, SGML, and Markdown. Within basic ASCII there are markup characters we’ll encounter regularly. These are non-printing characters as they define whitespace formatting around the printed characters (see Table 7.2).

7 The Microsoft Word “DOCX” format is a compressed archive (ZIP) of an XML file. We can “unzip” the DOCX and open the XML file in a plain-text editor.

The regularity of these markup languages can be a resource for wrangling text. Several packages can interpret markup and either remove it or use it to convert text into specific data structures. For example, html_text() in rvest removes all HTML markup tags.

## Table 7.2: Common Non-Printing Characters

| Description | Characters |
|---|---|
| Tab | \\t |
| Newline | \\n |
| Carriage return | \\r |
| Space | \\s Includes \\t \\n \\r |
| Line separator | \\r\\n |
| Horizontal space | \\h |
| Vertical tab | \\v |
| Word boundary | \\b |

We can also use the newline mark \\n or carriage return \\r encodings to break long pieces of text into lines and paragraphs. Let’s use a selection from Kennedy’s Rice speech. Below we arrange the speech as one long string, but after each line, we include \\n to indicate a newline.

```r
jfk_text <- c({
"we choose to go to the moon\\nwe choose to go to the moon\\n"
we choose to go to the moon in this decade and\\ndo the other
things not because they are easy\\nbut because they are hard\\n"
because they measure the best of our energies and skills\\n"
because that challenge is one that we're willing to accept\\n"
one we are unwilling to postpone and one we intend to win"
})
```

We can turn this long string into separate strings for each line by splitting on the newline character. This will structure our lines as discrete units of analysis.

```r
strsplit(jfk_text, split = "\\n")
```

```
[[1]]
 [1] "we choose to go to the moon"
 [2] "we choose to go to the moon"
 [3] "we choose to go to the moon in this decade and"
 [4] "do the other things not because they are easy"
 [5] "but because they are hard"
 [6] "because they measure the best of our energies and skills"
 [7] "because that challenge is one that we're willing to accept"
 [8] "one we are unwilling to postpone and one we intend to win"
```

## REMOVING AND REPLACING CHARACTERS

It is often useful to replace one character with a similar alternative or a shared root character. This “collapses” two versions of what researchers consider the “same” token. Unlike character encoding errors, these are not “corrections.” They are explicit reductions and thus should be motivated by our research aims.

We’ve already encountered an example: case. Certainly, not all languages have distinct upper (majuscule) and lower (minuscule) letters, but many do. In English, we often use capitals to denote, for example, the beginning of a sentence, proper nouns, acronyms, or to convey anger or excitement—and “camelcase” may convey sarcasm. Lowercasing or uppercasing all words assures the same word with different cases is still treated as the same, although it also means that we lose the information that capitalizing conveys.

8 Curiously, Georgian is typically written without case (called the Mkhedruli) but has a separate script of all capitals (called the Asomtavruli). In the 1950s, a linguist made a vain attempt to popularize mixing Asomtavruli with Mkhedruli, as upper and lowercase, respectively (Unicode 2022).

We may also want to change characters from one script to another—that is, transliterate. For example, accented characters are common among languages using the Latin script, such as “Raúl” and “Raül,” where English would render it “Raul.” Depending on the analysis, however, we may want to treat each of these names as equivalent. To do so, we could replace u, ũ, or ū with one of the other two, to render them equivalent.

```r
names <- c("Raul", "Raúl", "Raül")
# how many unique names?
length(unique(names))

names <- gsub("[ü|ū]", "u", names)
# now how many unique names?
length(unique(names))
```

We can do this with stringi , which uses dictionaries designating from and to a wide range of languages.9

9 stringi uses dictionaries from the ICU (unicode-org.github.io/icu/). Use stri_trans_list() to see the full list of language transliterators.

We’ll first transliterate from “any” character set to the broadest range of Latin characters, and then we’ll transliterate this output to only those represented by one of the 128 “Basic Latin” characters of ASCII. Instead of being replaced by the U+codes, characters are replaced by their nearest equivalent in Basic Latin as determined by the dictionary.

In UTF-8, ASCII and Basic Latin form the first and second Unicode blocks, respectively. Characters outside this set consume more memory. For example, compare charToRaw("su") with charToRaw("ス").

```r
in_str <- c("キャンパス", "wyladować", "Дюра", "heiß", "brûlée")
Encoding(in_str) <- "UTF-8"

# compare
stri_trans_general(in_str, id = "Latin-ASCII")
stri_trans_general(in_str, id = "Any-Latin")
```

```
[1] "キャンパス" "wyladowac" "Дюра" "heiss" "brulee"
[1] "kyanpasu" "wyladować" "Doroga" "heiß" "brûlée"
```

To correctly transliterate all of these to Basic Latin, use:

```r
stri_trans_general(in_str, id = "Any-Latin; Latin-ASCII")
```

```
[1] "kyanpasu" "wyladowac" "Doroga" "heiss" "brulee"
```

We may also want to replace some punctuation because ASCII only has a limited range of punctuation it can represent. Table 7.3 shows the punctuation represented in Basic Latin. Perhaps the most common punctuation needing replacement are the curved, curly, or smart quotes and apostrophes. They are so pesky that `textclean` has a function for replacing them: `replace_curly_quote()`.

In many cases, we'll strip punctuation from our corpus. For example, we usually want "wild." and "wild?" and "wild!" to be seen as the same token ("wild"). Without removing punctuation first, a tokenizer might assume they are distinct types (depending on what rules we use to tokenize).

## Table 7.3: Punctuation Marks and Unicodes

| Mark | Unicode | Description | Mark | Unicode | Description |
|---|---|---|---|---|---|
| ! | U+0021 | exclamation | : | U+003A | colon |
| " | U+0022 | quotation | ; | U+003B | semicolon |
| # | U+0023 | number | < | U+003C | less than |
| $ | U+0024 | dollar | = | U+003D | equal to |
| % | U+0025 | percent | > | U+003E | greater than |
| & | U+0026 | ampersand | ? | U+003F | question |
| ' | U+0027 | apostrophe | @ | U+0040 | at |
| ( | U+0028 | left parenthesis | [ | U+005B | left square bracket |
| ) | U+0029 | right parenthesis | \\ | U+005C | backslash |
| * | U+002A | asterisk | ] | U+005D | right square bracket |
| + | U+002B | plus sign | ^ | U+005E | circumflex/caret |
| , | U+002C | comma | _ | U+005F | low line/underscore |
| - | U+002D | hyphen/minus | { | U+007B | left curly bracket |
| . | U+002E | period/full stop | \| | U+007C | vertical bar |
| / | U+002F | forward slash | } | U+007D | right curly bracket |
| / | U+002F | forward slash | ~ | U+007E | tilde |

All these procedures rely on **regex**—this is true regardless of the programming language. In R, most packages rely on base R's suite of string matching functions—which are based on the Unix-based GREP—in addition to `stringi` and `stringr`, which are related (see Table 7.4).¹⁰ The simplest way to remove punctuation is with the character class `[:punct:]`, which matches all ASCII punctuation. Let's work through an example.

¹⁰ `stringr` builds atop `stringi` which uses ICU regular expressions.
