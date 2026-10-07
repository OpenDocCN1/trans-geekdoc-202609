Web interface available at http://0.0.0.0:9393

Gathering targets...
Retrieved 20 repositories from michenriks

Analyzing 20 repositories...

```
MODIFY: Contains word: credential
Path......: credentials.json
Repo......: michenriks/searchpath
Message...: Update passwords
Author....: Michael Henriksen <michenriks@neomailbox.ch>
File URL.... https://github.com/michenriks/searchpath/blob/
a245aee..[truncated]
Commit URL: https://github.com/michenriks/searchpath/commit/
a245aee..[truncated]
```

```
MODIFY: Contains word: credential
Path......: credentials.json
Repo......: michenriks/searchpath
Message...: Update passwords
Author....: Michael Henriksen <michenriks@neomailbox.ch>
File URL.... https://github.com/michenriks/searchpath/blob/
ff908..
[truncated]
Commit URL: https://github.com/michenriks/searchpath/commit/
ff908c..[truncated]
```

+   Findings....: 2
Files......: 539
Commits....: 225
Repositories: 20
Targets....: 1

Press Ctrl+C to stop web server and exit.

The difference in results is immediately visible. Gitrob provides a description of what “interesting” items are detected, and their location. In the case of this repository, the results show that certain files contain the word “credential.”

Now when we access the web server, we can see a more detailed list of the discovered items. Figure 13.9 shows each of the discovered items along with direct links to view them.

Gitrob is programmed to search for things like SSL keys, stored credentials, and a slew of other information. If you come across a data-rich repository, this screen will be lit up with information.