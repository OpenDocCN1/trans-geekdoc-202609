```
#
#route-addr  = "<" [route] addr-spec ">"
#
#route       = 1#("@" domain) ":"                ; path-relative
#
#addr-spec   = local-part "@" domain             ; global address
#
#local-part  = word *("." word)                  ; uninterpreted
#                                             ; case-preserved
#
#domain      = sub-domain *("." sub-domain)
#
#sub-domain  = domain-ref / domain-literal
#
#domain-ref  = atom                              ; symbolic reference
#
#atom        = 1*<any CHAR except specials, SPACE and CTLs>
#
#specials    = "(" / ")" / "<" / ">" / "@"       ; Must be in quoted-
#             / "," / ";" / ":" / "\" / "<>"     ; string, to use
#             / "." / "[" / "]"                  ; within a word.
#
#
#                                             ; ( Octal, Decimal.)
#CHAR        = <any ASCII character>             ; ( 0-177,  0.-127.)
#ALPHA       = <any ASCII alphabetic character>
#                                             ; (101-132, 65.- 90.)
#                                             ; (141-172, 97.-122.)
#DIGIT       = <any ASCII decimal digit>         ; ( 60- 71, 48.- 57.)
#CTL         = <any ASCII control                ; ( 0- 37,  0.- 31.)
#             character and DEL>                 ; ( 177,    127.)
#CR          = <ASCII CR, carriage return>       ; (   15,    13.)
#LF          = <ASCII LF, linefeed>              ; (   12,    10.)
#SPACE       = <ASCII SP, space>                 ; (   40,    32.)
#HTAB        = <ASCII HT, horizontal-tab>        ; (   11,     9.)
#"<>"        = <ASCII quote mark>                ; (   42,    34.)
#CRLF       = CR LF
#
#LWSP-char  = SPACE / HTAB                      ; semantics = SPACE
#
#linear-white-space = 1*([CRLF] LWSP-char)       ; semantics = SPACE
#                                             ; CRLF => folding
#
#delimiters  = specials / linear-white-space / comment
#
#text        = <any CHAR, including bare        ; => atoms, specials,
```