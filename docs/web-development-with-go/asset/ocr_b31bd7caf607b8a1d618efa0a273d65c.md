# 15.7. LETTING USERS DELETE IMAGES

some HTML uses to render the delete image button which will be inside an HTML form. This will cause a POST web request to be made when the button is clicked and the form is submitted.

We’ll start updating the show gallery template.

```
$ atom views/galleries/show.gohtml
```

The div with the images in it and update it to reflect the code below. We now need to call the Path method of an Image in order to get the path and can’t just us the dot (.) operator like we were doing before.

```
<div class="row">
{{range .ImagesSplit 3}}
  <div class="col-md-4">
    {{range .}}
      <a href="{{.Path}}">
<img src="{{.Path}}" class="thumbnail">
      </a>
    {{/end}}
  </div>
{{/end}}
</div>
```

Next is the edit gallery tempalte, where we will start by adding the deleteForm template.

```
$ atom views/galleries/edit.gohtml
```

Add the following template to the source file:

```
{{define "deleteImageForm"}}
<form action="/galleries/{{.GalleryID}}/images/{{.Filename}}/delete" method="POST">
<button type="submit" class="btn btn-default btn-delete">
```