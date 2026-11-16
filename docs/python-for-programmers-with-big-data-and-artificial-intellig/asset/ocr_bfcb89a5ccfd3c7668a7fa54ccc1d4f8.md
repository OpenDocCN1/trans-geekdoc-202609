# Sample Tweet JSON

Let's look at sample JSON for the following tweet from the @nasa account:

lick here to view code image

> @NoFear1075 Great question, Anthony! Throughout its seven-year mission,
> our Parker #SolarProbe spacecraft... https://t.co/xKd6ym8waT'

We added line numbers and reformatted some of the JSON due to wrapping. Note that
some fields in Tweet JSON are not supported in every Twitter API method; such
differences are explained in the online documentation for each method.

lick here to view code image

```
1 {'created_at': 'Wed Sep 05 18:19:34 +0000 2018',
2 'id': 1037404890354606082,
3 'id_str': '1037404890354606082',
4 'text': '@NoFear1075 Great question, Anthony! Throughout its seven-year mission, our Parker #SolarProbe spacecraft https://t.co/xKd6ym8waT',
5 'truncated': True,
6 'entities': {'hashtags': [{'text': 'SolarProbe', 'indices': [84, 95]}]},
7 'symbols': [],
8 'user_mentions': [{'screen_name': 'NoFear1075',
9 'name': 'Anthony Perrone',
10 'id': 284339791,
11 'id_str': '284339791',
12 'indices': [0, 11]}],
13 'urls': [{'url': 'https://t.co/xKd6ym8waT',
14 'expanded_url': 'https://twitter.com/i/web/status/ 1037404890354606082',
15 'display_url': 'twitter.com/i/web/status/l',
16 'indices': [[117, 140]]}]},
17 'source': '<a href="http://twitter.com" rel="nofollow">Twitter Web Client</a>',
18 'in_reply_to_status_id': 1037390542424956928,
19 'in_reply_to_status_id_str': '1037390542424956928',
20 'in_reply_to_user_id': 284339791,
21 'in_reply_to_user_id_str': '284339791',
22 'in_reply_to_screen_name': 'NoFear1075',
23 'user': {'id': 11348282,
24 'id_str': '11348282',
25 'name': 'NASA',
26 'screen_name': 'NASA',
27 'location': '',
28 'description': 'Explore the universe and discover our home planet @NASA. We usually post in EST (UTC-5)',
29 'url': 'https://t.co/TcEE6NS8nD',
30 'entities': {'url': {'urls': [{'url': 'https://t.co/TcEE6NS8nD',
```