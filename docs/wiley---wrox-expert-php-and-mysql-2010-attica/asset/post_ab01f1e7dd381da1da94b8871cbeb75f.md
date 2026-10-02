
## TABLE 9-4 (continued)

| OPTION | DESCRIPTION |
|---|---|
| sql_ranged_throttle | If set, this option creates a delay between ranged queries, in milliseconds. |
| sql_attr_uint | Name of an unsigned integer column or columns that exist in the result set from the sql_query to index on. Also allows for bit size (foo:8) of the attribute. |
| sql_attr_bool | Name(s) of a Boolean column to index. Formally, to store as an attribute because attributes are not (yet) indexed. |
| sql_attr_bigint | Name(s) of bigint column to index. |
| sql_attr_timestamp | Name(s) of timestamp column to index. |
| sql_attr_str2ordinal | Name(s) of string column to index. |
| sql_attr_float | Floating-point column to index. |
| sql_attr_multi | Multi-valued attribute (MVA) attribute declaration. Syntax is ATTR-TYPE ATTR-NAME 'from' SOURCE-TYPE [;QUERY] [;RANGE-QUERY]

An example would be:

```
uint tag from query; SELECT id, tag FROM tags
```

or ranged:

```
uint tag from ranged-query; \
SELECT id, tag FROM tags WHERE id>=$start AND id<=$end; \
SELECT MIN(id), MAX(id) FROM tags
``` |
| sql_query_post | Query run after the main data gathering query. Can be used for a task such as cleanup. Can have multiple queries specified. |
| sql_query_post_index | Query to run after the index is generated. This is especially useful for updating the sphinx counter table. Can have multiple queries specified. |
| sql_query_killlist | Fetches document IDs for the kill-list. The kill-list suppresses matches from preceding indexes in the current query. The default for this option is off. |
| unpack_zlib | Columns to unpack on the index side when indexing multi-value, using zlib compression. |
| unpack_mysqlcompress | Columns to unpack on the index side when indexing multi-value, using mysql compression. |

| OPTION | DESCRIPTION |
|---|---|
| unpack_mysqlcompress_maxsize | Maximum unpack length when using MySQL compression. |
| xmlpipe_command | Path to command that is used to pipe an XML file to the indexer. |
| xmlpipe_field | Specifies unique fields to be indexed when using XML pipe. |
| xmlpipe_attr_xxx | Specifies attributes to be indexed when you use XML pipe (same types as sql_xx counterparts). |
| xmlpipe_fixup_utf8 | Performs UTF-8 validation and filter out invalid codes. Default is 0 (off). |

## Defining the sakila_main Data Source

To set up a data source using Sphinx with the sakila schema, as shown in the previous section using FULLTEXT indexes, start by defining the main data source:

```
source sakila_main
{
    sql_host      = localhost
    sql_user      = webuser
    sql_pass      = mypass
    sql_db        = sakila
    sql_port      = 9312  # optional, default is 9312
    sql_sock      = /tmp/mysql.sock
    sql_query     = SELECT film_id, title, description FROM film_text
    sql_query_info = SELECT * FROM film_text WHERE film_id=$id
}
```

## Defining the Indexes

Next, the main index is defined, film_main. The index is a data structure stored in a file on disk that is the result of building an index. Available index options are shown in Table 9-5:

## TABLE 9-5: Index Options

| OPTION | DESCRIPTION |
|---|---|
| source | Name of the data source, as specified in the source section. |
| path | Path to the index file. Indexes are stored in the base sphinx directory under var/data. |
| docinfo | Document attribute values storage method. Values are extern, inline, and none. |
| mlock | Determines whether to use memory locking for cached data. |

## TABLE 9-5 (continued)

| OPTION | DESCRIPTION |
|---|---|
| morphology | Type of built-in preprocessors such as `stem_en`, `stem_ru`, `soundex`, `libstemmer_german`, and so on. The default is none. |
| min_word_len | Minimum length of words to index. For instance, MySQL’s FULLTEXT min word length is 3, but Sphinx allows 1 (default, index everything). |
| min_stemming_len | The minimum word length at which to enable stemming. Default is 1, meaning stem everything. |
| stopwords | Stop words files list. |
| wordforms | `wordforms` file, in "mapfrom > mapto" plain text format. |
| exceptions | Plain text, case-sensitive, space-insensitive, case-sensitive in mapfrom part one "AT&T => TATT" entry per line. Being able to use several tokens is a nice side effect. |
| charset_type | The `charset` encoding type. |
| ignore_chars | The ignored characters list. |
| min_prefix_len | Minimum length of prefix length to index. The default for this option is 0. |
| min_infix_len | Minimum word infix length to index. The default is 0. |
| overshort_step | This is the position on overshoot (words less than `min_word_len`). Allowed values are 0 and 1 with the default being 1. |
| stopword_step | The position increment on stop word. Values are 1 and 0 with the default being 1. |
| prefix_fields | The fields to prefix. |
| infix_fields | The fields to infix. |
| index_exact_words | Determines whether to index original keywords along with stemmed versions. This enables the use of the `=exactform` operator to work. |
| enable_star | This enables star syntax when you search prefix/infix indexes. |
| ngram_len | The n-gram length to index. |
| ngram_chars | The n-gram characters list for CJK indexing. The default is empty. |
| phrase_boundary | The phrase boundary characters list. The default is empty. |
| phrase_boundary_step | The phrase boundary word position increment. |

| OPTION | DESCRIPTION |
|---|---|
| html_strip | Determines whether HTML is stripped out from documents being indexed. The default is 0 (don't strip). |
| html_remove_elements | Determines what HTML elements to remove. |
| preopen | Determines whether pre-open index files open upon restarting searchd. |
| ondisk_dict | Determines whether to keep dictionary (.spi) on disk, or cache it in RAM. This is optional with the default being 0 (RAM only). |
| inplace_enable | Determines whether in-place inversion is enabled (uses 2x less disk, but at a cost of 5–10% indexing speed). This is optional with the default being 0 (use separate temporary files), indexer-only. |

## Defining the film_main and Its Inherited Indexes

To define the indexes, follow these steps:

1. If you're figuring the `sphinx.conf` for several indexes, you define the first index `film_text`, which is an index of the `film_text` table. Because `film_text` has a default character set of UTF-8, you should set the value for `charset_type` to `utf-8`:

```
index film_main
{
    source      = sakila_main
    path        = /usr/local/sphinx/var/data/film_main
    charset_type = utf-8
}
```

2. Also, a stemmed index is shown. This index inherits from `film_main` and only overrides the `morphology` option to be an English stemmed index:

```
index film_main_stemmed : film_main
{
    path = /usr/local/sphinx/var/data/film_main_stemmed
    morphology = stem_en
}
```

3. A distributed index `film_dist` is defined, using only the local `film_main` index, but as an agent (through `searchd`). This doesn't really show you the full benefit of distributed indexes because it is only used on a single agent. However, the section “Starting Sphinx” discusses distributed indexes.

```
index film_dist
{
    type = distributed
    agent = localhost:9312:film_main
}
```

## Specifying the Indexer Options

The option for the indexer, mem_limit, is set to 32 megabytes for this installation. This is the maximum amount of memory that the indexer is allowed to use.

```
indexer
{
    mem_limit = 32M
}
```

## Specifying the searchd Options

searchd options are also defined:

- address: 127.0.0.1, localhost address will be used.
- port: searchd port 9312 (default port for searchd).
- searchd_log: The log that shows requests to the local instance of searchd.
- query_log: Shows what queries were run against indexes.
- max_children: The maximum number of search processes that can run.
- pid_file: The pid file used by searchd.
- max_matches: The maximum number of matches returned (1000).
- seamless_rotate: Set this to 1. This means searchd can be restarted without any effect on applications using searchd.

```
searchd
{
    listen          = 127.0.0.1
    port            = 9312
    log             = /usr/local/sphinx/var/log/searchd.log
    query_log       = /usr/local/sphinx/var/log/query.log
    read_timeout    = 5
    max_children    = 30
    pid_file        = /usr/local/sphinx/var/log/searchd.pid
    max_matches     = 1000
    seamless_rotate = 1
}
```

## Starting Sphinx

Now that the sphinx.conf is set up, and you have a running Sphinx system, you will need to run the indexer and start the search daemon, searchd.

## Running the Indexer

At this point, you have not yet run the indexer. When you do so, the indexer runs the queries you specified for your data sources and then builds the local indexes you specified. Because they are distributed indexes, the distributed indexes are not and cannot be built by the indexer.
