login system’s security vulnerability.

Vulnerable code before AI enhancement:

```
app.post('/login', async (req, res) => {
  const user = await User.findOne({ username: req.body.username });
  if (user.password === req.body.password) { // Insecure comparison
    return res.json({ message: "Login successful" });
  }
  res.status(401).json({ message: "Invalid credentials" });
});
```

Issue: The code performs a plaintext password comparison, which is insecure. Passwords should be hashed and verified using appropriate cryptographic methods (e.g., bcrypt or Argon2).

Example prompt given to the AI tool: Examine the following Node.js code for security vulnerabilities and suggest a more secure version using password hashing.

The AI tool then analyzes the insecure logic and recommends secure improvements, such as using bcrypt.compare() to verify passwords securely.

Secure code after AI enhancement:

```
const bcrypt = require('bcryptjs');
app.post('/login', async (req, res) => {
  const user = await User.findOne({ username: req.body.username });
  if (user && await bcrypt.compare(req.body.password, user.password)) { // Secure comparison
    return res.json({ message: "Login successful" });
  }
  res.status(401).json({ message: "Invalid credentials" });
});
```