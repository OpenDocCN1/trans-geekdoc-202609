# .12 INTRODUCTION TO REGULAR EXPRESSIONS

Sometimes you'll need to recognize *patterns* in text, like phone numbers, e-mail addresses, ZIP Codes, web page addresses, Social Security numbers and more. A **regular expression** string describes a *search pattern* for *matching* characters in other strings.

Regular expressions can help you extract data from unstructured text, such as social media posts. They're also important for ensuring that data is in the correct format before you attempt to process it. ³

³ The topic of regular expressions might feel more challenging than most other Python features youve used. After mastering this subject, youll often write more concise code than with conventional string-processing techniques, speeding the code-development process. Youll also deal with fringe cases you might not ordinarily think about, possibly avoiding subtle bugs.

# Validating Data

Before working with text data, you'll often use regular expressions to *validate the data*. For example, you can check that:

+   • A U.S. ZIP Code consists of five digits (such as 02215) or five digits followed by a hyphen and four more digits (such as 02215-4775).

+   • A string last name contains only letters, spaces, apostrophes and hyphens.

+   • An e-mail address contains only the allowed characters in the allowed order.

+   • A U.S. Social Security number contains three digits, a hyphen, two digits, a hyphen and four digits, and adheres to other rules about the specific numbers that can be used in each group of digits.

You'll rarely need to create your own regular expressions for common items like these. Websites like

+   • https://regex101.com

+   • http://www.regexlib.com

+   • https://www.regular-expressions.info