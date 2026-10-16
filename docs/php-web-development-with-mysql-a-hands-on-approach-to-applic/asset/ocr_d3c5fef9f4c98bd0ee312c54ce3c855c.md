# 18. EDITING DATA USING THE WEB APPLICATION

2. Marking input elements with a required attribute to ensure the fields we want validated get validated:

```
<input type="number" ... required>
```

3. Adding <div> elements with class attributes set to invalid-feedback containing the validation text we want the user to see if they forget to fill in the field. Again, we add these directly under the <input> elements we want validated. Listing 18.9 is the complete HTML markup for the “Running Time” input field along with the invalid feedback we want the user to see if they forget to enter a value.

# Listing 18.9.

```
1. <div class="form-group row">
2.   <label for="movie_running_time_in_minutes"
3.     class="col-sm-3 col-form-label-lg">Running Time (min)</label>
4.   <div class="col-sm-8">
5.     <input type="number" class="form-control"
6.       id="movie_running_time_in_minutes"
7.       name="movie_running_time_in_minutes"
8.       value="<?= $movie_runtime ?>"
9.       placeholder="Running Time (in minutes)" required>
10.     <div class="invalid-feedback">
11.       Please provide a valid running time in minutes.
12.     </div>
13.   </div>
14. </div>
```

4. Adding the JavaScript code in Listing 18.10 to <script> tags following the form.

# Listing 18.10.

```
1. </form>
2. <script>
3. // JavaScript for disabling form submissions if there are invalid fields
4. (function() {
5.   'use strict';
6.   window.addEventListener('load', function() {
7.     // Fetch all the forms we want to apply custom Bootstrap validation styles to
8.     var forms = document.getElementsByClassName('needs-validation');
9.     // Loop over them and prevent submission
10.     var validation = Array.prototype.filter.call(forms, function(form) {
11.       form.addEventListener('submit', function(event) {
12.         if (form.checkValidity() === false) {
13.           event.preventDefault();
14.           event.stopPropagation();
15.         }
16.         form.classList.add('was-validated');
17.       }, false);
18.     });
19.   }, false);
20. }());
21. </script>
```