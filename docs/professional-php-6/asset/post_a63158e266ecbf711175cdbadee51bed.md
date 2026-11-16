
| Method | Role |
| :--- | :--- |
| IsRedirectFollowingConstraintFailure | If the page being displayed has been automatically loaded following a 302 redirect issued as a result of a constraint test failure, then this method returns true. |
| GetOriginalRequestObjectFollowingConstraintFailure | If the page being displayed has been automatically loaded following a 302 redirect issued as a result of a constraint test failure, then this method returns the request object that existed when that page was called, just before the constraint tests failed. |
| SetRedirectOnConstraintFailure | Accepting `true` or `false` as a parameter, this method enables you to tell the `request` object whether it should perform a 302 redirect upon any constraint tests failing. The target for that redirect is set using the `SetConstraintFailureRedirectTargetURL` and `SetConstraintFailureDefaultRedirectTargetURL` methods. |
| SetConstraintFailureRedirectTargetURL | Sets the target for a 302 redirect following a constraint failure. If one is not set, then either the referring page (which is normally the desired target) is used or, if that is not available, a default URL is used (which is set using the `SetConstraintFailureDefaultRedirectTargetURL` method). |
| SetConstraintFailureDefaultRedirectTargetURL | In the event that no target URL is set using the preceding accessor method, the referring page is used should a referral become necessary as a result of a constraint test failing. If no referring page is available (for example, as a result of a user visiting from a bookmark), the default URL specified using this method is used instead. |
| GetParameterValue | Returns the value of the specified parameter. This value is pulled directly from `$_REQUEST`, so the precedence of search for GET variables, POST variables, and COOKIE variables depends on PHP's overall configuration. |
| GetParameters | Returns a hash of parameters — essentially, a direct copy of `$_REQUEST` |
| GetCookies | Returns a hash of cookies — essentially, a direct copy of `$_COOKIE` |
| GetPostVariables | Returns a hash of `POST` variables — essentially, a direct copy of `$_POST` |
| GetGetVariables | Returns a hash of `GET` variables — essentially, a direct copy of `$_GET` |
| `AddConstraint` | Adds a constraint to this request. A constraint is applied to a single parameter and specifies a condition that must be met in order for that constraint to be considered met.<br>This method takes the name of the parameter, the delivery method (`VERB_METHOD_GET`, `VERB_METHOD_POST`, or `VERB_METHOD_COOKIE` as a constant) and a constraint object (discussed shortly) as its parameters. After a constraint is added, it cannot be removed. More than one constraint may be applied to a single parameter. |
| `TestConstraints` | Tests each constraint in turn and makes a note of any that fail by populating the member variable `$_arObjConstraintFailure`, accessible using `GetConstraintFailure`. In the event that `$_blRedirectOnConstraintFailure` is set to `true`, it redirects automatically to the appropriate URL, having first issued a temporary cookie that is a serialized representation of the current `request` object. |
| `GetConstraintFailures` | When a call to `TestConstraints()` indicates that one or more constraints fail, this method will return an array of `ConstraintFailure` objects representing all such failures. This method will need to be accessed from the original `request` object, accessed using `GetOriginalRequestObject() FollowingConstraintFailure` (described earlier in this table). |

Don't worry if the theory isn't quite clear from Table 13-3. Later in this chapter, you'll find a practical example showing how to employ this class and the rest of the toolkit in the real world. All should become clear then.

Now let's take a look at the `Constraint` class and its close cousin, the `ConstraintFailure` class.

## The Constraint Class

The `Constraint` class exists only as an object-oriented encapsulator. It does not concern itself with the code necessary to test whether the constraint is passed. As you have just seen, this is handled by the `request` object.

Enter the following code in a file called `constraint.php`:

```php
<?php
require_once("constants.php");
class constraint {
   private $_intConstraintType;
   private $_strConstraintOperand;

   function __construct($intConstraintType, $strConstraintOperand) {
       $this->_intConstraintType = $intConstraintType;
       $this->_strConstraintOperand = $strConstraintOperand;
   }

   function GetConstraintType() {
       return($this->_intConstraintType);
   }

   function GetConstraintOperand() {
       return($this->_strConstraintOperand);
   }
}
?>
```

Note how the constructor takes the constraint type (chosen from one of the constraint types that have been enumerated as constants) as its first parameter, and the operand as its second parameter. The meaning of the operand depends on the type of constraint. Its interpretation is up to the request object in its implementation of each type of constraint. For example, for a CT_MAXLENGTH constraint, the operand should contain the maximum length of the parameter. For a CT_PERMITTEDCHARS constraint, the operand should contain a string containing all permitted characters that may exist in the parameter.

To accommodate this flexibility, the operand is a string. However, it will be cast back to its most appropriate native form when the test takes place.

Note that you do not store the name of the parameter being tested in a constraint object. A constraint is simply a condition, and it can be applied to any (or even multiple) parameters using the methods in the request object. For that reason, to encapsulate neatly any given failure of a constraint, you must also store the parameter and delivery method that have provoked the failure. This is done using an instance of the ConstraintFailure class.

## The ConstraintFailure Class

A ConstraintFailure object is instantiated whenever a particular constraint fails. Its constructor expects the name of the parameter, the delivery method (VERB_METHOD_GET, VERB_METHOD_POST, or VERB_METHOD_COOKIE), and the original constraint object that caused the failure.

In normal use, the GetFailedConstraintObject method will be used to determine the nature of the constraint that failed through the use of the native Constraint class methods described previously.

Take a look at the following code, in a file called constraintfailure.php:

```php
<?php
require_once("constants.php");
require_once("constraint.php");
class constraintfailure {
    private $_strParameterName;
    private $_intVerbMethod;
    private $_objFailedConstraintObject;

    function __construct($strParameterName, $intVerbMethod,
                $objFailedConstraintObject) {
        $this->__strParameterName = $strParameterName;
        $this->__intVerbMethod = $intVerbMethod;
        $this->__objFailedConstraintObject = $objFailedConstraintObject;
    }

    function GetParameterName() {
        return($this->__strParameterName);
    }

    function GetVerbMethod() {
        return($this->__intVerbMethod);
    }

    function GetFailedConstraintObject() {
        return($this->__objFailedConstraintObject);
    }
};
?>
```

This class neatly encapsulates a failure that has occurred as a result of the user's input to the page not meeting your acceptance criteria.

As shown in the preceding code, it contains the name of the parameter that has failed, the method (GET, POST, or Cookie) in which the parameter was passed, and the constraint (expressed as a constraint object) test that has failed.

Instances of this object can be retrieved from the Request class using the GetConstraintFailures method, provided that the Request class has been instantiated in the context of a 302 redirect following redirection caused by constraint failures.

## Using the Toolkit

Now that you've learned a little bit about the basic classes that constitute the toolkit, it's worth looking at how you'd go about implementing this in a real-world application.

You'll also see in this example a practical case of an MVC approach as defined earlier in the chapter — namely, the use of native PHP templating. (The section “True Templating” later in this chapter goes into further detail about how this works.)

Assume that you have a search engine consisting of two pages: a search page in which the terms are entered, and a search terms page in which the results are displayed.

### search.php

The initial search controller has the following jobs:

- Require all the necessary components.
- Define the template file (search.phtml).
