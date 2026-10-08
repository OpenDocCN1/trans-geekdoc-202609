```
`mkvirtualenv pe --python=<path to python.exe>`
```

Make sure to replace `<path to python.exe>` with the actual path to python.exe on your machine.

After creating the virtual environment, it will be activated automatically. Ensure that you are using Python 3.9:

```
`python --version`
```

# ## 5.4 - Installing the OpenAI Python library

The OpenAI Python library is available on PyPI27. You can install it using pip:

```
`pip install openai==0.27.8`
```

# ## 5.5 - Getting an OpenAI API key

To use the OpenAI API, you need to get an API key. You can obtain one by signing up for OpenAI28 and then creating a new API key here29.

Note that the usage of the API is paid. However, for this guide, the total cost will not exceed $10. It’s probably half of that.

Don’t forget to export the API key as an environment variable:

```
`export OPENAI_API_KEY=<your API key>`
```

27 https://pypi.org/project/openai/  
28 https://platform.openai.com/  
29 https://platform.openai.com/account/api-keys