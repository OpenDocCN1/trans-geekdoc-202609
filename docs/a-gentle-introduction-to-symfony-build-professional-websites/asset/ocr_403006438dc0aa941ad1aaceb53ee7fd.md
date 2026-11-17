```
</tr>
<tr>
<th><label for="message">Message</label></th>
<td><textarea rows="4" cols="30" name="message"
id="message"></textarea></td>
</tr>
<tr>
<td colspan="2">
<input type="submit" />
</td>
</tr>
</table>
</form>
```

Each widget results in a table row containing a `<label>` tag, and a form input tag. Symfony
deduces the label name from the widget name by uppercasing it (the `subject` widget name
gives the ‘Subject’ label). As for the input tag, it depends on the widget type. Symfony adds
an `id` attribute to each widget, based on its name. Lastly, the rendering of the form is always
XHTML-compliant.

# Customizing the Form Display

Using echo `$form` is great for prototyping, but you probably want to control exactly the
resulting HTML code. The form object contains an array of fields, and calling `echo $form`
actually iterates over the fields and renders them one by one. To get more control, you can
iterate over the fields manually, and call the `renderRow()` on each field. The following listing
produces exactly the same HTML code as previously, but the template echoes each field
individually:

```
// in modules/foo/templates/contactSuccess.php
<?php echo $form->renderFormTag('foo/contact') ?>
<table>
<?php echo $form['name']->renderRow() ?>
<?php echo $form['email']->renderRow() ?>
<?php echo $form['subject']->renderRow() ?>
<?php echo $form['message']->renderRow() ?>
<tr>
<td colspan="2">
<input type="submit" />
</td>
</tr>
</table>
</form>
```

Rendering fields one by one allows you to change the order in which they are displayed, and
also to customize their appearance. `renderRow()` expects a list of HTML attributes as first
argument, so you can define a custom class, `id`, or JavaScript event handler for instance.
The second argument of `renderRow()` is an optional label that overrides the one deduced
from the widget name. Here is an example of customization for the contact form:

```
// in modules/foo/templates/contactSuccess.php
<?php echo $form->renderFormTag('foo/contact') ?>
<table>
<?php echo $form['name']->renderRow(array('size' => 25, 'class' =>
'foo'), 'Your Name') ?>
<?php echo $form['email']->renderRow(array('onclick' => 'this.value =
```