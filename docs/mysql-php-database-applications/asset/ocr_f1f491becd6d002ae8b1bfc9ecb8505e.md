# TABLE F-27 PAYFLOW PRO FUNCTIONS

| Function | Return Value | Action |
| :--- | :--- | :--- |
| pfpro_version() | string | Returns the version of the Payflow Pro library |
| pfpro_init() | void | Initializes the Payflow Pro library |
| pfpro_cleanup() | void | Shuts down the Payflow Pro library |
| pfpro_process_raw(string parmlist [, string hostaddress [, int port [, int timeout [, string proxyAddress [, int proxyPort [, string proxyLogon [, string proxyPassword]]]]]]) | string | Raw Payflow Pro transaction processing |
| pfpro_process(array parmlist [, string hostaddress [, int port [, int timeout [, string proxyAddress [, int proxyPort [, string proxyLogon [, string proxyPassword]]]]]]) | array | Payflow Pro transaction processing using arrays |

# TABLE F-28 PDF FUNCTIONS

| Function | Return Value | Action |
| :--- | :--- | :--- |
| pdf_set_info(int pdfdoc, string fieldname, string value) | bool | Fills an info field of the document |
| pdf_set_info_creator(int pdfdoc, string creator) | bool | Fills the creator field of the document |
| pdf_set_info_title(int pdfdoc, string title) | bool | Fills the title field of the document |
| pdf_set_info_subject(int pdfdoc, string subject) | bool | Fills the subject field of the document |