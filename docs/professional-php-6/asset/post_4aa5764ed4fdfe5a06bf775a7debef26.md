
```php
$this->_blIsRedirectOnConstraintFailure = false;
}

$this->_arObjParameterMethodConstraintHash = Array();
$this->_arObjConstraintFailure = Array();
$this->_blHasRunConstraintTests = false;
}

function IsRedirectFollowingConstraintFailure() {
    return($this->_blIsRedirectOnConstraintFailure);
}

function GetOriginalRequestObjectFollowingConstraintFailure() {
    if ($this->_blIsRedirectOnConstraintFailure) {
        return($this->_objOriginalRequestObject);
    };
}

function SetRedirectOnConstraintFailure($blTrueOrFalse) {
    $this->_blRedirectOnConstraintFailure = $blTrueOrFalse;
}

function SetConstraintFailureRedirectTargetURL($strURL) {
    $this->_strConstraintFailureRedirectTargetURL = $strURL;
}

function SetConstraintFailureDefaultRedirectTargetURL($strURL) {
    $this->_strConstraintFailureDefaultRedirectTargetURL = $strURL;
}
function GetParameterValue($strParameter) {
    return($this->_arRequestVars[$strParameter]);
}

function GetParameters() {
    return($this->_arRequestVars);
}

function GetCookies() {
    return($this->_arCookieVars);
}

function GetPostVariables() {
    return($this->_arPostVars);
}

function GetGetVariables() {
    return($this->_arGetVars);
}

function AddConstraint($strParameter, $intMethod, $objConstraint) {
    $newHash["PARAMETER"] = $strParameter;
    $newHash["METHOD"] = $intMethod;
    $newHash["CONSTRAINT"] = $objConstraint;
    $this->_arObjParameterMethodConstraintHash[] = $newHash;
}

function TestConstraints() {
    $this->_blHasRunConstraintTests = true;
    $anyFail = false;
    for ($i=0; $i<=sizeof($this->_arObjParameterMethodConstraintHash) -1; $i++) {
        $strThisParameter =
            $this->_arObjParameterMethodConstraintHash[$i] ["PARAMETER"];
        $intThisMethod = $this->_arObjParameterMethodConstraintHash[$i] ["METHOD"];
        $objThisConstraint =
            $this->_arObjParameterMethodConstraintHash[$i] ["CONSTRAINT"];
        $varActualValue = "";
        if ($intThisMethod == VERB_METHOD_COOKIE) {
            $varActualValue = $this->_arCookieVars[$strThisParameter];
        }
        if ($intThisMethod == VERB_METHOD_GET) {
            $varActualValue = $this->_arGetVars[$strThisParameter];
        }
        if ($intThisMethod == VERB_METHOD_POST) {
            $varActualValue = $this->_arPostVars[$strThisParameter];
        }
        $intConstraintType = $objThisConstraint->GetConstraintType();
        $strConstraintOperand = $objThisConstraint->GetConstraintOperand();
        $thisFail = false;
        $objFailureObject = new constraintfailure($strThisParameter,
            $intThisMethod, $objThisConstraint);
        switch ($intConstraintType) {
        case CT_MINLENGTH:
            if (strlen((string)$varActualValue) < (integer) $strConstraintOperand) {
                $thisFail = true;
            };
            break;
        case CT_MAXLENGTH:
            if (strlen((string)$varActualValue) > (integer) $strConstraintOperand) {
                $thisFail = true;
            };
            break;
        case CT_PERMITTEDCHARACTERS:
            for ($j=0; $j<strlen($varActualValue)-1; $j++) {
                $thisChar = substr($varActualValue, $j, 1);
                if (strpos($strConstraintOperand, $thisChar) === false) {
                    $thisFail = true;
                };
            };
            break;
        case CT_NONPERMITTEDCHARACTERS:
            for ($j=0; $j<strlen($varActualValue)-1; $j++) {
                $thisChar = substr($varActualValue, $j, 1);
                if (! (strpos($strConstraintOperand, $thisChar) === false)) {
                    $thisFail = true;
                };
            };
            break;
        case CT_LESSTHAN:
            if ($varActualValue >= $strConstraintOperand) {
                $thisFail = true;
            }
            break;
        case CT_MORETHAN:
            if ($varActualValue <= $strConstraintOperand) {
                $thisFail = true;
            }
            break;
        case CT_EQUALTO:
            if ($varActualValue != $strConstraintOperand) {
                $thisFail = true;
            }
            break;
        case CT_NOTEQUALTO:
            if ($varActualValue == $strConstraintOperand) {
                $thisFail = true;
            }
            break;
        case CT_MUSTMATCHREGEXP:
            if (!preg_match($strConstraintOperand, $varActualValue)) {
                $thisFail = true;
            }
            break;
        case CT_MUSTNOTMATCHREGEXP:
            if (preg_match($strConstraintOperand, $varActualValue)) {
                $thisFail = true;
            }
            break;
        }
        if ($thisFail) {
            $anyFail = true;
            $this->_arObjConstraintFailure[] = $objFailureObject;
        }
    }

    if ($anyFail) {
        if ($this->_blRedirectOnConstraintFailure) {
            $targetURL = $_ENV["HTTP_REFERER"];
            if (!$targetURL) {
                $targetURL = $this->_strConstraintFailureDefaultRedirectTargetURL;
            }
            if ($this->_strConstraintFailureRedirectTargetURL) {
                $targetURL = $this->_strConstraintFailureRedirectTargetURL;
            }
            if ($targetURL) {
                $objToSerialize = $this;
                $strSerialization = serialize($objToSerialize);
                $strResult = setcookie ("phprqcOriginalRequestObject",
                    $strSerialization, time() + 3600, "/");
                header("Location: $targetURL");
                exit(0);
            }
        }
    }
    return(!($anyFail)); // Returns TRUE if all tests passed, otherwise returns FALSE
}
function GetConstraintFailures() {
    if (!$this->_blHasRunConstraintTests) {
        $this->TestConstraints();
    };
    return($this->_arObjConstraintFailure);
}
?>
```

Take a look at each of the member variables shown in Table 13-2. These are all private, and accessor methods are provided to get or set their useful values. Hungarian notation has been used — that is, a hint is included as to which data type each member variable should contain at the start of the variable's name.

## Table 13-2 Member Variables

| Member Variable | Role |
|---|---|
| `$_arGetVars` | A copy of `$_GET`, an associative array of HTTP `GET` variables passed in this request |
| `$_arPostVars` | A copy of `$_POST`, an associative array of HTTP `POST` variables passed in this request |
| `$_arCookieVars` | A copy of `$_COOKIE`, an associative array of pre-existing cookies passed in this request |
| `$_arRequestVars` | A copy of `$_REQUEST`, an associative array of `GET` and `POST` variables, as well as cookies, combined into one. Where `GET`/`POST` variables or cookies of the same name exist, precedence is determined by `PHP.INI`. |
| `$_objOriginalRequestObject` | In the event that the user has been redirected back to the original page by the `request` object as a result of passing parameters that failed constraint tests, this will contain a copy of the original request object supplied. |
| `$_blIsRedirectFollowingConstraintFailure` | A Boolean variable determining whether this `request` has been created as a result of a redirect following a constraint test failure |
| `$_blRedirectOnConstraintFailure` | In the event that a constraint test is failed, should the `request` object automatically redirect the browser back to the original page, or to some other URL? |

## Table 13-2 (continued)

| Member Variable | Role |
|---|---|
| `$_strConstraintFailureRedirectTargetURL` | In the event that a constraint test is failed and `_blRedirectOnConstraintFailure` is set to true, this specifies whether the request object should be diverted to a particular URL. If this is left blank, the referring URL shall be used. |
| `$_strConstraintFailureDefaultRedirectTargetURL` | In the event that `_strConstraintFailureRedirectTargetURL` is not set, `_blRedirectOnConstraintFailure` is set to true, and no referring URL is available, this specifies the URL to which the browser should be redirected. |
| `$_arObjParameterMethodConstraintHash` | An array of constraints, the indices of which contain three keyed components in a hash: the parameter name on which the constraint applies; the method in which this parameter is expected to be passed (as a constant); and the constraint object expressing the test to be applied. |
| `$_arObjConstraintFailure` | An array of constraint failure objects, should any constraints have failed, assuming that the tests have been run |
| `$_blHasRunConstraintTests` | A Boolean variable expressing whether the constraint tests have yet been run on this request object |

Table 13-3 shows the methods provided by the request object.

## Table 13-3 Methods Provided by the Request Object

| Method | Role |
|---|---|
| `__construct` | Instantiates the request object. Does not take any required parameters. Instead, it consults `$_REQUEST`, `$_POST`, `$_GET`, and `$_COOKIE`, and populates member variables (see Table 13-2) as appropriate. In addition, the existence of a cookie called `phpqcOriginalRequestObject` is checked for. Should it exist, another request object is assumed to be passed back as a result of throwback following constraint test failures. The cookie is nullified at this stage to prevent an infinite loop when the original request object is recreated. Its contents are then unserialized (via the `stripslashes` PHP function) into a new request object, which is then made available for interrogation through the `GetOriginalRequestObjectFollowingConstraintFailure` accessor method (detailed in this table). |

