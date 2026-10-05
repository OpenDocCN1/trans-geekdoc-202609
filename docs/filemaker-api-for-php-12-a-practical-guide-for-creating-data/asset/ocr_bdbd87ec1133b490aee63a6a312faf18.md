| Method | Syntax | Value | Lesson |

| getContainerData() | getContainerData() | string | |
| getContainerDataURL() | getContainerData($URL) | String | 12 |
| getErrors() | getErrors($FileName) | array | 12 |
| getFetchCount() | getFetchCount() | integer | 25 |
| getField() | getField($FileName, $Repetition) | string | N/A |
| getFieldTimestamp() | getFieldTimestamp($FileName, $Repetition) | integer | 35 |
| getFields() | getFields() | array | 27 |
| getFieldUnencoded() | getFieldUnencoded($FileName, $Repetition) | string | 36 |
| getFirstRecord() | $result = $request->getFirstRecord() | FileMarker_Record | 22 |
| getFoundSetCount() | getFoundSetCount() | integer | 14 |
| getLastRecord() | $result = $request->getLastRecord() | FileMarker_Record | 21 |
| getLayout() | getLayout() | FileMarker_Layout | 13 |
| getLocalValidationRules() | getLocalValidationRules() | array | N/A |
| getMessage() | getMessage() | string | 1 |
| getModificationID() | getModificationID() | integer | 20 |
| getName() | getName() | string | 25 |
| getParent() | getParent() | FileMarker_Record | N/A |
| getProperties() | getProperties() | array | N/A |
| getProperty() | getProperty($PropertyName) | string | N/A |
| getRecordByID() | getRecordByID($layoutName, $recordID) | FileMarker_Record | 4 |
| getRecordID() | getRecordID() | string | N/A |
| getRecords() | getRecords() | array | 1 |
| getRelatedSets() | getRelatedSets($tableName) | array | 8 |
| getRelatedSetsFilters() | getRelatedSetsFilters() | array | N/A |
| getRepetitionCount() | getRepetitionCount() | integer | N/A |
| getResult() | getResult() | string | 27 |
| getStyleType() | getStyleType() | string | N/A |
| getTableRecordCount() | getTableRecordCount() | integer | 14 |
| getTypeValue() | getTypeValue() | string | N/A |
| getValidationMask() | getValidationMask() | array | N/A |
| getValidationRules() | getValidationRules() | string | 13 |
| getValueList() | getValueList($valueList) | array | N/A |
| getValueTwoFields() | getValueListTwoFields($valueList) | array | N/A |
| hasValidationRule() | hasValidationRule($number) | Boolean | N/A |
| isAutoEntered() | isAutoEntered() | Boolean | N/A |
| isError() | isError() | Boolean | N/A |
| isValidationError() | isValidationError() | array | N/A |
| listFields() | listFields() | FileMarker | dbaccess.php |
| newFile() | newFile($DatabaseName, $HostSpec, $UserName, $Password) | FileMarker_Command | 5 |
| newCommand() | newCommand($layoutName, $fieldValues) | FileMarker_Command | 26 |
| newFindCommand() | newFindCommand($layoutName) | FileMarker_Command | N/A |
| newDeleteCommand() | newDeleteCommand($layoutName, $recordID) Note: As Document | |
| newDuplicateCommand() | newDuplicateCommand($layoutName, $recordID) | FileMarker_Command | 30 |
| newEditCommand() | newEditCommand($layoutName, $recordID, $fieldValues) | FileMarker_Command | 7 |
| newFindCommand() | newFindCommand($layoutName) | FileMarker_Command | 3 |
| newAllFindCommand() | newAllFindCommand($layoutName) | FileMarker_Command | 1 |
| newAnyFindCommand() | newAnyFindCommand($layoutName) | FileMarker_Command | 29 |
| newConfigRequest() | newConfigRequest($layoutName) | FileMarker_Command | 26 |