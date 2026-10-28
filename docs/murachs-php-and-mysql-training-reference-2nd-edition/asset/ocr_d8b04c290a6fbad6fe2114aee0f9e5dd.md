# Exercise 6-2 Use NetBeans to step through the Future Value application

In this exercise, you’ll use NetBeans with xDebug to set a breakpoint and step through the Future Value application of chapter 2. Before you do that, though, be sure you have configured xDebug to work with NetBeans as described in the appendix.

+   1. Start NetBeans and open the ch06_ex2 application in the ex_starts directory. Then, open the display_results.php file in the editor.
+   2. Set a breakpoint in the display_results.php file on the statement before the for loop that calculates the future value.
+   3. Right-click on the project, select the Debug command to begin debugging. If this displays a dialog box warning that a firewall has blocked some features of NetBeans, allow NetBeans to communicate on private and/or domain networks.
+   4. Switch back to NetBeans after the browser opens. The debugger should stop the application at the first PHP statement it encounters. Then, click on the Step Into button repeatedly to step through the code until the first web page is displayed.
+   5. Switch to the browser to view the first page. Then, enter valid values, click on the Calculate button, and switch back to NetBeans. The application should stop at the next PHP statement it encounters.
+   6. Click on the Step Into button to execute three statements. Then, click on the Variables tab to display the current variables.
+   7. Click on the plus sign of the Superglobals variable in the Variables tab, and click on the plus sign for the _POST array. That will display the values of the three user entries that were passed to the server.
+   8. Click on the Continue button to continue to the breakpoint that you set. Then, use the Step Into button to execute the loop. Note how the variables in the Variables tab change as you execute the loop.
+   9. Click on the Continue button to finish the calculation and display the next web page. To view this page, switch to your browser.
+   10. Run the application again and experiment with the Step Into, Step Over, and Step Out buttons as you step through the code of the application. At each step, notice the values that are displayed in the Variables tab.
+   11. When you’re through experimenting, remove the breakpoint and click on the Finish Debugger Session button. Close the browser and then close the project.