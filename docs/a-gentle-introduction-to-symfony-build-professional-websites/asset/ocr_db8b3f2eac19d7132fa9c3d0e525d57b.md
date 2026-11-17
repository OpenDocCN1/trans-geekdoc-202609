```
author_id: { type: integer, required: true, foreignTable: author,
foreignReference: id, OnDelete: cascade }
created_at: ~

author:
  id: ~
  first_name: varchar(20)
  last_name: varchar(20)
  email: { type: varchar(255), required: true, index: unique }
  active: boolean
```

A form to edit an Article object should use a hidden widget for the id, a text widget for the title, a string validator for the title, etc. Symfony generates the form for you, provided that you call the propel:build-forms task:

```
// propel
$ php symfony propel:build-forms

// doctrine
$ php symfony doctrine:build-forms
```

For each table in the model, this command creates two files under the lib/form/ directory: a BaseXXXForm class, overridden each time you call the propel:build-forms task, and an empty XXXForm class, extending the previous one. It is the same system as the Propel model classes generation.

The generated lib/form/base/BaseArticleForm.class.php contains the translation into widgets and validators of the columns defined for the article table in the schema.yml:

```
class BaseArticleForm extends BaseFormPropel
{
    public function setup()
    {
        $this->setWidgets(array(
            'id' => new sfWidgetFormInputHidden(),
            'title' => new sfWidgetFormInputText(),
            'slug' => new sfWidgetFormInputText(),
            'content' => new sfWidgetFormTextarea(),
            'is_published' => new sfWidgetFormInputCheckbox(),
            'author_id' => new sfWidgetFormPropelChoice(array('model' =>
            'Author', 'add_empty' => false)),
            'created_at' => new sfWidgetFormDatetime(),
        ));
        $this->setValidators(array(
            'id' => new sfValidatorPropelChoice(array('model' =>
            'Article', 'column' => 'id', 'required' => false)),
            'title' => new sfValidatorString(array('max_length' => 255)),
            'slug' => new sfValidatorString(array('max_length' => 255)),
            'content' => new sfValidatorString(array('max_length' => 255,
            'required' => false)),
            'is_published' => new sfValidatorBoolean(),
            'author_id' => new sfValidatorPropelChoice(array('model' =>
            'Author', 'column' => 'id')),
            'created_at' => new sfValidatorDatetime(array('required' =>
            false)),
        ));
        $this->setPostValidator(
            new sfValidatorPropelUnique(array('model' => 'Article', 'column' =>
```