```
$this->__blIsRedirectOnConstraintFailure = false;
};

$this->__arObjParameterMethodConstraintHash = Array();
$this->__arObjConstraintFailure = Array();
$this->__blHasRunConstraintTests = false;
}

function IsRedirectFollowingConstraintFailure() {
    return($this->__blIsRedirectOnConstraintFailure);
}

function GetOriginalRequestObjectFollowingConstraintFailure() {
    if ($this->__blIsRedirectOnConstraintFailure) {
        return($this->__objOriginalRequestObject);
    };
}

function SetRedirectOnConstraintFailure($blTrueOrFalse) {
    $this->__blRedirectOnConstraintFailure = $blTrueOrFalse;
}

function SetConstraintFailureRedirectTargetURL($strURL) {
    $this->__strConstraintFailureRedirectTargetURL = $strURL;
}

function SetConstraintFailureDefaultRedirectTargetURL($strURL) {
    $this->__strConstraintFailureDefaultRedirectTargetURL = $strURL;
}
function GetParameterValue($strParameter) {
    return($this->__arRequestVars[$strParameter]);
}

function GetParameters() {
    return($this->__arRequestVars);
}

function GetCookies() {
    return($this->__arCookieVars);
}

function GetPostVariables() {
    return($this->__arPostVariables);
}

function GetGetVariables() {
    return($this->__arGetVariables);
}

function AddConstraint($strParameter, $intMethod, $objConstraint) {
    $newHash["PARAMETER"] = $strParameter;
    $newHash["METHOD"] = $intMethod;
```