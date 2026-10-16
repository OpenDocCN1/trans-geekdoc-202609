# 23. ADDING USER LOGINS

```
```html
</div>
</div>
<button class="btn btn-primary" type="submit" name="signup_submission">Sign Up
</button>
</form>
<?php
endif;
?>
</div>
</div>
<script>
  // JavaScript for disabling form submissions if there are invalid fields
  (function () {
    'use strict';
    window.addEventListener('load', function () {
      // Fetch all the forms we want to apply custom Bootstrap validation styles to
      var forms = document.getElementsByClassName('needs-validation');
      // Loop over them and prevent submission
      var validation = Array.prototype.filter.call(forms, function (form) {
        form.addEventListener('submit', function (event) {
          if (form.checkValidity() === false) {
            event.preventDefault();
            event.stopPropagation();
          }
          form.classList.add('was-validated');
        }, false);
      });
    }, false);
  })();

  function togglePassword() {
    var password_entry = document.getElementById("password");
    if (password_entry.type === "password") {
      password_entry.type = "text";
    } else {
      password_entry.type = "password";
    }
  }
</script>
<script src="https://code.jquery.com/jquery-3.5.1.slim.min.js"
        integrity="sha384-DfXdz2htPH0lsSSs5nCTpuj/zy4C+Ogpa..."
        crossorigin="anonymous"></script>
<script src="https://cdn.jsdelivr.net/npm/popper.js@1.16.0/dist/umd/popper.min.js"
        integrity="sha384-Q6E9RHvbIyZFJoft+2mJbHaEWldvI9Y0y5n3zV9zzTtm3lksdQRVvoxMfooAo"
        crossorigin="anonymous"></script>
<script src="https://stackpath.bootstrapcdn.com/bootstrap/4.5.0/js/bootstrap.min.js"
        integrity="sha384-OgVRvuATP1z7JjHLkuou8xW704+h835Lr+6QL9UvYjZE3Ipu6T7jBh/kR0JKT"
        crossorigin="anonymous"></script>
</body>
</html>
```
```