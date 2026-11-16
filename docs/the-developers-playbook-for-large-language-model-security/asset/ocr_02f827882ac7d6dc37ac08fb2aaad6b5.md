We use Python's re library to match strings against a regular expression pattern for SSNs, which have a standard format of XXX-XX-XXXX, where each X is a digit. Here's some sample code that can help you check if a given string contains an SSN:

```
import re

def contains_ssn(input_string):
    # Define a regular expression pattern for a U.S. Social Security Number
    ssn_pattern = r'\b\d{3}-\d{2}-\d{4}\b'
    # Search for the pattern in the input string
    match = re.search(ssn_pattern, input_string)
    # Check if a match was found
    if match:
        print("Found a Social Security Number: {match.group(0)}")
        return True
    else:
        print("No Social Security Number found.")
        return False

# Test the function
contains_ssn("My Social Security Number is 123-45-6789.")
contains_ssn("No number here!")
```

In this example, the function contains_ssn will search input_string for a Social Security number and print a message indicating whether or not one was found.

Please note that this is simple pattern matching and doesn't account for invalid numbers (such as 000-00-0000), so you might want to extend this function to include additional validation if needed.

For more full-featured PII detection, you can use a commercial API, such as the Google Cloud Natural Language API or Amazon Comprehend. However, these APIs may have costs associated with them.

# Evaluating for Toxicity

Looking for toxic language is much more complex than finding a standard string format. There are many approaches to evaluating the possible toxicity of a string of characters. Here, we'll use a commonly available function from the Open AI API set: the Moderation API.

To use the OpenAI Moderation API, initialize an OpenAI API client and then call the check_toxicity() function, passing in the text you want to check. This function will return a toxicity score between 0 and 1, where a higher score indicates a higher probability of the text being toxic: