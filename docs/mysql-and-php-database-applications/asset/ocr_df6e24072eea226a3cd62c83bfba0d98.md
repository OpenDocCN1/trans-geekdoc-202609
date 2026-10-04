# Appendix E: PHP Function Reference

Table E-32 MHASH FUNCTIONS

| Function | Returns | Action |
|---|---|---|
| mhash_count() | int | Gets the number of available hashes |
| mhash_get_block_size(int hash) | int | Gets the block size of hash |
| mhash_get_hash_name(int hash) | string | Gets the name of hash |
| mhash(int hash, string data) | string | Computes hash function on data, using the hash in the first argument |

![](bbox=[0.181, 0.406, 0.243, 0.467])

Use of these functions requires the mhash library from http://mhash.sourceforge.net/.PHP must be compiled --with-mash.

The mSQL database is another open-source SQL database server. It is not actively maintained and has some limitations that make it a poor choice compared to MySQL, PostgreSQL, or Interbase. Note that msqp and MySQL have almost identical function sets.

Table E-33 MSQL FUNCTIONS

| Function | Returns | Action |
|---|---|---|
| msql_connect([string hostname[:port]], . string username [, string password]) | int | Opens a connection to an mSQL Server |
| msql_pconnect([string hostname[:port]], . string username [, string password]) | int | Opens a persistent connection to an mSQL Server |

Continued