GitHub repository. First off, log in to the Azure Container Registry, and then build and push the Docker image to the registry. Finally, this workflow will deploy the app to the Azure web app service and log out from Azure.

```
1. name: Build and deploy to production
2.
3. on:
4.   push:
5.     branches:
6.       - master
7.
8. jobs:
9.   build-and-deploy:
10.     runs-on: ubuntu-18.04
11.     strategy:
12.       matrix:
13.         python-version: ['3.7']
14.
15.     steps:
16.     - name: Checkout GitHub Actions
17.       uses: actions/checkout@master
18.
19.     - name: Set up Python ${{ matrix.python-version }}
20.       uses: actions/setup-python@v2
21.       with:
22.         python-version: ${{ matrix.python-version }}
23.
24.     - name: Install dependencies
25.       run: |
26.         python -m pip install --upgrade pip
27.         python -m pip install tox tox-gh-actions
28.
29.     - name: Test with tox
```