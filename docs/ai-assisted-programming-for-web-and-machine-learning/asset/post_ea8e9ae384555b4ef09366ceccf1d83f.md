
| Generate an HTML form.| Generate a Bootstrap-based login form with JavaScript validation and ARIA accessibility. |

**Table 3.6:** Impact of prompt refinement on AI-generated outputs

This AI-generated code creates a responsive Bootstrap login form with JavaScript validation and accessibility features for a smooth user experience:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width,initial-scale=1.0">
  <title>Login Page</title>
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css">
</head>
<body>
  <div class="container mt-5">
    <form class="w-50 mx-auto" onsubmit="return validate()" aria-label="Login Form">
      <h2 class="text-center">Login</h2>
      <div class="mb-3">
        <label for="username" class="form-label">Username</label>
        <input type="text" class="form-control" id="username" required aria-required="true">
        <small id="userError" class="text-danger"></small>
      </div>
      <div class="mb-3">
        <label for="password" class="form-label">Password</label>
        <input type="password" class="form-control"
```

```html
id="password" required aria-required="true">
<small id="passError" class="text-danger"></small>
<div><button type="submit" class="btn btn-primary w-100">Login</button></form></div>
<script>
 function validate() {
  let username = document.getElementById("username").value;
  let password = document.getElementById("password").value;
  let userError = document.getElementById("userError");
  let passError = document.getElementById("passError");
  userError.innerHTML = "";
  passError.innerHTML = "";
  if (username.trim() === "") {
    userError.innerHTML = "Username cannot be empty";
    return false;
  }
  if (password.length < 6) {
    passError.innerHTML = "Password must be at least 6 characters long";
    return false;
  }
  return true;
}
</script>
</body>
</html>
```
```

**Note:** AI-generated code may slightly vary across tools like GitHub Copilot or ChatGPT. Always review and test before use.

**Visual preview: Figure 3.4** illustrates the rendered Bootstrap-based login form, complete with input validation and ARIA accessibility features. This serves as a reference for readers to visualize the expected output.

![](img/036cc5d5719121241c605ad59a82949c_188_0.png)

**Figure 3.4:** Responsive login form with validation messages

Integrating Accessible Rich Internet Applications (ARIA) attributes enhances accessibility by allowing screen readers to interpret content more effectively, ensuring a more inclusive experience for users with disabilities. Implementing client-side validation prevents form submissions when inputs are invalid, providing immediate feedback and improving usability. By prioritizing accessibility and validation, the application creates a seamless and user-friendly experience for all users.

- **AI-generated dark mode toggle with Tailwind CSS:** This example shows how AI can create a responsive dark mode toggle using Tailwind CSS and JavaScript, making theme switching easy and seamless.

**Better prompt: Generate a responsive HTML dark mode toggle switch using Tailwind CSS and JavaScript.**

This AI-generated code creates a simple dark mode toggle with Tailwind CSS and JavaScript, letting users switch themes with one click:

```html
<button id="dark-mode-toggle" class="bg-gray-300 dark-gray-800 text-black dark:text-white px-4 py-2 rounded">
  Toggle Dark Mode
</button>
<script>
  const toggleButton = document.getElementById("dark-mode-toggle");
  toggleButton.addEventListener("click", () => {
    document.documentElement.classList.toggle("dark");
  });
</script>
```

Tailwind CSS utility classes offer a highly flexible and efficient way to style components, making customization seamless. The implementation features an instant light or dark mode toggle that allows users to switch themes effortlessly without reloading the page. A straightforward JavaScript event listener dynamically applies dark mode, ensuring a smooth and responsive user experience.

Using well-structured prompts helps improve the quality of AI-generated front end code, ensuring cleaner and more efficient output. By incorporating accessibility and performance constraints, developers can enhance usability and create more inclusive web experiences. AI can generate complete web components, handling styling, validation, and interactivity, significantly streamlining development. By leveraging AI for front end development, developers can build high-quality, accessible, and user-friendly web interfaces more efficiently.

# AI-powered back end code suggestions

AI can streamline back end development by generating, optimizing, and securing API implementations in response to structured prompts. Developers can build secure, scalable, well-structured back end systems using AI-powered assistance.

- **Example: Secure flask API with role-based authentication and rate limiting.**

This example shows how AI can generate a secure Flask API with authentication, role-based access, and rate limiting. JWT, SQLite, and logging ensure a safe and well-monitored system.

- **Better prompt: Generate a secure Flask API with authentication, role-based access...**

The following figure shows how API authentication works:

![](img/036cc5d5719121241c605ad59a82949c_191_0.png)

**Figure 3.4:** Responsive login form with validation messages

Integrating Accessible Rich Internet Applications (ARIA) attributes enhances accessibility by allowing screen readers to interpret content more effectively, ensuring a more inclusive experience for users with disabilities. Implementing client-side validation prevents form submissions when inputs are invalid, providing immediate feedback and improving usability. By prioritizing accessibility and validation, the application creates a seamless and user-friendly experience for all users.

```python
from flask import Flask, request, jsonify
import jwt
import datetime
import logging
from functools import wraps

app = Flask(__name__)
app.config['SECRET_KEY'] = 'your_secret_key'

# Configure logging for API monitoring
logging.basicConfig(
    filename="api_logs.log",
    level=logging.INFO,
    format="%(asctime)s - %(levelname)s - %(message)s"
)

# Secret key for JWT Function to generate JWT

```python
def generate_token(username, role):
    expiration = datetime.datetime.utcnow() + datetime.timedelta(hours=1)
    token = jwt.encode({
        "username": username,
        "role": role,
        "exp": expiration
    }, app.config["SECRET_KEY"], algorithm="HS256")
    return token
```

# Token required decorator

```python
def token_required(f):
    @wraps(f)
    def decorated(*args, **kwargs):
        token = request.headers.get("Authorization")
        if not token:
            logging.warning("Unauthorized access")
            return jsonify({"error": "Token is missing!"}), 401
        try:
            data = jwt.decode(token, app.config["SECRET_KEY"], algorithms=["HS256"])
        except jwt.ExpiredSignatureError:
            logging.warning("Expired token used")
            return jsonify({"error": "Token expired. Please log in again."}), 403
        except jwt.InvalidTokenError:
            logging.warning("Invalid token.")
            return jsonify({"error": "Invalid token!"}), 403
        return f(data, *args, **kwargs)
    return decorated
```

# User login
@app.route('/login', methods=['POST'])
def login():
    data = request.get_json()
    username = data.get("username")
    password = data.get("password")
    logging.info(f'Login attempt: {username}')
    # Mock user authentication
    if username == "admin" and password == "password123":
        token = generate_token(username, "admin")
        return jsonify({"token": token})
    logging.warning(f'Failed login attempt for {username}')
    return jsonify({"error": "Invalid credentials"}), 401

@app.route('/protected', methods=['GET'])
@token_required
def protected(data):
    return jsonify({"message": f"Welcome, {data['username']}!",
        "role": data['role']})

if __name__ == '__main__':
    app.run(debug=True)
```
