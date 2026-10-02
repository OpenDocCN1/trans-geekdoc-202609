
> About this query: it performs a join of url with url_content to obtain the actual content from the blob table as well as the other columns specified after the primary key value. These columns create a full-text index and are therefore searchable. Sphinx has a very flexible query language, allowing you to specify on which columns to search. Also, this query uses a WHERE clause to select records less than or equal to the value in the sphinx_counter table for the main index. This is the mechanism that applies an extent to the data being gathered.

3. The option sql_query_info provides a query to the search command-line program, which is good for running test queries against your index. Do note that this does not search against Sphinx through the Sphinx search daemon, searchd — it searches on the index itself, so it does not work with distributed indexes.

```
source url
{
    type            = mysql
    sql_host        = localhost
    sql_user        = narada
    sql_pass        = n@r@d@
    sql_db          = narada
    sql_port        = 9312
    sql_query_pre   = UPDATE sphinx_counter SET max_id=
                      (SELECT MAX(id) FROM url)
                      WHERE index_name = 'url'
    sql_query       = SELECT id, content FROM url_content
                      WHERE id <= (SELECT max_id
                                   FROM sphinx_counter
                                   WHERE index_name = 'url')
    sql_query_info  = SELECT * FROM url_content WHERE id=$id
}
```

4. The source for the delta index, url_delta, is defined. The notation url_delta : url means that url_delta will inherit every option from the data source URLs, unless otherwise overridden. In this case, the options sql_query_pre and sql_query are overridden to specify a different range than is used with the url data source. For the url_delta data source, all records greater than the max_id value for the data source url are specified:

```
source url_delta : url
{
    sql_query_pre   = UPDATE sphinx_counter SET max_id=
                      (SELECT MAX(id) FROM url)
                      WHERE index_name = 'url_delta'
    sql_query       = SELECT id, content FROM url_content
                      WHERE id > (SELECT max_id
                                  FROM sphinx_counter
                                  WHERE index_name = 'url')
}
```

5. The indexes are defined. The options shown here are the most important. The option source defines the data source that is used to build this index, in this case the source url is used. The option path specifies the path and base name of the actual index files. Other index options are omitted for the sake of brevity.

```
index url
{
    source      = url
    path        = /usr/local/sphinx/var/data/url
    ...
}
```

6. The delta index, url_delta, inherits everything from the index url, except path and source, which it overrides. Because the source for url_delta is also called url_delta, this is the data source that has a different range than url, hence url_delta is a smaller index composed of a smaller range, the topmost records, of the database table url.

```
index url_delta : url
{
    source      = url_delta
    path        = /usr/local/sphinx/var/data/url_delta
}
```

7. Next, the distributed index dist_url is defined. This is the glue that makes the delta index and main index work together as one index. Queries run against this distributed index without the user ever knowing that the index is made up of parts.

```
index dist_url
{
    type                = distributed
    agent               = localhost:3312:url
    agent               = localhost:3312:url_delta
    agent_connect_timeout = 1000
    agent_query_timeout = 3000
}
```

8. The final piece in making delta indexes work is that the indexer has another feature — index merging. This is the feature that you use at a given interval in which you merge the delta index into the main index or indexes. For the sake of having fast index regeneration of the delta index, you cannot allow your delta index to grow too large. The indexer configuration is simple enough, and the option mem_limit specifies how much memory is used for the indexer, when it runs, to generate indexes.

```
indexer
{
    # memory limit, in bytes, kilobytes (16384K) or megabytes (256M)
    # optional, default is 32M, max is 2047M, recommended is 256M to
    # 1024M
    mem_limit           = 32M
}
```

9. The searchd daemon is configured in the following section. The listen option specifies which port or socket the daemon binds to. In this case, none are specified, so all interfaces are used. The log option specifies the log for the searchd daemon — this log will log the status of the searchd daemon. The query_log option specifies a log used to log search queries run against searchd.

The other options set timeout values, max number of children to run, a pid file, maximum number of matches returned, and whether the searchd daemon can be restarted seamlessly after running the indexer.

Also listed is the option seamless_rotate. As mentioned, this feature makes it possible to have the delta index generated without users of the index noticing. When you run the indexer, searchd is seamlessly restarted once the indexer completes (kill HUP).

```
searchd
{
    log = /usr/local/sphinx/var/log/searchd.log
    query_log = /usr/local/sphinx/var/log/query.log
    read_timeout = 5
    client_timeout = 300
    max_children = 30
    pid_file = /usr/local/sphinx/var/log/searchd.pid
    max_matches = 1000
    seamless_rotate = 1
    preopen_indexes = 0
    unlink_old = 1
    mva_updates_pool = 1M
    max_packet_size = 8M
    max_filters = 256
    max_filter_values = 4096
}
```

## Merging Indexes

As mentioned already, you would have a primary index that you merge with a delta index on a particular frequency. In order to do this, you run the indexer program with the main and delta index names, as shown in the following code example:

```
sphinx@hanuman:~$ ./bin/indexer --merge url url_delta --rotate
Sphinx 0.9.9-rc2 (r1785)
Copyright (c) 2001-2009, Andrew Aksyonoff

using config file '/usr/local/sphinx/etc/sphinx.conf'...
FATAL: no merge source index 'url_detla'
sphinx@hanuman:~$ ./bin/indexer --merge url url_delta --rotate
Sphinx 0.9.9-rc2 (r1785)
Copyright (c) 2001-2009, Andrew Aksyonoff

using config file '/usr/local/sphinx/etc/sphinx.conf'...
merged 63.4 Kwords
merged in 0.424 sec
total 457 reads, 0.010 sec, 32.6 kb/call avg, 0.0 msec/call avg
total 60 writes, 0.051 sec, 246.2 kb/call avg, 0.8 msec/call avg
rotating indices: successfully sent SIGHUP to searchd (pid=9238).
```

The --rotate argument simply means that searchd is restarted seamlessly after the index is finished being merged.

## DEVELOPING APPLICATIONS THAT USE SPHINX

In applications you write yourself, you have to implement the same type of functionality that the search utility gives you, except you’ll use the Sphinx client API, whereas the search utility performs the search on an index at a file-level. To use Sphinx, your application will perform a search against Sphinx on whatever index you specify, obtaining the unique document or record IDs of the results found in your search, and then you query MySQL against the table of the data source with those IDs to obtain the results from the database. With these results, you can generate excerpts. As part of the Sphinx API, Sphinx includes the means for generating excerpts — which are text with the original search terms enclosed in HTML tags, such as bold, emphasis, and so on (<b> . . </b>), to highlight the original search terms.

## Sphinx and PHP

The Sphinx source distribution comes with an API for PHP and is a pure PHP implementation for the SphinxAPI. You can find the main PHP API file in the api directory in the top-level source directory as the file sphinxapi.php. Ensure this file is copied to a location where you put common PHP library files. In this example, /usr/lib/php5 is used (Ubuntu). To begin using Sphinx with PHP, a simple program, sphinx_ch09.php, is written that uses the sakila database and a distributed index called film_dist which is the full-text index of the sakila table film.

Like so many client APIs, the first thing you need to do is to instantiate a client object and then connect to a server or servers

```
require('/usr/lib/php5/sphinxapi.php');

# mysql options
$dbhost = '192.168.1.106';
$dbuser = 'sakila';
$dbpass = 's@k1la';
$dbschema = 'sakila';

# connect to mysql
$dbh = new mysqli($dbhost, $dbuser, $dbpass, $dbschema);

# sphinx host and port
$host = '192.168.1.106';
$port = 9312;
# instantiate a SphinxClient object
$sphinx= new SphinxClient();
# connect to the server
$sphinx->SetServer($host, $port);
# set match mode
$sphinx->SetMatchMode(SPH_MATCH_EXTENDED2);
# set the sort mode
$sphinx->SetSortMode(SPH_SORT_ASC);

# the index to perform searches against
```
