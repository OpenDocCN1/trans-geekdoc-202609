In the new task screen, set URI Spider with the initial host target set to our target. Included in the options are the spider depth (default is 10), and a limit to the maximum number of pages to spider. The default configuration will extract DNS Record types, PhoneNumbers, and EmailAddress entity in the content of the page. When looking to extract metadata, it is important to set the extract-uris option to be true. Figure 12.8 shows the URI Spider screen with these options set this way.

# Start

| Task | URI Spider |
|---|---|
| Entity Type | Urn |
| Entity Name | http://www... |
| limit | 100 |
| max_depth | 10 |
| spider_whitelist | (current domain) |
| extract_dns_records | true |
| extract_dns_record_pattern | (current domain) |
| extract_email_addresses | true |
| extract_phone_numbers | true |
| parse_file_metadata | true |
| extract_uris | true |
| user_agent | Mozilla/5.0 (Macintosh; Intel Mac OS X 10_10_2) AppleWeb |
| Machine | Org Asset Discovery (Active) 'Machine' specifies the post-processor for each new entity. |
| Iterations | 3 Iterations 'iterations' specifies the depth to which the machine is runs. Auto Enrich

Figure 12.8