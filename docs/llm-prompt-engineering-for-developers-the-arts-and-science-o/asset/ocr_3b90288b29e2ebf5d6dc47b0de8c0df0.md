```
message
except:
    print("Felix: Sorry, a problem occured. Please try again later.")
```

This code sets up a simple chatbot interaction using the OpenAI API. The user provides a message, and the chatbot (named Felix) responds based on the given message and the previous hardcoded conversation context. If there's any issue with the API call, it gracefully handles the error and informs the user.

# 5.7 - Interactive Prompting

To make the chatbot interactive, we will use Click to create a command-line interface (CLI). Click<sup>30</sup> is a third-party Python package that allows for the creation of command-line interfaces in a composable way with as little code as neccessary. It's known as the “Command Line Interface Creation Kit”.

Install Click using pip:

```
pip install click==8.1.7
```

Next, update the code in app.py to use Click:

```
import os
import openai
import click

openai.api_key = os.getenv("OPENAI_API_KEY")

@click.command()
def chat_with_felix():
    """Chat with Felix, the chatbot."""
    print("Felix: Hi there. I am Felix, the chatbot. How can I help you\
```

<sup>30</sup>https://palletsprojects.com/p/click/