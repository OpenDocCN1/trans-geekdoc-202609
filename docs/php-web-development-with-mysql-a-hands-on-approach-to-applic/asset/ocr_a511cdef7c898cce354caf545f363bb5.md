# 23. ADDING USER LOGINS

```
```html
</div>
</div>
</div>
<div class="form-group row">
    <label for="password"
           class="col-sm-2 col-form-label-lg">Password</label>
    <div class="col-sm-4">
        <input type="password" class="form-control"
               id="password" name="password"
               placeholder="Enter a password" required>
        <div class="form-group form-check">
            <input type="checkbox"
                   class="form-check-input"
                   id="show_password_check"
                   onclick="togglePassword()">
            <label class="form-check-label"
                   for="show_password_check">Show Password</label>
        </div>
        <div class="invalid-feedback">
            Please provide a valid password.
        </div>
    </div>
</div>
<button class="btn btn-primary" type="submit"
        name="signup_submission">Sign Up
</button>
</form>
</div>
</div>
// ?>
</body>
```
```

Similar to previous forms we’ve created for this application, you’ll notice I’ve added Bootstrap’s validation for the password and user_name fields. Hence, we get Figure 23.3 when a user doesn’t enter any data into these form fields.

To enable this behavior, as in previous forms we’ve created requiring validation, we need to include the JavaScript function in Listing 23.3 in a `<script>` element tag set in our HTML `<body>` (right before the other `<script>` tags).

![](bbox=[0.5, 0.596, 0.87, 0.771])