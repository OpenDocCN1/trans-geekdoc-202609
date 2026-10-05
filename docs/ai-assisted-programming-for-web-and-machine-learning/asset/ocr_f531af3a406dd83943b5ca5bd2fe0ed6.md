```
return jsonify({"error": "Invalid token!"}), 403
return f(data, *args, **kwargs)
return decorated
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
\    logging.warning(f'Failed login attempt for {username}')
    return jsonify({"error": "Invalid credentials"}), 401
```

@app.route('/protected', methods=['GET'])
@token_required

```
def protected(data):
    return jsonify({"message": f"Welcome, {data['username']}!",
        "role": data['role']})
```

```
if __name__ == '__main__':
    app.run(debug=True)
```

The system employs JWT-based authentication to verify users and safeguard sensitive data. To enhance security, it includes logging mechanisms that track login attempts and monitor API access patterns, helping detect potential threats. Failed authentication attempts are actively monitored, allowing for real-time security oversight. Role-based access control (RBAC) ensures efficient user management by assigning permissions based on user roles and maintaining a structured and secure access framework. Additionally, token misuse is mitigated through expiration handling and