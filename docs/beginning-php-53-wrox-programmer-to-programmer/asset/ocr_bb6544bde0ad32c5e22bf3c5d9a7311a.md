# Part III: Using PHP in Practice

![](bbox=[0.158, 0.087, 0.743, 0.332])

Figure 9-8

![](bbox=[0.158, 0.393, 0.743, 0.626])

Member Signup: Step 2

Figure 9-9

# How It Works

For each step of the signup process, the script displays a form with a hidden field, step, to track the current step. For example:

```
<input type="hidden" name="step" value="1" />
```

The script starts by testing for the presence of this field in the submitted form data. If found, and its value is valid (between 1 and 3), the script uses PHP's call_user_func() function to call the appropriate processing function — processStep1(), processStep2(), or processStep3(). If the the

254