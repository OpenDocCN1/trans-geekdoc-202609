+   4. The user subsequently submits their token to a new `PUT /v1/users/activated` endpoint.
+   5. If the hash of the token exists in the `tokens` table and hasn’t expired, then we’ll update the `activated` status for the relevant user to `true`.
+   6. Lastly, we’ll delete the activation token from our `tokens` table so that it can’t be used again.

In this section of the book, you’ll learn how to:

+   - Implement a secure ‘account activation’ workflow which verifies a new user’s email address.
+   - Generate cryptographically-secure random tokens using Go’s `crypto/rand` and `encoding/base32` packages.
+   - Generate fast hashes of data using the `crypto/sha256` package.
+   - Implement patterns for working with cross-table relationships in your database, including setting up foreign keys and retrieving related data via SQL `JOIN` queries.