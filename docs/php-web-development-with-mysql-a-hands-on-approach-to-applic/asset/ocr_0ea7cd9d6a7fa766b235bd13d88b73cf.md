# Complete Code Listing

```
166.     </div>
167.     </div>
168.     <button class="btn btn-primary" type="submit"
169.         name="add_movie_submission">Add Movie</button>
170. </form>
171. <script>
172. // JavaScript for disabling form submissions if there are invalid fields
173. (function() {
174.     'use strict';
175.     window.addEventListener('load', function() {
176.     // Fetch all the forms we want to apply custom Bootstrap validation styles to
177.     var forms = document.getElementsByClassName('needs-validation');
178.     // Loop over them and prevent submission
179.     var validation = Array.prototype.filter.call(forms, function(form) {
180.         form.addEventListener('submit', function(event) {
181.             if (form.checkValidity() === false) {
182.                 event.preventDefault();
183.                 event.stopPropagation();
184.             }
185.             form.classList.add('was-validated');
186.         }, false);
187.     }, false);
188.     }, false);
189. })();
190. </script>
191. <?php
192. } // Display add movie form
193. ?>
194. </div>
195. </div>
196. <script src="https://code.jquery.com/jquery-3.3.1.slim.min.js"
197.     integrity="sha384-q8i/X+965DzO0rT7abK41JSTqIAqVgRVzpbzo5snXKpqYfRvH+8abtTE1Pi6jizo"
198.     crossorigin="anonymous"></script>
199. <script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.6/umd/popper.min.js"
200.     integrity="sha384-wHAiFfRl8U1abW3Og8zh9lNwAbd14Pi2jh4P+opef0gT8K27Xr1JzZ8W3U1dYfW"
201.     crossorigin="anonymous"></script>
202. <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/js/bootstrap.min.js"
203.     integrity="sha384-B0Uglyr+r7cqK1l5JgaXjtg..."
204.     crossorigin="anonymous"></script>
205. </body>
206. </html>
```