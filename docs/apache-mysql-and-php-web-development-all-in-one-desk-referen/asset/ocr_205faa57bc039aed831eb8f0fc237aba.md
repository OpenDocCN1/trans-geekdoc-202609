As for what all these cryptic letters and symbols mean, well, that's the point of this minibook. In the chapters that follow, you discover what the different pieces mean. For now, here's what you need to know: The stuff I typed in the Find What box extracts a string from each line and saves it in a variable of sorts called \1. This string is the name in the middle of the line; for example, the \1 string in the line `<option value="My Page">My Page</option>` would be My Page. In the Replace With box, I use that \1 variable; you can see the \1 in it. Thus, the line containing My Page will become `insert into mytable (name) values ('My Page');`.

![](bbox=[0.12, 0.27, 0.22, 0.34])

If you're a little familiar with regular expressions, you may want to know more about the cryptic expression used earlier. The first part — `<o.*` — searches for the initial option tag. Here's a closer look:

+   * The `<o` represents the start of the option tag.
+   * The `.*` means any number of any characters.
+   * The `>` is the closing part of the tag.

Continuing with the technical stuff, the last part — `<.*$` — finds the closing `</option>` tag. In this part, the expression starts with the final `<` and goes to the end of the line. Here's a breakdown:

+   * The `<` represents the final `<`.
+   * `$` means the end of the line.
+   * The middle part — `\(.*\)` — grabs everything in between and saves it in a variable that you can access in the replace string as `\1`. The reason everything gets saved is thanks to the parentheses. (However, some editors, such as the one I'm using, require you to put backslashes before each parenthesis.)

Now I want to show you how you can do this same thing in the ancient but beloved vi editor. (Please don't tell anybody I use it. I have a reputation to uphold.) This technique will work in other Unix editors as well, because they tend to use this same format. The only difference is that for those editors, you will type a different set of keystrokes to get to the search and replace feature. (Check your docs for the route to the land of Search and Replace if you're not sure.)

Here's the command for the vi editor:

```
:g/<o.*>(.*)<.>*s//insert into mytable (name) values ('\1');/g
```