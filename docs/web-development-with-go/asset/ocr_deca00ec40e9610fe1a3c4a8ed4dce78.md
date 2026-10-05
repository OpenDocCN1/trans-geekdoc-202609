```
Delete
</button>
</form>
{{end}}
```

Then update our galleryImages template to include this template and use the Path method we introduced earlier. We are also going to slightly tweak the style section to add a margin under our images, which will make our delete button and thumbnail combo look a little nicer.

```
{{define "galleryImages"}}
{{range .ImagesSplit 6}}
<div class="col-md-2">
  {{range .}}
    <a href="{{.Path}}">
      <img src="{{.Path}}" class="thumbnail">
    </a>
    {{template "deleteImageForm" .}}
  {{end}}
</div>
{{end}}
<style>
.thumbnail {
  width: 100%;
  margin-bottom: 6px;
}
.btn-delete {
  margin-bottom: 6px;
}
</style>
{{end}}
```

At this point our edit page should now be rendering both images and delete buttons for each image. The UI isn't amazing looking, but making them work is more important so we are going to start working on the method for our ImageService that will enable us to delete images.

Open up the images model again.