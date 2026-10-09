
The calling program will also contain the view logic that imports the minimum JavaScript to implement jQuery DataTables. You can add the code shown in step 3 of the preceding code. Then, add the document ready function and the display logic shown in steps 5 and 6. Here is the output:

![](img/39390f6d56c5a83b28db083a8bd5185c_193_0.png)

![](img/39390f6d56c5a83b28db083a8bd5185c_193_1.png)

### Wilfredo Taylor

- **Balance**: 25.11
- **Email**: wilfredo.taylor@telecom.net
- **Status**: 1
- **Level**: BEG

Show: 10 entries  
Search:

| **Transaction** | **Date** | **Qty** | **Price** | **Product** |
|---|---|---|---|---|
| APJ8650 | 2003-04-17 00:15:27 | 3 | 11.10 | Ice Cream Cake |
| AQP8375 | 2006-07-20 03:12:51 | 14 | 30.80 | Ambrosia Salad |
| BQO6079 | 1994-11-10 17:49:11 | 3 | 16.20 | Oatmeal Raisin Cookies |
| BHR1274 | 2004-03-20 08:24:13 | 17 | 75.50 | Banana Split |
| BMC1921 | 2013-02-22 19:39:15 | 7 | 12.50 | Apple Turnover |
| BME5477 | 2011-06-27 01:18:51 | 6 | 12.60 | Tapioca Pudding |
| BUY4627 | 2014-05-06 01:07:04 | 15 | 30.00 | Glazed Doughnut |
| CJH3811 | 1997-12-09 01:19:36 | 15 | 78.00 | Davis Food Cake |
| CPN1308 | 2008-11-14 01:47:20 | 5 | 7.00 | Peanut Butter Cookies |
| CPV1728 | 2000-05-22 23:50:23 | 8 | 48.00 | Mint Chocolate Milk Shake |

Showing 1 to 10 of 88 entries    Previous 1 2 3 4 5 ... 9 Next

## There's more...

For more information on jQuery, please visit their website at https://jquery.com/. To read about the DataTables plugin to jQuery, refer to this article at https://www.datatables.net/. Zero configuration data tables are discussed at https://datatables.net/examples/basic_init/zero_configuration.html. For more information on AJAX sourced data, have a look at https://datatables.net/examples/data_sources/ajax.html.

# 6

# Building Scalable Websites

In this chapter, we will cover the following topics:

- Creating a generic form element generator
- Creating an HTML radio element generator
- Creating an HTML select element generator
- Implementing a form factory
- Chaining `$_POST` filters
- Chaining `$_POST` validators
- Tying validation to a form

## Introduction

In this chapter, we will show you how to build classes that generate HTML form elements. The generic element generator can be used for text, text areas, passwords, and similar HTML input types. After that, we will show variations that allow you to pre-configure the element with an array of values. The form factory recipe will bring all these generators together, allowing you to render an entire form using a single configuration array. Finally, we introduce recipes that allow filtering and the validation of incoming `$_POST` data.

### Creating a generic form element generator

It’s pretty easy to create a function that simply outputs a form input tag such as `<input type="text" name="whatever">`. In order to make a form generator generically useful, however, we need to think about the bigger picture. Here are some other considerations over and above the basic input tag:

- The form input tag and its associated HTML attributes
- A label that tells the user what information they are entering
- The ability to display entry errors following validation (more on that later!)
- Some sort of wrapper, such as a `<div>` tag, or an HTML table `<td>` tag

### How to do it...

1. First, we define a `Application\Form\Generic` class. This will also later serve as a base class for specialized form elements:
   ```php
   namespace Application\Form;

   class Generic
   {
       // some code ...
   }
   ```
2. Next, we define some class constants, which will be generally useful in form element generation.
3. The first three will become keys associated with the major components of a single form element. We then define supported input types and defaults:
   ```php
   const ROW = 'row';
   const FORM = 'form';
   const INPUT = 'input';
   const LABEL = 'label';
   const ERRORS = 'errors';
   const TYPE_FORM = 'form';
   const TYPE_TEXT = 'text';
   const TYPE_EMAIL = 'email';
   const TYPE_RADIO = 'radio';
   const TYPE_SUBMIT = 'submit';
   const TYPE_SELECT = 'select';
   const TYPE_PASSWORD = 'password';
   const TYPE_CHECKBOX = 'checkbox';
   const DEFAULT_TYPE = self::TYPE_TEXT;
   const DEFAULT_WRAPPER = 'div';
   ```

4. Next, we can define properties and a constructor that sets them.
5. In this example, we require two properties, `$name` and `$type`, as we cannot effectively use the element without these attributes. The other constructor arguments are optional. Furthermore, in order to base one form element on another, we include a provision whereby the second argument, `$type`, can alternatively be an instance of `Application\Form\Generic`, in which case we simply run the getters (discussed later) to populate properties:

   ```php
   protected $name;
   protected $type = self::DEFAULT_TYPE;
   protected $label = '';
   protected $errors = array();
   protected $wrappers;
   protected $attributes; // HTML form attributes
   protected $pattern = '<input type="$$" name="$s" $s>';
   ```

   ```php
   public function __construct($name,
                               $type,
                               $label = '',
                               array $wrappers = array(),
                               array $attributes = array(),
                               array $errors = array())
   {
       $this->name = $name;
       if ($type instanceof Generic) {
           $this->type    = $type->getType();
           $this->label   = $type->getLabelValue();
           $this->errors  = $type->getErrorsArray();
           $this->wrappers = $type->getWrappers();
           $this->attributes = $type->getAttributes();
       } else {
           $this->type    = $type ?? self::DEFAULT_TYPE;
           $this->label   = $label;
           $this->errors  = $errors;
           $this->attributes = $attributes;
           if ($wrappers) {
               $this->wrappers = $wrappers;
           } else {
               $this->wrappers[self::INPUT]['type'] = self::DEFAULT_WRAPPER;
               $this->wrappers[self::LABEL]['type'] = self::DEFAULT_WRAPPER;
               $this->wrappers[self::ERRORS]['type'] = self::DEFAULT_WRAPPER;
           }
       }
       $this->attributes['id'] = $name;
   }
   ```

> Note that `$wrappers` has three primary subkeys: `INPUT`, `LABEL`, and `ERRORS`. This allows us to define separate wrappers for labels, the input tag, and errors.

6. Before defining the core methods that will produce HTML for the label, input tag, and errors, we should define a `getWrapperPattern()` method, which will produce the appropriate wrapping tags for the label, input, and error display.
7. If, for example, the wrapper is defined as `<div>`, and its attributes include `['class' => 'label']`, this method will return a `sprintf()` format pattern that looks like this: `<div class="label">%s</div>`. The final HTML produced for the label, for example, would then replace `%s`.
8. Here is how the `getWrapperPattern()` method might look:
   ```php
   public function getWrapperPattern($type)
   {
       $pattern = '<' . $this->wrappers[$type]['type'];
       foreach ($this->wrappers[$type] as $key => $value) {
           if ($key != 'type') {
               $pattern .= ' ' . $key . '="' . $value . '"';
           }
       }
       $pattern .= '>' . $s . '</' . $this->wrappers[$type]['type'] . '>';
       return $pattern;
   }
   ```

9. We are now ready to define the `getLabel()` method. All this method needs to do is to plug the label into the wrapper using `sprintf()`:
   ```php
   public function getLabel()
   {
       return sprintf($this->getWrapperPattern(self::LABEL),
                      $this->label);
   }
   ```

10. In order to produce the core input tag, we need a way to assemble the attributes. Fortunately, this is easily accomplished as long as they are supplied to the constructor in the form of an associative array. All we need to do, in this case, is to define a `getAttrs()` method that produces a string of key-value pairs separated by a space. We return the final value using `trim()` to remove excess spaces.
