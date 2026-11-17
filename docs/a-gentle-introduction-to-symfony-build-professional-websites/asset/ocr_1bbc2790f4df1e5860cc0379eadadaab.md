```
"";'), 'Your Email') ?>
<?php echo $form['message']->renderRow() ?>
<tr>
<td colspan="2">
<input type="submit" />
</td>
</tr>
</table>
</form>
```

But maybe you need to output the label and the input of each field in <li> tags rather than in a <tr> tags. A field “row” is made of a label, an optional error message (added by the validation system, explained later in this chapter), a help text, and a widget (note that the widget can consist of more than one form control). Just as you can output the various fields of a form one by one, you can also render the various parts of a form independently. Instead of using renderRow(), use any of render() (for the widget), renderError(), renderLabel(), and renderHelp(). For instance, if you want to render the whole form with <li> tags, write the template as follows:

```
// in modules/foo/templates/contactSuccess.php
<?php echo $form->renderFormTag('foo/contact') ?>
<ul>
<?php foreach ($form as $field): ?>
<li>
<?php echo $field->renderLabel() ?>
<?php echo $field->render() ?>
</li>
<?php endforeach; ?>
<li>
<input type="submit" />
</li>
</ul>
</form>
```

This renders to HTML as follows:

```
<form action="/frontend_dev.php/foo/contact" method="POST">
<ul>
<li>
<label for="name">Name</label>
<input type="text" name="name" id="name" />
</li>
<li>
<label for="email">Email</label>
<input type="text" name="email" id="email" />
</li>
<li>
<label for="subject">Subject</label>
<select name="subject" id="subject">
<option value="0">Subject A</option>
<option value="1">Subject B</option>
<option value="2">Subject C</option>
</select>
</li>
<li>
<label for="message">Message</label>
<textarea rows="4" cols="30" name="message" id="message"></textarea>
</li>
```