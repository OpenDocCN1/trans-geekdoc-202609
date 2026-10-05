# 15.1. IMAGE UPLOAD FORM

example in the bootstrap docs¹. One of the few things we did add to the input field is edit the multiple attribute, which is our way of telling the browser that a user can select multiple images instead of just one. This is handy because users will frequently be uploading many images to a gallery.

The other thing worth noting is that this HTML form is using the “form-horizontal” class², which is another style of form provided by bootstrap that looks a little different. Most notably, the name of each input is displayed to the left of the input. We will be using this to make our form a little easier for users to follow and use.

We don't want our existing forms to look out of place, so we also need to go back and edit them to match the new form-horizontal style. While doing this we will also break the edit form and the delete button apart into two separate templates we can render wherever we want on the page moving forward.

```
(define editGalleryForm())
<form action="galleries/{{.ID}}/update" method="POST"
class="form-horizontal">
  <div class="form-group">
    <label for="title" class="col-md-1 control-label">Title</label>
    <div class="col-md-10">
      <input type="text" name="title" class="form-control" id="title"
placeholder="What is the title of your gallery?" value="{{.Title}}">
    </div>
  </div>
  <div class="col-md-1">
    <button type="submit" class="btn btn-default">Save</button>
  </div>
</form>
({end})

(define deleteGalleryForm())
<form action="galleries/{{.ID}}/update" method="POST"
class="form-horizontal">
  <div class="form-group">
    <div class="col-md-10 col-md-offset-1">
      <button type="submit" class="btn btn-danger">Delete</button>
    </div>
  </div>
</form>
```

¹https://bootstrap.com/docs/3.3/css/#forms-horizontal

²https://bootstrap.com/docs/3.3/css/#forms-horizontal