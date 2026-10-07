

## 第 14 章 = 公开访问的数据存储 315

这是来自一个服务器的典型 ES 输出。注意文件开头有 -----Results: IP。这希望有助于日后更容易搜索和清理这些内容。

你可能想要使用的流程是搜索某些关键词并删除其他所有内容。你可以使用 `--filter` 参数来实现这一点。我不建议在搜索的此阶段使用该选项，因为如果你只查看索引名称，将会错过很多重要的结果。

## 搜索

`search` 参数将通过查看数据库中每个索引的映射表（mappings table），对 Elasticsearch 数据库进行更深层的查询。这等同于查看表头。使用此选项通常更有用，因为实际索引可能会被掩盖，或者不是你感兴趣的内容。映射文件将向你准确显示每个索引中包含什么类型的数据。

`dump` 参数将使用 Elasticsearch 导出 IP 地址内的所有索引。请谨慎使用此命令，因为它将下载所有内容。如果 Elasticsearch 使用索引名称作为 JSON 文件名，则你不需要指定输出文件名。

输出结果极有可能是巨大的，因此请准备好处理大文件。输出看起来如下：

```
[root ] > python3 -py es -tf es-list.txt -s search

{"type":"keyword", "timezone":{"type":"keyword"},"host":{"type":"keyword"},"hostname":{"type":"keyword"},"jsessionid":{"type":"keyword"},"level":{"type":"keyword"},"logger_name":{"type":"keyword"},"message":{"type":"keyword"},"messageId":{"type":"keyword"},"requestUri":{"type":"keyword"},"requestedSessionId":{"type":"keyword"},"requestedSessionIdCookie":{"type":"keyword"},"requestedSessionId":{"type":"keyword"},"service":{"type":"keyword"},"sessionId":{"type":"keyword"},"trace_id":{"type":"keyword"},"subscription":{"type":"keyword"},"system":{"type":"keyword"},"tags":{"type":"keyword"},"thread_name":{"type":"keyword"},"type":{"type":"keyword"},"user":{"type":"keyword"},"userId":{"type":"keyword"},"userIp":{"type":"keyword"},"userAgent":{"dynamic":true,"properties":{"build":{"type":"keyword"},"device":{"type":"keyword"},"keyword":{"type":"keyword"},"major":{"type":"keyword"},"minor":{"type":"keyword"},"name":{"type":"keyword"},"os":{"type":"keyword"},"os_major":{"type":"keyword"},"keyword":{"type":"keyword"},"os_minor":{"type":"keyword"},"os_name":{"type":"keyword"},"keyword":{"type":"keyword"},"patch":{"type":"keyword"}},"x-forwarded-for":{"type":"text"},"x-forwarded-host":{"type":"keyword"},"x-forwarded-port":{"type":"keyword"},"x-forwarded-server":{"type":"keyword"},"keyword":{"type":"keyword"}}
```

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
useragent":"{"dynamic":true","properties":{"build":"{"type":"keyword"},
device":"{"type":"keyword"},major":"{"type":"keyword"},minor":"{"type":"keyword"},
os":"{"type":"keyword"},os_name":"{"type":"keyword"},
_{"typetypekeyword"},
patch":"{"type":"keyword"},x-forwarded-for":"{"type":"text"},x-forwarded-host":"{"type":"keyword"},x-forwarded-port":"{"type":"keyword"},x-forwarded-server":"{"type":"keyword"},
keyword":"{"type":"keyword"},x-prerender-token":"{"type":"keyword"},x-real-ip":"{"type":"keyword"},
request-id":"{"type":"keyword"}}\},
```

这是一个巨大的输出。输出看起来如下：

## 316 第三部分 挖掘黄金

## 14 公开访问的数据存储 317

（此处省略了重复的“14 公开访问的数据存储 317”行，以对应原文中的重复结构，但根据要求，实际翻译中应保持格式一致）

14 公开访问的数据存储 317

`matchdump` 参数是之前所有扫描和抓取方法的结合。它不是采取完全广泛的直接下载方法，而是允许你指定特定的标准。

