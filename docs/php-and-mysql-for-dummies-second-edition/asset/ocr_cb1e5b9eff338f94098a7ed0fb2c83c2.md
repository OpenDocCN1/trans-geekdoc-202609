```
$interest[horse]=horse
$interest[dragon]=dragon
```

The program that processes the form has the selections available in the POST array, as follows:

```
$_POST['interest']['horse']
$_POST['interest']['dragon']
```

Figure 8-12 shows the Web page produced by buildCheckbox.php.

![](bbox=[0.23, 0.33, 0.74, 0.61])

Figure 8-12:
A list of
check
boxes
produced
by the
program in
Listing 8-11.

# Using the information from the form

As I discuss earlier in this section, Joe Customer fills in an HTML form, selecting from lists and typing information into text fields. He clicks the submit button.

In the form tag, you tell PHP which program to run when the submit button is clicked. You do this by including action="programname" in the form tag. For instance, in most of the example listings in this chapter, I use action="processform.php". When the user clicks the submit button, the program runs and receives the information from the form. Handling form information is one of PHP's best features. You don't need to worry about the form data — just get it from one of the built-in arrays and use it.

The form data is available in the processing program in arrays, as shown in Table 8-1. The key for the array element is the name of the input field in the form. For instance, if you echo the following field in your form

```
echo "<input type='text' name='firstName'>";
```