To initialize pspell, you must configure a dictionary. To do so, you need to create a handle to a dictionary configuration file, modify a few settings on that handle, and then use the dictionary configuration to create a second handle to the actual dictionary.

If this sounds a little complicated, don't worry. The code rarely changes, so you can usually just copy it from another script. However, let's look at it piece by piece. Here is the code that configures the dictionary:

```
```php
$dict_config = pspell_config_create('en', 'american');
pspell_config_ignore($dict_config, 3);
pspell_config_mode($dict_config, PSPELL_FAST);
```
```

$dict_config is the initial handle that controls the settings of your dictionary. You have to load all the settings into $dict_config and then create the dictionary with it. In this case, pspell_config_create() creates an English (en) dictionary with American spelling.

pspell_config_ignore() sets your dictionary to ignore all words of three letters and under. This is done because checking every a and the can be time consuming.

Finally, pspell_config_mode() tells pspell how you want to look things up. You have three choices:

You have three choices:

+   • PSPELL_FAST is a quick method that returns as few suggested spellings as possible.
+   • PSPELL_NORMAL returns a medium number of spellings, at a normal rate.
+   • PSPELL_SLOW takes some time to check, but it returns the maximum possible number of suggestions.

We can use other configurations here (such as adding a custom dictionary, which I'll get to in a bit), but since this is a quick-and-dirty spell check, we'll just create the dictionary itself with this line:

```
```php
$dictionary = pspell_new_config($dict_config);
```
```

There are two basic ways of using a dictionary at this point:

+   1. pspell_check($dictionary, word) returns True if word is in the dictionary.
+   2. pspell_suggest($dictionary, word) returns an array of suggested words if word isn't in the dictionary, with the first entry in the array being the most likely candidate. If the word is in the dictionary, or if there are no suggestions, this function returns nothing. The number of words that you get varies, but you get more with PSPELL_SLOW and fewer with PSPELL_FAST.

> **NOTE** These functions do not check for contextual spellings. Mary hat a ladle lam checks out perfectly, even if you meant Mary had a little lamb. In addition, pspell always returns True if the word is under the string length set with pspell_config_ignore(), so in this case, a small but obviously misspelled word like jlz will still return True.