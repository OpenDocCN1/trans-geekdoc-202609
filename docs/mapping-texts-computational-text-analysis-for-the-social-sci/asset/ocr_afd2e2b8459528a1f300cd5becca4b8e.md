not “corrections.” They are explicit reductions and thus should be motivated by our research aims.

We’ve already encountered an example: case. Certainly, not all languages have distinct upper (majuscule) and lower (minuscule) letters, but many do. In English, we often use capitals to denote, for example, the beginning of a sentence, proper nouns, acronyms, or to convey anger or excitement—and “camelcase” may convey sarcasm. Lowercasing or uppercasing all words assures the same word with different cases is still treated as the same, although it also means that we lose the information that capitalizing conveys.

8 Curiously, Georgian is typically written without case (called the Mkhedruli) but has a separate script of all capitals (called the Asomtavruli). In the 1950s, a linguist made a vain attempt to popularize mixing Asomtavruli with Mkhedruli, as upper and lowercase, respectively (Unicode 2022).

We may also want to change characters from one script to another—that is, transliterate. For example, accented characters are common among languages using the Latin script, such as “Raúl” and “Raül,” where English would render it “Raul.” Depending on the analysis, however, we may want to treat each of these names as equivalent. To do so, we could replace u, ũ, or ū with one of the other two, to render them equivalent.

```
```
names <- c("Raul", "Raúl", "Raül")
# how many unique names?
length(unique(names))

names <- gsub("[ü|ū]", "u", names)
# now how many unique names?
length(unique(names))
```
```

We can do this with stringi , which uses dictionaries designating from and to a wide range of languages.9

9 stringi uses dictionaries from the ICU (unicode-org.github.io/icu/). Use stri_trans_list() to see the full list of language transliterators.

We’ll first transliterate from “any” character set to the broadest range of Latin characters, and then we’ll transliterate this output to only those represented by one of the 128 “Basic Latin” characters of ASCII. Instead of being replaced by the U+codes, characters are replaced by their nearest equivalent in Basic Latin as determined by the dictionary.

In UTF-8, ASCII and Basic Latin form the first and second Unicode blocks, respectively. Characters outside this set consume more memory. For example, compare charToRaw("su") with charToRaw("ス").

```
```
in_str <- c("キャンパス", "wyladować", "Дюра", "heiß", "brûlée")
Encoding(in_str) <- "UTF-8"

# compare
stri_trans_general(in_str, id = "Latin-ASCII")
stri_trans_general(in_str, id = "Any-Latin")
```
```

```
```
[1] "キャンパス" "wyladowac" "Дюра" "heiss" "brulee"
[1] "kyanpasu" "wyladować" "Doroga" "heiß" "brûlée"
```
```

To correctly transliterate all of these to Basic Latin, use:

```
```
stri_trans_general(in_str, id = "Any-Latin; Latin-ASCII")
```
```

```
```
[1] "kyanpasu" "wyladowac" "Doroga" "heiss" "brulee"
```
```