```
$states = array_merge($states)
.db_values_array("states"."state"."statename"."state")
);
return $states;
}
```

Uses the $db_values_array() function discussed earlier in this chapter, in the section "Reusable functions" to get an array of countries and their abbreviations.

FETCH_QUESTION() This function grabs the contents of a row in the questions table and assigns the columns to global variables.

```
function fetch_question($question_id="")
{
  if (empty($question_id)) { $question_id = 0; }
  $result = fetch_record("questions"."question_id",$question_id);
  return $result;
}
```

This will run the fetch_record() function and return from the database all the information regarding a particular question, based on the question.

FETCH_USER() This function grabs the contents of a row in the users table and assigns the columns to global variables.

```
function fetch_user($user_id="")
{
  if (empty($user_id)) { $user_id = 0; }
  $result = fetch_record("users"."user_id",$user_id);
  return $result;
}
```

This returns the result set based on a user_id.

# Interesting Code Flow

There are a few pages in this application that could stand some explanation. However, you should be able to follow most of them if you understand the functions in the previous section.

# admin_question.php

This is a fairly lengthy page, and for good reason: it is used for adding, editing, and deleting questions in the database. The portion of the page that will be run will