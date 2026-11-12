Then run perl cmdline.pl a.txt, and a.txt is printed out to the command line. The key to this Perl program is this part of the code:

```
foreach (<>)
```

The magical thing inside parentheses, <>, opens the file named on the command line and puts each line of the file into a list. Thus, the foreach statement walks through the list — that is, each line in the file. Inside the loop, I print out each item in the list using the default variable; each item in the list is a line in the file. Therefore, I'm printing out each line in the file. It's like magic!

# Chomping your lines

Take a close look at this code, which is from the preceding section:

```
foreach (<>) {
   print "$_";
}
```

Then look at the output. You may notice something strange: The print statement prints the default variable, $_, and nothing more. But each line prints to the screen on a separate line, as if I had included a \n inside quotes after the $_. But I didn't. What's going on?

When you read in each line from the file, you get not only the text from the line, but also the newline at the end of the line. That newline ends up as a part of the line. Thus, the first line is not just the string hello, but rather hello\n.

The inclusion of this newline may or may not be what you want. Often people don't want the newline, especially when reading in data. For example, you wouldn't want to read in the newline when your text file is a list of e-mail addresses you want to process. (You want e-mail addresses to read something like president@whitehouse.gov, not president@whitehouse.gov\n, with a newline at the end.) In cases such as this, you want to chomp the newline. (Yes, chomp is the official Perl word for removing the newline. I'm not making this up.)

If you've ever written code in another language that reads in lines of text, and you've wanted to remove the extra newline, you probably found that the process isn't clear cut. You don't just remove the final character because you may accidentally remove some important data. Sure, this code isn't very long: only a few lines, but why rewrite it over and over each time you write a program that processes a text file? The Perl designers recognized this and therefore came up with the chomp function.