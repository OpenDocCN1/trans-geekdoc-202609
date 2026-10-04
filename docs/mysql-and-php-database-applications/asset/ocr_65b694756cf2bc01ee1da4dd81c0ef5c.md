# Part V: Appendices

```
#
#route-addr = "< [route] addr-spec ""
#
#route = 1#("@" domain) : : path-relative
#
#addr-spec = local-part "@" domain : global address
#
#local-part = word(".*") word : uninterpreted
# : case-preserved
#
#domain = sub-domain(".*") sub-domain
#
#sub-domain = domain-ref / domain-literal
#
#domain-ref = atom : symbolic reference
#
#atom = 1<any CHAR except specials
```