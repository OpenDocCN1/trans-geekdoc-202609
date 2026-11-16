as you'll remember, the JavaScript error pop-up that appeared when the form was not filled in correctly wasn't terribly helpful.

In this task, you will add form validation on the server-side; that is, you will write some ASP, ColdFusion, or PHP code to verify that numbers were entered. If they were not, a hidden region of the HTML page will appear indicating an error. Because the error will be coded in HTML, you can make it say whatever you want, and you can also format it however you want.

The process will be as follows: The user fills out the form and clicks Submit. The page tourprice_processor.asp is requested. At the top of that page is a small form validation script, written in ASP, ColdFusion, or PHP, which verifies that numbers were entered in both fields. If numbers were entered in both fields, then the page processes as normal. If numbers were not entered in both fields, the user is redirected back to tourprice.asp, and the once-hidden HTML region with an error message is revealed.

'To create this functionality, we need to write the form validation script, which you'll do in this task. Then, in the next task, you'll create the HTML error region and hide it. Finally, you'll format the text in the HTML error region using CSS.

Now that you understand the big picture, let's sketch how this form validation script is going to work. First, we are using it for flow control. That is, depending on whether the user entered the proper data, the script needs either to continue to do the calculation or to redirect the user back to tourprice.asp. Handling flow control based on conditions is easy, using if..else constructs. The following pseudocode maps out the intended functionality of the script:

```
if the user entered a non-numeric or null value in either field
    redirect the user back to tourprice.asp
else
    continue as usual
end if
```

We'll further refine this script in two ways. The first is that you don't need to spell out the else portion if you just want to continue as usual. Thus, we really only need the if half of the script.

'The second refinement is that you don't merely want to redirect back to tourprice.asp: you also want to send a trigger that will change the visibility of the hidden region. In this case, a querystring/URL variable will do the job. Then, you'll add a script that looks for the presence of that URL variable, and if it is there, it will display the region. If it is not, the region will be hidden. Don't worry if this seems abstract; you'll get