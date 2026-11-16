the last two parameters aren't part of the function syntax, but are rather the actual text strings that PHP should print, they are enclosed in single quotes. Without the single quotes, the PHP interpreter would mistakenly attempt to read the period as the concatenation character and the comma as a separator between parameters, which would yield an error.

If you test the page now, the results are more satisfying.

![](bbox=[0.265, 0.205, 0.925, 0.605])

# ADDING SERVER-SIDE FORM VALIDATION

As you discovered in the previous task, the application works well when the user enters numbers in both fields. But if the user leaves one blank or enters a non-numeric character, an unsightly error message appears when she or he clicks Submit. Error messages such as the one shown earlier were meant to help developers debug applications; ideally, users should never see them.

To prevent the possibility of this error occurring, you can add form validation to ensure that the requisite numbers have been entered. You used form validation with the email form in Lesson 6. That was client-side form validation—using a Dreamweaver behavior, you added a JavaScript form validation script that fired as soon as the user clicked the Submit button. That was certainly easy to deploy, but