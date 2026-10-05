# CHAPTER 14. CREATING THE GALLERY RESOURCE

```
<tbody>
</table>
<a href="galleries/new" class="btn btn-primary">
New Gallery
</a>
</div>
</div>
{{end}}
```

Note: The above is all pure HTML and Bootstrap, and isn't specific to Go at all. If you are having trouble with it I suggest checking out some resources on HTML and the Bootstrap docs.

We want to replace the fake row we have with the current user's galleries. Those galleries can be accessed via a slice stored in the dot (.) inside of our template, so we would first start by adding a range.

```
{{range .}}
<tr>
<th scope="row">123</th>
<td>Fake gallery title</td>
<td><!-- ... --></td>
</tr>
{{end}}
```

Inside of range we can access each individual gallery by the dot (.) because the original dot will be replaced with an individual gallery while the range block is being executed. This can be confusing if first, but just remember that inside of a range block you're accessing the same data as outside of it.

Knowing that we can access the individual gallery, we can update our template to create real gallery rows by replacing each piece of mocked data with the field it would normally store. We need to do this for both the data we display, as well as the data used to generate hrefs inside the a tags.