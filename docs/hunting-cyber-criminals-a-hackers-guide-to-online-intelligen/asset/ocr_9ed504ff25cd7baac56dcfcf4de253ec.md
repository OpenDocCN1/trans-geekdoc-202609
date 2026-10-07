# 316 Part III — Digging for Gold

```
"x-prerender-token":{"type": "keyword"}, x-real-ip":{"type":
keyword"}, x-request-id":{"type": "keyword}}\}, ERROR":{all:
"enabled":false,"dynamic_templates":{{match_field":"{match",
match_mapping_type":"string","mapping":"{"index":"analyzed",
type":"string"},string_fields":{{"match":"*","match_mapping_type":
"string","mapping":"{"index":"not_analyzed","type":"string"}},}}
properties":{{\@timestamp":"{"type":"date"},ga_cid":"{"type":"keyword"},
mxpl_cd":"{"type":"keyword"},mxpl_cm":"{"type":"keyword"},
mxpl_cw":"{"type":"keyword"},accept":"{"type":"keyword"},
accept-encoding":"{"type":"keyword"},accept-language":"{"type":
keyword"},agent":"{"type":"keyword"},application_name":"{"type":
keyword"},version":"{"type":"keyword"},cf-connecting-ip":
{"type":"keyword"},cf-ipcountry":"{"type":"keyword"},cf-ray":"{"type":
"},type":"{"type":"keyword"},cf-visitor":"{"type":"keyword"},clientip":"{"type":
keyword"},connection":"{"type":"keyword"},dos":"{"type":"keyword"},dos_ga_clientid":"{"type":
keyword"},dos_mixpanel_clientid":"{"type":"keyword"},environment":
{"type":"keyword"},geo":"{"dynamic":"true","properties":{"area_code":
long":"{"float"},longitude":"{"float"},postal_code":"{"type":"keyword"},
keyword":"{"double"},city_name":"{"type":"text"},continent_code":"{"type":
keyword"},country_code":"{"type":"keyword"},country_name":"{"type":
keyword"},dma_code":"{"type":"long"},ip":"{"type":"keyword"},
latitude":"{"float"},location":"{"type":"geo_point",nlongitude":"{"float"},postal_code":"{"type":"keyword"},
real_name":"{"type":"keyword"},region_code":"{"type":"keyword"},
region_name":"{"type":"keyword"},timezone":"{"type":"keyword"},
host":"{"type":"keyword"},hostname":"{"type":"keyword"},jsessionid
{"type":"keyword"},level":"{"type":"keyword"},logger_name":"{"type":
keyword"},message":"{"type":"text"},planned":"{"type":"keyword"},
request-id":"{"type":"keyword"},session_id":"{"type":"keyword"},
requestedSessionIdFromCookie":"{"type":"keyword"},
requestedSessionIdValue":"{"type":"keyword"},service":"{"type":
keyword"},sessionid":"{"type":"keyword"},stack_trace":"{"type":
text"},tags":"{"type":"keyword"},system":"{"type":"keyword"},
tags":"{"type":"keyword"},thread_name":"{"type":"keyword"},
user":"{"type":"keyword"},userId":"{"type":"keyword"},
useragent":"{"dynamic":"true","properties":{"build":
device":"{"type":"keyword"},major":"{"type":
keyword"},method":"{"type":"keyword"},os":"{"type":
keyword"},origin":"{"type":"keyword"},minor":"{"type":
os_name":"{"type":"keyword"},patch":"{"type":"keyword"},
x-forwarded-for":"{"type":"text"},x-forwarded-host":"{"type":"keyword"},
x-forwarded-port":"{"type":"keyword"},x-forwarded-proto":"{"type":
keyword"},x-forwarded-server":"{"type":"keyword"},x-prerender-token":
{"type":"keyword"},x-real-ip":"{"type":"keyword"},x-
request-id":"{"type":"keyword"}}\},
```

This is a huge mess, but if you look closer at the results, you will notice
sothing really interesting. The headers include keywords like ip, latitude,
geo, geocode, and userid.