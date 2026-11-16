The conditions that apply in the following example relate to the only search parameter passed to the script — the search string provided by the user. It must contain between 4 and 11 characters, which must be letters, not numbers:

> Do not try to run this code directly in your Web browser. It expects to be invoked from the search page.

```
<?
require_once("constants.php");
require_once("request.php");
require_once("constraint.phpm");
require_once("constraintfailure.phpm");

$strTemplateFile = "searchresults.phtml";

$displayHash = Array();
session_start();

if ($_POST) {
    $objRequest = new request();
    $objRequest->SetRedirectOnConstraintFailure(true);

    $objConstraint = new constraint(CT_MINLENGTH, "3");
    $objRequest->AddConstraint("typeofSteak", VERB_METHOD_POST, $objConstraint);
    $objConstraint = new constraint(CT_MAXLENGTH, "12");
    $objRequest->AddConstraint("typeofSteak", VERB_METHOD_POST, $objConstraint);
    $objConstraint = new constraint(CT_PERMITTEDCHARACTERS,
    "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz");
    $objRequest->AddConstraint("typeofSteak", VERB_METHOD_POST, $objConstraint);

    $objRequest->SetConstraintFailureDefaultRedirectURL("/search.php");
    $objRequest->TestConstraints();

    # If we've got this far, tests have been passed - perform the search.
    $displayHash["RESULTS"] = Array();
    $arSteaks = array("fillet", "rump", "sirloin", "burnt");

    for ($i=0; $i<sizeof($arSteaks)-1; $i++) {
        if (! (strpos (trim(strtolower ($arSteaks[$i])),
        strtolower (trim($objRequest->
        >GetParameterValue("typeofSteak")))))
        == false) {
            array_push($displayHash["RESULTS"], $arSteaks[$i]);
        }
    };

    $_SESSION['dh'] = $displayHash;
    header("Location: searchresults.php");
    exit(0);
}
```