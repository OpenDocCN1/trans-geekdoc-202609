
```
# Available options: DRIZZLE_CON_MYSQL
$NaradaDBOptions= 0;
# Whether to enable debugging.
$NaradaDebug= true;

#
# Insert Worker Configuration.
#

# Name of the function the insert worker will register.
$NaradaInsertFunctionName= 'NaradaInsert';

#
# Fetch Worker Configuration.
#

# Name of the function the fetch worker will register.
$NaradaFetchFunctionName= 'NaradaFetch';

# Whether to crawl (search and insert) other URLs when fetching pages.
$NaradaFetchCrawl= true;

# Whether to limit crawling to URLs local to the original URL or not.
$NaradaFetchLocalURLs= true;

#
# Index Worker Configuration.
#
# Name of the function the index worker will register.
$NaradaIndexFunctionName= 'NaradaIndex';

# How often the index should run, per number of documents.
$NaradaIndexFrequency= 10;

# Command to execute when the indexer needs to run.
$NaradaIndexCommand= '/usr/local/sphinx/bin/indexer --rotate --all';

# How often the index timer should send a message to make sure unindexed
# documents eventually get indexed.
$NaradaIndexTimer= 60;

#
# Sphinx Configuration
#

# Path to the Sphinx PHP API. This needs to be included before the other Sphinx
# configuration in case API constants are used.
require('/usr/lib/php5/sphinxapi.php');

# Name of the function the search worker will register.
$NaradaSearchFunctionName= 'NaradaSearch';

# Name of the index to search
```
```php
$NaradaSearchIndex= 'dist_url';

# Name of the non-distributed excerpt index (for creating excerpts)
$NaradaExcerptIndex= 'url';

# Name of the Sphinx host
$NaradaSearchHost= 'localhost';

# Name of the Sphinx port
$NaradaSearchPort= 3312;

# Sphinx search mode
$NaradaSearchMode= SPH_MATCH_EXTENDED2;

?>
```

## The Narada Class

The next PHP code component of Narada is the Narada class. This class implements the bulk of the functionality needed for Narada, containing many of the methods that the various PHP Gearman workers — which are shown in the next section — will use.

First and foremost is the class definition:

```php
<?php
# Narada Search Engine in PHP
# Copyright (C) 2009 Eric Day, Patrick Galbraith
# All rights reserved.
#
# Use and distribution licensed under the BSD license.  See
# the COPYING file in this directory for full text.

# This is a helper/base class for all Narada components to use. It encapsulates
# common configuration and initialization of things like Gearman clients and
# workers.

require('NaradaConf.php');

#if ($GLOBALS['NaradaDebug'])
#  error_reporting(E_ALL | E_NOTICE | E_STRICT);

class Narada
{
    private $gearmanServers;
    private $gearmanClient;
    private $dbh;
    private $dbhCon;
    private $sphinx;
    private $sphinxIndex;
    private $sphinxHost;
    private $sphinxPort;
```
```php
private $sphinxMatchMode;
protected $functionName;
protected $fetchFunctionName;
protected $searchFunctionName;
protected $insertFunctionName;
protected $indexFunctionName;
```

The first method is the constructor, which performs the following:

- Obtains the Gearman job server list, parsing and initializing the list
- Sets the value of class variables for worker names
- Sets the class variables for Sphinx index, excerpt index, host, port, and search mode
- Connects to the memcached server pool
- Connects to MySQL

```php
public function __construct()
{
    $servers= explode(',', $GLOBALS['NaradaGearmanServers']);
    foreach ($servers as $server)
        $this->gearmanServers[]= explode(':', $server);

    $this->gearmanClient= new GearmanClient();

    foreach ($this->gearmanServers as $server)
        $this->gearmanClient->addServer($server[0], $server[1]);

    $this->fetchFunctionName= $GLOBALS['NaradaFetchFunctionName'];
    $this->searchFunctionName= $GLOBALS['NaradaSearchFunctionName'];
    $this->insertFunctionName= $GLOBALS['NaradaInsertFunctionName'];
    $this->indexFunctionName= $GLOBALS['NaradaIndexFunctionName'];

    $this->sphinx= NULL;
    $this->sphinxIndex= $GLOBALS['NaradaSearchIndex'];
    $this->sphinxExcerptIndex= $GLOBALS['NaradaExcerptIndex'];
    $this->sphinxHost= $GLOBALS['NaradaSearchHost'];
    $this->sphinxPort= $GLOBALS['NaradaSearchPort'];
    $this->sphinxMatchMode= $GLOBALS['NaradaSearchMode'];

    $this->memc= new Memcached();
    $this->memc->addServer($GLOBALS['NaradaMemcachedHost'],
        $GLOBALS['NaradaMemcachedPort']);

    $this->dbh= new mysqli($GLOBALS['NaradaDBHost'],
$GLOBALS['NaradaDBUser'],
        $GLOBALS['NaradaDBPass'],
        $GLOBALS['NaradaDB']);
    if ($GLOBALS['NaradaDBType'] == 'mysqli')
        $this->dbhCon= $this->dbh;
}
```

For the previous code, note the following:

The debug() method simply prints the messages that were passed to it if $GLOBALS['NaradaDebug'] is set. This method is useful for printing out various messages or var_dump() of PHP arrays when you are debugging Narada, should you want to extend it and submit the code to the project!

```
public function debug($msg)
{
    if ($GLOBALS['NaradaDebug'])
        print "$msg\n";
}
```

The insert() method performs an insert by way of requesting an insert job (backgrounded) from the Gearman job server using the gearman client API method, doBackground().

```
public function insert($url)
{
    $this->gearmanClient->doBackground($this->insertFunctionName, $url);
}
```

The search() method performs a search by way of the search worker, which it requests of the Gearman job server. It returns the results of the search (non-backgrounded worker) using the gearman client method do().

```
public function search($query)
{
    return $this->gearmanClient->do($this->searchFunctionName, $query);
}
```

The fetch() method requests the retrieval of the content of a page for a given URL by way of the fetch worker requested of gearmand as a background job.

```
protected function fetch($url)
{
    $this->gearmanClient->doBackground($this->fetchFunctionName, $url);
}
```

The index() method requests that the Sphinx indexes are re-indexed by way of the index worker requested of gearmand as a background worker.

```
public function index()
{
    $this->gearmanClient->doBackground($this->indexFunctionName, NULL);
}
```

The store() method, which is called by the insert worker, inserts the specified URL. This URL comes either from the initial submission on the index page of a URL or from a URL parsed by the fetch worker.

![](img/88e43d4c6a3d0e0d1f265975ce2f9f50_460_0.png)

> It's important to note that the store() method returns the insert id, which is the primary key value that is used for the subsequent insertion of the page content and title fetched from the page of the URL into the url_content table, maintaining the 1:1 relation between the url and url_content tables.

```
protected function store($url)
{
    $query= "INSERT INTO url (url_md5, url, created, last_updated)"
        . "VALUES ('" . md5($url) . "','"
        . $this->dbh->real_escape_string($url) .
        "', now(), now())";

    $result= @$this->dbhCon->query($query);
    if ($result)
    {
        $id= $this->dbhCon->insert_id;
        return $id;
    }

    return 0;
}
```

The storeContent() method is called by the fetch worker after the page content and title are retrieved and parsed for a given URL. Note the useful application of the INSERT INTO...ON DUPLICATE KEY UPDATE statement — explained more in Chapter 18 — which essentially means if the record exists for a given record, update it instead; otherwise insert it.

```
protected function storeContent($id, $title, $content)
{
    $query= "INSERT INTO url_content (id, title, content) VALUES ($id .
        "','" . $this->dbh->real_escape_string($title) .
        "','" . $this->dbh->real_escape_string($content) . "')" .
        "ON DUPLICATE KEY UPDATE content='" .
        $this->dbh->real_escape_string($content) . "'";

    $this->dbhCon->query($query);
}
```

The get() method is called by the fetch worker to obtain the URL, which is obtained using the workload that happens to be the id value for the given URL.

```
protected function get($id)
{
    $result= $this->dbhCon->query("SELECT url FROM url WHERE id=$id");
    if (!$result)
```
