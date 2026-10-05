of numeric inputs. This flexibility is crucial for calculating the average without requiring an array. Option A requires an array, while option C does not directly allow variable-length arguments without modification. Option D achieves the same but is less efficient than the splat operator.

**Question 84.** In PHP, when performing error handling, what does the error_reporting() function do, and how can it be used to control the level of error reporting in a script?

+   - A. It sends error messages to the browser only when critical errors occur.
- B. It defines which errors are reported based on severity levels defined by constants.
- C. It automatically logs all errors to a specified file regardless of the settings.
- D. It allows the developer to ignore all errors in the script during execution.

Correct Answer: B
Explanation: The error_reporting() function sets which types of errors PHP will report during script execution based on predefined severity constants. By specifying levels like E_ALL, E_NOTICE, or E_WARNING, developers can control the verbosity of error messages, making it a vital tool for debugging. Options A, C, and D incorrectly describe the function's purpose and capabilities.

**Question 85.** When you define a PHP function, which of the following is true about the scope of variables within that function, and how do global variables interact with local function variables?

+   - A. Local variables can access global variables directly without any special declarations.
- B. Global variables can be accessed within a function only if they are declared with the global keyword.
- C. Functions in PHP have access to all variables defined outside of them, regardless of scope.
- D. Local variables inside a function can override global variables of the same name without any issues.