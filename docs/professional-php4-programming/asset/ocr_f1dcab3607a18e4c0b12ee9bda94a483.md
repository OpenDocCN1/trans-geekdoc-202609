```
case "Create":
	$bSuccess = creatRecord();
	displayResults($bSuccess);
	break;
case "Delete":
	$bSuccess = deleteRecord();
	displayResults($bSuccess);
	break;
case "View":
	$aData = getData();
	displayData($aData);
	break;
} // end main()
/*************************/
// Call the main() function
main();
/*************************/
?>
```

This design has many advantages. One of them concerns the use of local variables. Since we have organized our code into functions, variables associated with one task, such as database querying, cannot interfere with variables associated with another task, such as page generation. Without functions, such interference could occur, especially with very commonly used variable names, like $i for loop control variables.

Perhaps the most significant advantage to the design above is that all of the client-side code is now centralized in a few specialized functions. Separating the application logic from the presentation code is extremely beneficial. Changes to either can be made easily without affecting the other (unless you want to). A less obvious benefit of this separation has to do with the built-in header() function. header() can be used to send HTTP header strings, and is very often used to redirect the user to a different PHP program.

For header() to work, it must be invoked before any character is sent to the browser. In a normal (non-function-based) page in which PHP and (X)HTML are interspersed throughout, this could be a problem: by the time you know that you want to call header(), you may have already sent a lot of output to the browser. In our new design, it is very easy for our main() function to determine the flow of execution, including any redirects, well before any client-side code is generated.

Of course, the outline above is a simplified example. In your site, you might have a standard navigation bar at the top of every page. You could create a function that generates the top of a page, and then call this function at the beginning of all of the other displayXxx() functions.

In addition to basic flow control, the main() function has a more subtle role. Through its analysis of the user's action, it is determining the state of the page. If $action has no value, then we know that the user has arrived at the page for the first time, because no submit button was clicked. If $action's value is "View", then we know that the user clicked the "View" submit button from the menu.