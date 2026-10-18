
## Exercises

**9.1** Write a script which uses a ‘while’ loop to display the two times table:

```
2 × 1 = 2
2 × 2 = 4
2 × 3 = 6
2 × 4 = 8
2 × 5 = 10
2 × 6 = 12
2 × 7 = 14
2 × 8 = 16
2 × 9 = 18
2 × 10 = 20
```

Make sure that your script is flexible enough so that simply changing the value stored in a single variable, for example `$intTable`, would allow it to correctly display a different times table.

**9.2** Write a script which can display an XHTML table with a numeric value displayed in each table cell. For example, for a 3 × 4 table the table should look like this:

| 1 | 2 | 3 |
|---|---|---|
| 4 | 5 | 6 |
| 7 | 8 | 9 |
| 10 | 11 | 12 |

The script should use a nested loop construct and should be able, by changing the values of two variables (for example, `$intWidth` and `$intHeight`), to adjust the size of the table. Therefore, if changed to a 4 × 2 table the output would look like this:

| 1 | 2 | 3 | 4 |
|---|---|---|---|
| 5 | 6 | 7 | 8 |

**9.3** Write a script which defines a value of pence in a variable, for example `$intNumberOfPence`. It then calculates the minimum number of £2, £1, 50p, 20p, 10p, 5p, 2p and 1p coins that are required to represent that amount. For example, if the value of `$intNumberOfPence` was 97 then the output from the script would be:

The minimum number of coins required to make up 97p exactly is:

- 1 × 50p
- 2 × 20p
- 1 × 5p
- 1 × 2p

**9.4** Using loop constructs, produce a script which will output a calendar. You will need to define variables to contain the start day of the month (Sunday, Monday, etc.) and the number of days in the month. The output from a month beginning on a Tuesday and with 30 days should look like this:

| S | M | T | W | T | F | S |
|---|---|---|---|---|---|---|
|   |   | 1 | 2 | 3 | 4 | 5 |
| 6 | 7 | 8 | 9 | 10 | 11 | 12 |
| 13 | 14 | 15 | 16 | 17 | 18 | 19 |
| 20 | 21 | 22 | 23 | 24 | 25 | 26 |
| 27 | 28 | 29 | 30 |   |   |   |

**9.5** Write a script which will convert an Arabic format date, for example, 2005, into Roman numerals. To do this you will need to know the rules for Arabic to Roman numeral conversion:

| Numeral | Usage |
|---|---|
| I | I = 1 |
|   | II = 2 |
|   | III = 3 |
| V | IV = 4 (This means 5-1) |
|   | V = 5 |
|   | VI = 6 |
|   | VII = 7 |
|   | VIII = 8 |
| X | IX = 9 (This means 10-1) |
|   | X = 10 |
|   | ... |
| L | XL = 40 (This means 50-10) |
|   | L = 50 |
|   | LI = 51 |
|   | ... |
| C | XC = 90 (This means 100-10) |
|   | C = 100 |
|   | CI = 101 |
|   | ... |
| D | CD = 400 (This means 500-100) |
|   | D = 500 |
|   | DI = 501 |
| M | CM = 900 (This means 1000-100) |
|   | M = 1000 |
|   | MI = 1001 |
|   | ... |

Here are some dates for you to check your script with:

- 1900 = MCM
- 1975 = MCMLXXV
- 1998 = MCMXCVIII
- 2000 = MM
- 2067 = MMLXVII

## Summary

In this chapter, we began by describing the concept of flow of control and explained that PHP has a number of constructs which can be employed by the programmer to alter the flow of control through the script statements. The first flow of control statement which we examined was the ‘if’ statement. This was enhanced through the use of the ‘else’ and ‘elseif’ constructs. Following this, the ‘switch’ statement was described, which is essentially a different form of ‘if’ construct. The use of the ‘break’ statement was explained to control some of the processing within the ‘switch’ construct. Following this, the different forms of loop constructs, namely the ‘while’, ‘do–while’ and ‘for’ loops were examined. The chapter concluded by providing some examples of nested loops, breaking out of and continuing the iteration of various loop constructs.

## References and further reading

Imagination, PHP Documentation Group. PHP Flow of Control Overview.
http://theopensourcery.com/phpcontrol.htm

Newman, C. (2005) PHP's Flow Control: Conditional statements. http://www.informit.com/articles/article.asp?p=381922&rl=1

Wikipedia. Flow of Control. http://en.wikipedia.org/wiki/Control_flow

## Form Interaction

### LEARNING OBJECTIVES

- To understand how PHP can interact with the user through the use of XHTML forms
- To understand and be able to create an XHTML form construct and understand why combining PHP and XHTML forms is good practice
- To understand how a PHP form can invoke itself
- To understand how the data provided by the form elements can be accessed inside a PHP script
- To understand the concept of form validation and how it can be performed
- To understand how form elements’ data can be retained after a form submission
- To understand how and why hidden data can be included within a form

### INTRODUCTION

In this chapter we are going to examine the way in which the user can interact with a PHP script. In all of our previous scripts, interaction with the computer user has been one way: the script runs and the user can view the output. Apart from directly editing the script, the user cannot alter the way in which the statements function. However, unless we have a means to alter what a script does or change the data a script uses dynamically during run time, our PHP scripts are always going to be a bit limited.

Luckily for us, PHP is able to interact with a user via a web page by using forms. Forms are part of (X)HTML and not part of PHP. However, PHP can be used to access data entered into the form and use this data within the script.

In this chapter, we begin by explaining how form interaction works. We examine how form field data can be accessed by a PHP script and why it is often better to combine a form and its accompanying script into a single file. We examine each of the form field types and illustrate how the data from each of them can be accessed. We conclude the chapter by examining form validation and how to retain data on a form so that the user doesn't have to retype it.

### 10.1 PHP and form interaction

As previously mentioned, PHP can use forms to allow a script to interact with the user. But how does this work and why would we want to do this? Well, in Chapter 9, we set a few exercises where user interaction would have allowed us to produce a far more interesting and useful script. Consider the Arabic to Roman date conversion problem. Because we were unable to interact with the script we were unable to alter the date that we wished to convert without modifying the original script. While this is slightly annoying in a development environment, it has far more serious consequences for any scripts we may wish to make available online to the Web community.

Consider the security implications that would surround allowing everyone access to your server to make changes to your PHP scripts! Apart from allowing access to the inner workings of your code (which you may not wish to do for confidentiality reasons), you would have to trust everyone who modified your script to do this properly and in an orderly fashion. Basically, this is not going to work and so a mechanism to allow users to specify the data that they wish to input to the script needs to be implemented and this is where forms come in.

By using an XHTML form, we can provide an interface (the form itself) to allow, for example, a user to enter the date they wish to convert. This date can then be transferred to the PHP script in the form of a variable for processing by the statements forming the script. This simple use of forms is illustrated in Figure 10.1.

**FIGURE 10.1** Using forms to interact with PHP

![](img/b2471264f405d17994ef173e4b9cec92_297_0.png)

**FIGURE 10.2** Using forms to interact with PHP

![](img/b2471264f405d17994ef173e4b9cec92_298_0.png)

In Figure 10.1, we see a web user request the form from the web server. This is located on the server and sent to the user's client computer to be displayed in the web browser. Figure 10.2 continues the story.

Figure 10.2 illustrates that the user completes the form by entering the required data. The form is then returned to the web server, which locates the appropriate PHP script and the script and form data are passed to the PHP interpreter. The output from the interpreter is then sent back to the client browser to be viewed by the user.

### 10.2 A simple form

Since we are using forms to interact with PHP, the best place to start is by creating an XHTML web form like the one shown here:

```
<!-- File: example10-1.htm -->

<h2>Please enter your personal details:</h2>
<form action="example10-1.php" method="post">

<p>
<label for="strFirstname">Firstname: </label>
```
