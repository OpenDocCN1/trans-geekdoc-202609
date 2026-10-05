Before linting error with variable scope issue:

```
var total= 0;
function calculateTotal(price){
  total+= price; // No function scope, potential bug
}
```

**Problem:** Using var can cause scope-related issues, leading to unexpected behavior.

After AI-suggested fix:

```
let total = 0; // AI recommends using 'let' to ensure pro per scope
function calculateTotal(price){
  total += price;
}
```

AI prevents scope errors and enforces best coding practices automatically.

+   **Using GitHub Copilot for automated code refactoring:** GitHub Copilot analyzes code in real-time and suggests improvements in efficiency, security, and readability.

Let us look at an example of detecting and refactoring inefficient code.

Before optimization with complex, redundant code and security risks:

```
def get_user_data(username):
  query = "SELECT * FROM users WHERE username = " + username + "" # SQL Injection risk
  db.execute(query)
  return db.fetchall()
```

# **Problems:**

The following problems need to be addressed:

+   **Security vulnerability:** The query is susceptible to SQL injection attacks.