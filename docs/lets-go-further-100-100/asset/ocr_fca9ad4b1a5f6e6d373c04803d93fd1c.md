| db/migrations/new name=$1 | create a new database migration |
| db/migrations/up | apply all up database migrations |

# Phony targets

In this chapter we’ve been using `make` to execute *actions*, but another (and arguably, the primary) purpose of `make` is to help create files on disk where *the name of a target is the name of a file* being created by the rule.

If you’re using `make` primarily to execute actions, like we are, then this can cause a problem if there is a file in your project directory *with the same path as a target name*.

If you want, you can demonstrate this problem by creating a file called `./run/api` in the root of your project directory, like so:

```
```bash
$ mkdir run && touch run/api
```
```

And then if you execute `make run/api`, instead of our API application starting up you’ll get the following message:

```
```bash
$ make run/api
make: 'run/api' is up to date.
```
```