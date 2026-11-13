# # Writing Scripts for the Command Line

The PHP language provides certain functionality that is particularly useful for writing command-line scripts. You will rarely, if ever, use these features in the web environment, but they are described in the following sections.

# ## Character Mode Output

When you're producing web output, you use the <br> tag to produce a simple line break in the output. When it is sent to a web page, the newline character, \n , causes a line break in the HTML source, but it is not visible in the rendered web page.

Command-line scripts, however, produce text-only output, so you must use the newline character to format your output. If your script produces any output, you should always include \n after the last item has been displayed.

You can also take advantage of the fixed-width character mode when running command-line scriptsfor instance, by spacing output into columns. The printf function allows you to use width and alignment format characters, which have no effect on HTML output unless they're contained in <PRE> tags. For more information, refer to Lesson 6 , "Working with Strings."

# ## Command-Line Arguments

You can pass arguments to a shell script by simply appending them after the script name itself. The number of arguments passed can be found in the variable $argc , and the arguments themselves are stored in a numerically indexed array named $argv .

> **Arguments** The identifier names argc and argv are used for historic reasons. They originated in C and are now widely used in many programming languages.
> 
> In PHP $argc is assigned for convenience only; you could, of course, perform count ($argv) to find out how many arguments were passed to the script.

The $argv array will always contain at least one element. Even if no additional arguments are passed to the script, $argv[0] will contain the name of the script itself, and $argc will be 1 .

The script in Listing 21.1 requires exactly two arguments to be passed. Otherwise, an error message appears, and the script terminates. The output produced shows which of the two arguments is greater.