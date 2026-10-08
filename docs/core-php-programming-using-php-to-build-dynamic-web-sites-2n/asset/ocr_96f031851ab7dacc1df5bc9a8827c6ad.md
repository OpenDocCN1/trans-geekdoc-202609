# Core PHP Programming

Note that both cursor_type and blob_id are optional. The ifx_query function will allow you to specify an array of blob identifiers for the third argument. See ifx_create_blob for an example of use.

# boolean ifx_textvarchar(integer mode)

Use ifx_textvarchar to control how text blobs are queried in queries. If mode is 0, blob IDs are returned. If mode is 1, blob contents are returned. See ifx_pconnect for an example of use.

# boolean ifx_update_blob(integer blob, string data)

The ifx_update_blob function changes the contents of a blob.

# boolean ifx_update_char(integer character, string data)

The ifx_update_char function changes the contents of a character object.

# ifx_close_slob

You can use ifx_close_slob as an alias for ifx_free_slob.

# integer ifx_create_slob(integer mode)

Use ifx_create_slob to create a slob object. The object identifier is returned. The modes listed in Table 13.4 may be combined with | operators.

Table 13.4. Informix Slob Modes

| Value | Informix Modes API Constant |
| 1 | LO_RDONLY |
| 2 | LO_WRONLY |
| 4 | LO_APPEND |
| 8 | LO_RDWR |
| 16 | LO_BUFFER |
| 32 | LO_NOBUFFER | |

# boolean ifx_free_slob(integer slob)

The ifx_free_slob function deletes a slob object.

# integer ifx_open_slob(integer slob, integer mode)

Use ifx_open_slob to get an identifier for an existing slob object. The modes listed in Table 13.4 may be combined with | operators.