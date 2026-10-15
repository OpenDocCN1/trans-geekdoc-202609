# 2.1 Tasks performed in the CI stage:

+   - **Linting:** This involves using static code analysis tools to identify potential errors, stylistic inconsistencies, and adherence to coding best practices. These tools can detect issues like:
+     - **Syntax errors:** Unclosed brackets, missing semicolons, and other syntax errors that can prevent your code from running.
+     - **Potential bugs:** The linter might flag code constructs prone to logical errors, memory leaks, or other issues.
+     - **Style violations:** Many linters enforce specific coding styles (e.g., indentation, naming conventions) to improve code readability and maintainability.

# Code Example (using ESLint for linting Python code):

```
```bash
# Install ESLint and a linter plugin for Python
pip install eslint eslint-plugin-python
# Create a configuration file (.eslintrc.json) with desired rules
{
    "extends": ["eslint:recommended"],
    "plugins": ["python"],
    "env": {
        "browser": true,
        "es2020": true
    },
    "rules": {
        "semi": ["error", "always"],
        "quotes": ["error", "double"]
    }
}
```
```