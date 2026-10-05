```
id="password" required aria-required="true">
<small id="passError" class="text-danger"></small>
<div><button type="submit" class="btn btn-primary w-100">Login</button></form></div>
<script>
 validate validate() {
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
```