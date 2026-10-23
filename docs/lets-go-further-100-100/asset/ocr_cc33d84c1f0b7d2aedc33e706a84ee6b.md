+   - Lastly, the `scope` column will denote what *purpose* the token can be used for. Later in the book we'll also need to create and store *authentication tokens*, and most of the code and storage requirements for these is exactly the same as for our activation tokens. So instead of creating separate tables (and the code to interact with them), we’ll store them in one table with a value in the `scope` column to restrict the purpose that the token can be used for.

OK, with those explanations out of the way, you should be able to execute the ‘up’ migration with the following command:

```
$ migrate -path=./migrations -database=$GREENLIGHT_DB_DSN up
5/u create_tokens_table (21.568194ms)
```