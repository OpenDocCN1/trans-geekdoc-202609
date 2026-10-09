```
'class'=> 'display','cellspacing'=> '0'],
'tform_tag_inside_wrapper' => FALSE,
];
```

Next, define an array that holds parameters for each form element to be created by the factory. The array key becomes the name of the form element, and must be unique:

```
$config = [
'email' => [
'class' => 'Application\Form\Generic',
'type' => Generic::TYPE_EMAIL,
'label' => 'Email',
'wrappers' => $wrappers,
'attributes'=> ['id'=>'email', 'maxLength'=>128,
'title'=>'Enter address',
'required'=>'', 'value'=>strip_tags($email)]
],
'password' => [
'class' => 'Application\Form\Generic',
'type' => Generic::TYPE_PASSWORD,
'label' => 'Password',
'wrappers' => $wrappers,
'attributes'=> ['id'=>'password',
'title' => 'Enter your password',
'required' => '']
],
// etc.
];
```

Lastly, be sure to generate the form:

```
$form = Factory::generate($config);
```

The actual display logic is extremely simple, as we simply call the form level `render()` method:

```
<?? $form->render($form, $formConfig); ?>
```