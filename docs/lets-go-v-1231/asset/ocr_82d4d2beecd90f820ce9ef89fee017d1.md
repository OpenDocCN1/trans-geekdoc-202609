```
File: ui/html/pages/create.tmpl

{{define "title"}}Create a New Snippet{{end}}

{{define "main"}}}
<form action='/snippet/create' method='POST'>
<div>
<label>Title:</label>
<!-- Use the 'with' action to render the value of .Form.FieldErrors.title
if it is not empty. -->
{{with .Form.FieldErrors.title}}
<label class="error">{{.}}</label>
{{end}}
<!-- Re-populate the title data by setting the 'value' attribute. -->
<input type='text' name='title' value='{{.Form.Title}}'>
</div>
<div>
<label>Content:</label>
<!-- Likewise render the value of .Form.FieldErrors.content if it is
empty. -->
{{with .Form.FieldErrors.content}}
<label class="error">{{.}}</label>
{{end}}
<!-- Re-populate the content data as the inner HTML of the textarea. -->
<textarea name='content'>{{.Form.Content}}</textarea>
</div>
<div>
<label>Delete in:</label>
<!-- And render the value of .Form.FieldErrors.expires if it is not empty. -->
{{with .Form.FieldErrors.expires}}
<label class="error">{{.}}</label>
{{end}}
<!-- Here we use the 'if' action to check if the value of the re-populated
expires field equals 365. If it does, then we render the 'checked'
attribute so that the radio input is re-selected. -->
<input type='radio' name='expires' value='365' {{if (eq .Form.Expires 365)}}checked{{end}}> One Year
<!-- And we do the same for the other possible values too... -->
<input type='radio' name='expires' value='7' {{if (eq .Form.Expires 7)}}checked{{end}}> One Week
<input type='radio' name='expires' value='1' {{if (eq .Form.Expires 1)}}checked{{end}}> One Day
</div>
<div>
<input type='submit' value='Publish snippet'>
</div>
</form>
{{end}}
```

Hopefully this markup and our use of Go’s templating actions is generally clear — it’s just using techniques that we’ve already seen and discussed earlier in the book.

There’s one final thing we need to do. If we tried to run the application now, we would get a 500 Internal Server Error when we first visit the form at http://localhost:4000/snippet/create. This is because our snippetCreate handler currently doesn’t set a value for the templateData.Form field, meaning that when Go tries to evaluate a template tag like {{with .Form.FieldErrors.title}} it would result in an error because Form is nil.

Let’s fix that by updating our snippetCreate handler so that it initializes a new