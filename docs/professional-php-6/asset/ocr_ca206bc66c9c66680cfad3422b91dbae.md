Examine the following source code, called request.phpm, in detail:

```
<?
require_once("constants.phpm");
require_once("constraint.phpm");
require_once("constraintfailure.phpm");
class request {
    private $_arGetVars;
    private $_arPostVars;
    private $_arCookieVars;
    private $_arRequestVars;
    private $_objOriginalRequestObject;

    private $_blIsRedirectFollowingConstraintFailure;

    private $_blRedirectOnConstraintFailure;
    private $_strConstraintFailureRedirectTargetURL;
    private $_strConstraintFailureDefaultRedirectTargetURL;

    private $_arObjParameterMethodConstraintHash;
    private $_arObjConstraintFailure;
    private $_hasRunConstraintTests;

    function __construct($check_for_cookie = true) {
    // Import variables
    global $_REQUEST;
    global $_GET;
    global $_POST;
    global $_COOKIE;
    $this->_arGetVars = $_GET;
    $this->_arPostVars = $_POST;
    $this->_arCookieVars = $_COOKIE;
    $this->_arRequestVars = $_REQUEST;
    if ($check_for_cookie) {
    if ($this->_arCookieVars["phprqcOriginalRequestObject"]) {
    $cookieVal = $this->_arRequestVars["phprqcOriginalRequestObject"];
    $this->_blIsRedirectFollowingConstraintFailure = true;
    if (strlen($cookieVal) > 0) {
    $strResult = setcookie ("phprqcOriginalRequestObject", "",
    time() - 3600, "/", "");
    $origObj = unserialize(stripslashes($cookieVal));
    $this->_objOriginalRequestObject = &$origObj;
    $this->_arRequestVars["phprqcOriginalRequestObject"] = "";
    $this->_arGetVars["phprqcOriginalRequestObject"] = "";
    $this->_arPostVars["phprqcOriginalRequestObject"] = "";
    };
    $this->_blIsRedirectOnConstraintFailure = true;
    } else {
    $this->_blIsRedirectOnConstraintFailure = false;
    };
    } else {
```