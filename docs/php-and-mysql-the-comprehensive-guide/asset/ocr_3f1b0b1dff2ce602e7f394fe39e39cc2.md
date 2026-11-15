> > **Note**
> > An overview of all modifiers can be found in the PHP documentation at http://s-prs.co/v602215.

# ## 10.3 Application Examples

In this section, we will show you some useful applications for regular expressions—for form validation, for example.

> > **Note**
> > You will find further examples of regular expressions in this book—for example, in the completeness check in Chapter 13. A check of email addresses is carried out there. This difficult topic is also discussed at http://s-prs.co/v602216.

# ## 10.3.1 Zip Codes

The verification of zip codes is very simple. A US zip code always consists of five digits. You can check this as follows:

```
`$reg = "/^\d{5}$/";`
```

Additionally a zip code can have a second part with four digits. As separator should be a space or a hyphen possible, after this there are four digits:

```
`$reg = "/^(\d{5})([:-\s](\d{4}))?$/";`
```

So you have the following tests:

+   * `(\d{5})` matches 5 digits for the first part of the zip code. The brackets make it accessible as part in the parts array of `preg_match()`.
+   * `(? ... )` groups the separator (space or hyphen) with the second four digits to a group. The question mark at the end tells, that this group is optional
+   * `[-\s]` matches a space with `\s` or a hyphen
+   * `(\d{4})` matches the 4 digits as part 2 of the parts array.

The brackets help to access the individual parts of the zip code separately. The following simple example uses Perl RegEx, and Figure 10.7 shows the result.

```
```php
<?php
$zip = "50000-4000";
$reg = "/^(\d{5})([:-\s](\d{4}))?$/";
if (preg_match($reg, $zip, $parts)) {
```
```